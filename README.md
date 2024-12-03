# Git - hệ thống quản lý phiên bản phân tán
- Hiểu đơn giản thì nó là thằng trung gian quản lí source code của bạn - nó theo dõi sự thay đổi của các tệp tin
- Nó quản lý repository local(trên thiết bị cá nhân) và remote repository origin(nơi lưu trữ từ xa - làm nhiều người chung 1 dự án)
- GitHub, GitLab, hoặc Bitbucket là các thằng cung cấp chức năng dịch vụ của git, có thể sử dụng UI thay cho CLI nếu bạn không nhớ
- Clone remove repository origin về local: SSH hoặc HTTPS
- Với repository publish thì không cần đăng nhập hoặc cấu hình SSH Key để xác thực
- Tại vị trí thư mục cần clone dự án về: git clone + URL giao thức HTTPS trỏ đến repository trên GitHub

# Một số lệnh
1.Kiểm tra trạng thái của các file đã thay đổi: **git status**

2.Kiểm tra xem bạn đang ở nhánh nào: **git branch**

3.Nên tạo nhánh mới -> sau khi tạo nhánh mới thì git tự động chuyển bạn sang nhánh mới:  **git checkout -b <ten-nhanh-moi>** 

4.Tạo Staging ghi lại lịch sử các thay đổi vào repository -> lựa chọn và kiểm soát các thay đổi nào sẽ được lưu trữ commit kế tiếp
- Lưu tất cả các file đã thay đổi: **git add .** 
- Lưu tệp có lựu chọn: **git add <tên-file>**

5.Tạo commit thay đổi: **git commit -m "Sửa file README.md"**
- Lấy mã commit: **git log**

6.Nếu bạn muốn đẩy nhánh mới này lên GitHub: **git push -u origin <ten-nhanh-moi>**

7.Nếu muốn xóa các commit khỏi lịch sử nhưng những thay đổi code vẫn được dữ lại **git reset --soft <ma-commit>**
-> Khi push cần sử dụng **git push --force** để đồng bộ hóa thay đổi
- Nếu muốn xóa các commit và cả những thay đổi code: **git reset --hard <ma-commit>** -> không nên dùng

8.Đẩy code lên origin: **git push origin <ten-nhanh>**

9.Lệnh dùng để đồng bộ hóa kho lưu trữ từ xa (remote repository) với kho lưu trữ cục bộ (local repository): **git pull** và **git fetch**
- **git fetch origin** kiểm tra các nhánh hoặc các commit mới đã được tải về local chưa -> không tự động áp dụng những thay đổi đó vào nhánh hiện tại của bạn
- **git pull origin** sự kết hợp của **git fetch** và **git merge** -> tải về các thay đổi từ kho lưu trữ từ xa và tự động áp dụng chúng vào nhánh hiện tại của bạn
- **git log origin/main**  -> Xem lịch sử commit của nhánh main từ origin(remote repository)

10.Nếu muốn thay đổi commit cuối cùng: **git commit --amend** hoặc nếu không muốn thay đổi thông điệp: **git commit --amend --no-edit**
-> Phải lưu thay đổi code vào Staging trước nhé -> Sau đó push code lên origin: git push origin <tên-nhánh> --force

-> Sau khi push code thành công có thể tạo merge request hoặc pull request (cách gọi khác nhau trong gitlab và github) để merge nhánh code mới bạn vừa commit và push lên origin vào nhánh code chính (nhánh code chạy tổng thể của chương trình/hệ thống)
