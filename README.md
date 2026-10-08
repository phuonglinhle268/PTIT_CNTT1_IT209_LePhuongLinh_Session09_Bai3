# Bài 3: Viết Dockerfile đóng gói trang Web HTML tĩnh

## 1. Cấu hình tệp tin

### `index.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<h1>Hello Docker Session 09!</h1>
</body>
</html>
```

### `Dockerfile`
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

---

## 2. Các bước thực hiện & Kiểm tra

### Bước 1: Build Docker Image
```bash
docker build -t my-html-app:v1 .
```
**Kết quả:** Build image thành công với tên `my-html-app:v1`.

### Bước 2: Khởi chạy Container từ Image vừa build
```bash
docker run -d -p 8081:80 --name html-app my-html-app:v1
```
**Kết quả:** Container `html-app` được khởi chạy ở chế độ chạy ngầm và lắng nghe trên cổng `8081`.

### Bước 3: Kiểm tra truy cập Web
```bash
curl http://localhost:8081
```
**Kết quả:** Trả về mã HTTP 200 và hiển thị đúng nội dung thẻ `<h1>Hello Docker Session 09!</h1>`.

```text
StatusCode        : 200
StatusDescription : OK
Content           : <!DOCTYPE html>
                    <html lang="en">
                    <head>
                        <meta charset="UTF-8">
                        <title>Title</title>
                    </head>
                    <body>
                    <h1>Hello Docker Session 09!</h1>
                    </body>
                    </html>
...
```
