# FLAC to MP3

Ứng dụng chuyển đổi file đuôi mở r ộng.flac sang .mp3

## Cài đặt
```
npm install
```
## Hướng dẫn sử dụng
Bước 1:
Truyền vào đường dẫn của thư mục chứa file .flac vào flac-to-mp3/convert_runner.js:
```
let srcFolder = "đường dẫn";
```

Bước 2: Gõ lệnh trong Terminal
```
node --harmony-async-await convert_runner.js
```
## Cấu trúc:
1. Ứng dụng bắt đầu chạy từ `convert_runner.js`

    File này sẽ chạy hàm `runner()` truyền vào 2 tham số: 
    
    - `srcFolder`: đường dẫn đầu vào chứa file .flac 
    
    - `desFolder`: đường dẫn đầu ra chứa file .mp3 (mặc định cùng thư mục với ứng dụng)


2. File `convert_runner.js` sẽ khởi tạo 2 biến gọi đến 2 file:

    - `myConvert`: gọi đến class Converter trong `converter.js` làm nhiệm vụ chuyển file .flac sang .mp3 
    bằng FFmpeg
    
    - `myScanner`: gọi đến class ScanFile để quét toàn bộ file .flac trong thư mục đầu vào
    
3. Tiếp tục khởi tạo 2 biến:

    - `fileArrFlac`: mảng chứa đường dẫn của tất cả file .flac đã quét được
    
    - `fileArrMp3`: mảng chứa đường dẫn của các file .mp3 để làm thư mục đầu ra 
    (copy lại cấu trúc của thư mục gốc chứa file .flac)
        - sử dụng hàm `mp3path()` lấy mảng file .flac đã quét được, thay thế đuôi ".flac" sang ".mp3";
        lưu sang 1 mảng mới dẫn vào fileArrMp3
         
4.  Truyền tất cả tham số lấy được (fileArrMp3, fileArrFlac, myConvert) vào hàm renderFile:

    - `renderFile` dùng để kiểm soát số lượng các file được convert cùng 1 lúc, tránh trường hợp convert
    tất cả file 
    
    - `myConvert` sẽ nhận được tham số đầu vào là fileArrFlac, đầu ra `fileArrMp3`
