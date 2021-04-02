# Config Remote-SSH on VSCode

- **Thực hiện:** Thi Minh Nhựt - **Email:** <thiminhnhut@gmail.com>

- **Thời gian:** Ngày 02 tháng 04 năm 2020

## Nguồn tham khảo

1. [Password-less SSH into Raspberry Pi with openSSH](https://electrobotify.wordpress.com/2019/08/14/passwordless-ssh-into-raspberry-pi-with-openssh/)

## Các bước thực hiện

1. Tạo directory `.ssh` trên máy tính mà bạn muốn SSH vào:

   - Gõ lệnh trên máy tính muốn SSH vào:

     ```bash
     mkdir ~/.ssh
     ```

1. Tạo SSH Key trên máy tính của bạn:

   - Gõ lệnh trên máy tính của bạn:

     ```bash
     ssh-keygen -t ed25519
     ```

   nếu `ed25519` đã tồn tại thì có thể tạo mới (`overwrite`) hoặc bỏ qua.

1. Thêm public SSH Key (máy tính của bạn) vào máy tính mà bạn muốn truy cập vào:

   - Gõ lệnh trên máy tính của bạn:

     ```bash
     scp C:\Users\YOUR_USERNAME\.ssh\id_ed25519.pub username@ip:~\.ssh\authorized_keys
     ```

   thay đổi: `C:\Users\YOUR_USERNAME\.ssh\id_ed25519.pub` thành đường dẫn chứa file `id_ed25519.pub`),`username` `ip` của máy tính bạn muốn SSH vào.

1. Config Remote-SSH trên VSCode:

   ```text
   Host ssh_ip
      HostName ssh_ip
      User ssh_username
      Port 22
      IdentityFile ~/.ssh/id_ed25519
   ```

   thay đổi: `ssh_ip`, `ssh_username`, đường dẫn `~/.ssh/id_ed25519`.
