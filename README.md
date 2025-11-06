# BAI_3_LAP_TRINH_WEB_LINUX
Yêu cầu     : LẬP TRÌNH ỨNG DỤNG WEB trên nền linux
1. Cài đặt môi trường linux: SV chọn 1 trong các phương án
 - enable wsl: cài đặt docker desktop
 - enable wsl: cài đặt ubuntu
 - sử dụng Hyper-V: cài đặt ubuntu
 - sử dụng VMware : cài đặt ubuntu
 - sử dụng Virtual Box: cài đặt ubuntu
2. Cài đặt Docker (nếu dùng docker desktop trên windows thì nó có ngay)
3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: 
   mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443)
4. Lập trình web frontend+backend:
 SV chọn 1 trong các web sau:
 4.1 Web thương mại điện tử
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - Có tính năng liệt kê các sản phẩm bán chạy ra trang chủ
 - Có tính năng liệt kê các nhóm sản phẩm
 - Có tính năng liệt kê sản phẩm theo nhóm
 - Có tính năng tìm kiếm sản phẩm
 - Có tính năng chọn sản phẩm (đưa sản phẩm vào giỏ hàng, thay đổi số lượng sản phẩm trong giỏ, cập nhật tổng tiền)
 - Có tính năng đặt hàng, nhập thông tin giao hàng => được 1 đơn hàng.
 - Có tính năng dành cho admin: Thống kê xem có bao nhiêu đơn hàng, call để xác nhận và cập nhật thông tin đơn hàng. chuyển cho bộ phận đóng gói, gửi bưu điện, cập nhật mã COD, tình trạng giao hàng, huỷ hàng,...
 - Có tính năng dành cho admin: biểu đồ thống kê số lượng mặt hàng bán được trong từng ngày. (sử dụng grafana)
 - backend: sử dụng nodered xử lý request gửi lên từ javascript, phản hồi về json.
 4.2 Web IOT: Giám sát dữ liệu IOT.
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - hiển thị giá trị mới nhất của các thông số đang giám sát, khi click vào thì hiển thị đồ thị lịch sử quá trình thay đổi (gọi grafana iframe để hiển thị)
 - backend: Sử dụng nodered để đọc dữ liệu từ các cảm biến (có thể dùng api online để lấy dữ liệu theo giời gian thực), 
   nodered sẽ lưu dữ liệu mới nhất (dạng update) vào cơ sở dữ liệu mariadb (sử dụng phpmyadmin để tạp table và quản trị lần đầu)
   nodered sẽ lưu dữ liệu (insert) vào influxdb để lưu giá trị lịch sử, để cho grafana dùng để hiển thị biểu đồ.
5. Nginx làm web-server
 - Cấu hình nginx để chạy được website qua url http://fullname.com  (thay fullname bằng chuỗi ko dấu viết liền tên của bạn)
 - Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80, (dù nodered đang chạy ở port 1880)
 - Cấu hình nginx để http://fullname.com/grafana truy cập vào grafana qua cổng 80, (dù grafana đang chạy ở port 3000)

# +  1. Cài đặt môi trường linux.
 # + Cài đặt ubuntu và docker desktop.</p>
      <img width="1054" height="594" alt="image" src="https://github.com/user-attachments/assets/08c551bf-58b2-4f87-9aa6-0b9bed87516f" /></p>
<img width="1128" height="651" alt="image" src="https://github.com/user-attachments/assets/1e33adcb-fada-4209-9fd4-c2b7415fb1c7" /></p>
<img width="890" height="689" alt="image" src="https://github.com/user-attachments/assets/d1ac0ea9-6803-4ebf-a940-1c54d04f8f7e" /></p>
# + 3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container</p>
<img width="1335" height="761" alt="image" src="https://github.com/user-attachments/assets/2d15410b-8c3f-4e08-b807-4571fe45a584" />

 # + Cài đặt các container </p>
<img width="1616" height="482" alt="image" src="https://github.com/user-attachments/assets/da7260ba-804b-4633-877e-4769f2e09ec9" />

# + 4. Lập trình web frontend+backend ( Web IOT: Giám sát dữ liệu IOT.)</p>
# + Tạo bảng database</p>
<img width="1516" height="847" alt="image" src="https://github.com/user-attachments/assets/01c03fe6-9501-493c-b62f-cece298ffead" />

# + Bảng lưu tài khoản đăng nhập </p>
<img width="1065" height="295" alt="image" src="https://github.com/user-attachments/assets/55383376-f85c-4e01-835d-364fa5d1ddcf" /></p>

# + bảng cập nhập dữ liệu nhiệt độ độ ẩm</p>
<img width="1013" height="660" alt="image" src="https://github.com/user-attachments/assets/ea673116-9f41-4707-8c8b-62adf8737c0c" /> <p/p>

# + khởi động nodered và cài packages Tạo settings.js để expose libs cho function nodes</p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b2568dc9-f882-40cb-b6fe-9b348f333346" /> </p>

# + tạo liên kết nodered </p>
<img width="1424" height="658" alt="image" src="https://github.com/user-attachments/assets/46d6a33b-8b84-436e-b7f0-b6c8b2609a49" />

# + Cấu hình các node để trỏ api </p>
# + SQL </p>
<img width="1074" height="598" alt="image" src="https://github.com/user-attachments/assets/41777e40-dc68-499c-995b-187881ab20b6" />

# + Tạo web để trỏ api lấy database của nodered </p>
# + Tạo file html gồm Js </p>
<img width="1715" height="760" alt="image" src="https://github.com/user-attachments/assets/362e457f-818d-4d03-aea2-cc75567271a4" />

# + Tạo file nignx.conf để tạo khối yêu cầu </p>
<img width="1576" height="686" alt="image" src="https://github.com/user-attachments/assets/a4a239c8-5b85-4c42-96f7-06d52851d2a8" />

# + kết quả của website </p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b2f41183-909a-4ae4-a5fc-d07e4552c161" />

# + cấu hình gafana </p>
# + đăng nhập và cấu hình các liên kết </p>
<img width="1564" height="332" alt="image" src="https://github.com/user-attachments/assets/95d9b594-3b6c-4bc5-936a-6815439ef592" />
<img width="1884" height="895" alt="image" src="https://github.com/user-attachments/assets/fc382f0a-96c1-42f0-a1e8-4a2b9a267da3" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cb37e387-37dd-48d0-9b2f-5309ab10282a" />

# + Kết quả hiển thị biểu đồ đo nhiệt độ </p>
<img width="547" height="162" alt="image" src="https://github.com/user-attachments/assets/68561c16-cc80-41e5-a7a8-07f2bd28cfdb" />

# + Đổi tên miền vuductu </p>
<img width="1458" height="786" alt="image" src="https://github.com/user-attachments/assets/1e035253-704f-4ae3-96c6-811d97f864d0" />
<img width="1898" height="995" alt="image" src="https://github.com/user-attachments/assets/210bf159-7b67-4ca2-8733-bd580b1c1f52" />

# EM CẢM ƠN THẦY ĐÃ XEM BÀI CỦA EM 


