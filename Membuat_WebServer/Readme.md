# Proyek Membangun WebServer <br>
## 1. Membuat Server <br>
**Untuk membangun sebuah webserver yang harus dilakukan pertama kali ialah membuat server terlebih dahulu, bisa secara local maupun cloud.**<br>
**Disini saya akan menjelaskan pembuatan server cloud menggunakan AWS.**<br>
**1. Masuk ke website `aws.dicoding.com`.**<br>
![Gambar membuat server aws](screenshot/gambar1.png)<br>

**2. Ketika sudah masuk ke dashborad aws untuk pertama kali, klik `sign in` pada pilihan di kanan atas.**<br>
**3. Akan masuk ke halaman login, disini kita bisa login dengan akun yang kita punya dengan `root user`, atau sign up bila tidak punya akun.**<br>
![Gambar membuat server aws](screenshot/gambar2.png)<br>

**4.klik login, selanjutnya akan menuju ke dashboard console management.**<br>
![Gambar membuat server aws](screenshot/gambar3.png)<br>

**5. Klik atau cari EC2 di pencarian, lalu akan masuk ke halaman dashboard dari EC2**<br>
![Gambar membuat server aws](screenshot/gambar4.png)<br>

**6. pada dashboard pilih instance di sebelah kiri, lalu klik launch instance.**<br>
![Gambar membuat server aws](screenshot/gambar5.png)<br>

**7. Selanjutnya akan masuk ke menu launch instance, pada `Name and Tags` masukan nama server yang diinginkan.**<br>
![Gambar membuat server aws](screenshot/gambar6.png)<br>

**8. Selanjutnya pada `Application and OS Images(Amazon machine image)` pilih ubuntu, lalu pilih versi ubuntu yang ingin dipakai, disini saya menggunakan versi ubuntu 20.04**<br>
![Gambar membuat server aws](screenshot/gambar7.png)<br>

**9. Selanjutnya pada `Key Pair(Login)`, klik create key pair, disini saya bertujuan agar memberikan keamanan pada server agar tidak sembarang orang dapat mengakses atau mengubah isi dari server tersebut. pada key pair pilih `RSA` dan masukkan nama key pair yang di inginkan pada key pair name. lalu pada private key file format, pilih `.pem`. selanjutnya klik create key pair bila sudah selesai.**<br>
![Gambar membuat server aws](screenshot/gambar8.png)<br>

**10. Selanjutnya pada `Network Settings` pilih edit. pada VPC pilih VPC-A, pada Subnet pilih Subnet A, disini saya sudah membuat vpc dan subnet sendiri. pada auto-assign public ip pilih disable. pada firewall pilih create security group, masukkan nama security group serta description.**<br>
![Gambar membuat server aws](screenshot/gambar9.png)<br>

**11. Pada configure default, atau storage pilih micro atau ukuran 8gb, karena pada kasus ini server ini digunakan untuk penyelesaian tugas final dicoding, atau aplikasi yang sederhana. selanjutnya pilih launch instance disebalah kanan bawah**<br>
![Gambar membuat server aws](screenshot/gambar10.png)<br>

**12. Akan muncul notifikasi bahwa server success dibuat, untuk melihat detailnya bisa klik view all instances.**<br>
![Gambar membuat server aws](screenshot/gambar11.png)<br>

**13. Pada instances, akan muncul nama server yang berhasil kita buat. namun belum memiliki ip public IPv4 address.**<br>
![Gambar membuat server aws](screenshot/gambar12.png)<br>

**14. Cara mendapatkan public IPv4 Address, yaitu dengan cara pilih `Elastic IPs` pada menu di sebelah kiri, lalu pilih `Allocate Elastic IP address`, lalu pilih Allocate**<br>
![Gambar membuat server aws](screenshot/gambar13.png)<br>

**15. Akan menampilkan ip public yang telah dibuat dengan nama yang kita masukkan.**<br>
![Gambar membuat server aws](screenshot/gambar14.png)<br>

**16. Selanjutnya pilih Actions, dan pilih `Associate Elastic IP Address`**<br>
![Gambar membuat server aws](screenshot/gambar15.png)<br>

**17. Akan masuk ke halaman `Associate Elastic IP Address` pada pilihan instance, masukkan nama server yang dibuat sebelumnya, setelah itu klik associate.**<br>
![Gambar membuat server aws](screenshot/gambar16.png)<br>

**18. Selanjutnya pilih instance, lalu refresh server tersebut, akan muncul ip public yang telah kita koneksikan sebelumnya. **<br>
![Gambar membuat server aws](screenshot/gambar17.png)<br>

**19. Buka terminal, ubah hak akses untuk key pair yang di buat sebelumnya dengan `chmod 400` lalu nama key.**<br>
![Gambar membuat server aws](screenshot/gambar18.png)<br>

**20. Ketikkan perintah `ssh -i namakeypair username@ip-public` untuk masuk ke server aws.**<br>
![Gambar membuat server aws](screenshot/gambar19.png)<br>

**21. Selanjutnya jalankan update dan upgrade sistem.**<br>
![Gambar membuat server aws](screenshot/gambar20.png)<br>

**22. Selanjutnya pada instance server yang kita buat, kita ubah security groups, masuk ke security lalu klik nama security group, masuk ke inbound rules, pilih edit inbound rules, lalu add rule dan tambahkan http dan https agar bisa mengakses port http dan https. selanjutnya pada source pilih anywhere ipv4. klik save rules bila sudah selesai konfigurasi security group.**<br>
![Gambar membuat server aws](screenshot/gambar24.png)<br>

**23. Masuk ke akun github `https://github.com/dicodingacademy/a387-jarkom-labs` untuk melakukan proses clone ataupun fork. disini saya akan memilih proses clone secara local. piluh code lalu copy link tersebut.**
![Gambar membuat server aws](screenshot/gambar25.png)<br>

**24. Masuk ke terminal server aws, lalu jalankan proses clone dengan perintah `git clone https://github.com/dicodingacademy/a387-jarkom-labs`.**<br>
![Gambar membuat server aws](screenshot/gambar26.png)<br><br>

## Menginstall Docker Engine <br>
**1. Update system dan setup repository.**<br>
![Gambar setup docker](screenshot/gambar21-docker.png)<br>

**2. Add Docker’s official GPG key**<br>
![Gambar setup docker](screenshot/gambar22-docker.png)<br>

**3. Setup repository dan install docker engine.**<br>
![Gambar setup docker](screenshot/gambar23-docker.png)<br>

**4. Pull docker images untuk nginx.**<br>
![Gambar setup docker](screenshot/gambar27-docker.png)<br>

**5. Membuat container untuk images nginx. serta mengubah port akses nginx yang sebelumnya port 80, agar bisa terekspos diluar, saya menggantinya dengan port 3000**<br>
![Gambar setup docker](screenshot/gambar28-docker.png)<br>

**6. Cek apakah webserver sudah bisa berjalan, dengan perintah docker ps.**<br>
![Gambar setup docker](screenshot/gambar29-docker.png)<br>

**7. Masuk ke website dan masukkan ip public kita untuk mengakses web server nginx dan juga port 3000**<br>
![Gambar setup docker](screenshot/gambar30.png)<br>

**8. Alternatif lain selain menggunakan web server nginx, yaitu dengan menggunakan Apache. kita bisa mendownload atau menginstall image dari apache, dengan menjalankan perintah docker pull httpd.**<br>
![Gambar setup docker](screenshot/gambar31-docker.png)<br>

**9. Setelah berhasil mengepull image Apache, langkah selanjutya ialah, membuat container dengan image tersebut.**<br>
![Gambar setup docker](screenshot/gambar32-docker.png)<br>

**10. Kita bisa melihat apakah container yang sudah kita buat berhasil berjalan, dengan menjalankan perintah docker ps. bisa terlihat bahwa webserver nginx dan webserver apache berjalan di port yang berbeda.**<br>
![Gambar setup docker](screenshot/gambar33-docker.png)<br>

**11. Kita bisa masuk ke website dan arahkan ip public dan port, untuk mengetahui apakah web server apache sudah berhasil di jalankan.**<br>
![Gambar setup docker](screenshot/gambar34.png)<br><br>

## Mengkonfigurasi Nginx sebagai reverse proxy <br>
**Setelah kita berhasil sebelumnya menjalankan webserver nginx dan apache menggunakan docker. langkah selanjutnya ialah menggunakan nginx sebagai reverse proxy.**<br>

**1. Buka terminal dan masuk ke dalam server aws.**<br>
**2. Masuk ke dalam direktori dengan perintah cd. selanjutnya kita install nvm terlebih dahulu dengan menjalankan perintah `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash`.**<br>
![Gambar setup nginx sebagai reverse proxy](screenshot/gambar35.png)<br>

**3. Selanjutnya ialah mengintall nvm.**<br>
![Gambar setup nginx sebagai reverse proxy](screenshot/gambar36.png)<br>

**4. Langkah selanjutnya setelah menginstall nvm ialah, menjalankan npm install untuk menginstall semua package yang dijalankan.**<br>
![Gambar setup nginx sebagai reverse proxy](screenshot/gambar37.png)<br>

**5. Kita ubah dulu file yang ada di app.js, lalu kita ubah hello world menjadi nama kita, dengan menjalankan `nano <nama file>`**<br>
![Gambar setup nginx sebagai reverse proxy](screenshot/gambar38.png)<br>

**6. Selanjutnya kita bisa menjalankan `npm run start` untuk menjalankan aplikasi tersebut, dan masuk ke website dan arahkan ke public ip**<br>
![Gambar setup nginx sebagai reverse proxy](screenshot/gambar39.png)<br>

**7. Selanjutnya ialah bagaimana cara kita menjalankan aplikasi secara global menggunakan `pm2`, cara ini dilakukan agar kita bisa menjalankan tanpa harus masuk dan menjalankan `npm run start`. pertama kita install `npm install pm2 -g`, lalu buat file `ecosystem.config.js`. setelah berhasil dibuat, langkah selanjutnya ialah jalankan aplikasi tersebut dengan perintah `pm2 start ecosystem.config.js`**<br>
![Gambar setup nginx sebagai reverse proxy](screenshot/gambar40.png)<br>

**8. Langkah selanjutnya ialah konfigurasi web server nginx untuk reverse proxy dan menerapkan limit access. jalankan perintah `nano /etc/nginx/sites-available/default` untuk konfigurasi web server. lalu simpan file tersebut.**<br>
![Gambar setup nginx sebagai reverse proxy](screenshot/gambar41.png)<br>

**9. Langkah selanjutnya ialah merestart nginx kita dengan cara, jalankan perintah `sudo systemctl restart nginx` dan masuk ke website, arahkan ip public server untuk mengetahui apakah aplikasi menggunakan reverse proxy dapat berjalan.**<br>
![Gambar setup nginx sebagai reverse proxy](screenshot/gambar42.png)<br>

**10. Selanjuntya menerapkan access limit, jalankan perintah `sudo nano /etc/nginx/sites-available/default` untuk masuk ke reverse proxy nginx. lalu masukkan `limit_req_zone $binary_remote_addr zone=one:10m rate=6r/m` serta tambahkan `limit_req zone=one;` pada kolom location.**<br>
![Gambar setup nginx sebagai reverse proxy](screenshot/gambar43.png)<br>

![Gambar setup nginx sebagai reverse proxy](screenshot/gambar44.png)<br>

**11. Selanjutnya restart nginx, dengan perintah `sudo systemctl restart nginx`. selanjutnya akses ke website dengan ip, disini saya mencoba untuk me-refresh aplikasi dengan 6x refresh dan setelah lebih dari permintaan request akan terjadi error.**<br>
![Gambar setup nginx sebagai reverse proxy](screenshot/gambar45.png)<br><br>

## Membuat Domain Name System(DNS) di AWS <br>
**Sebelumnya kita telah melakukan reverse proxy pada webserver nginx dan menerapkan access limit, selanjutnya kita akan membuat domain name system(dns) pada aplikasi yang telah kita buat.**<br>
**1. Buka terminal dan jalankan perintah `curl -X POST -H "Content-type: application/json" -d "{ \"ip\": \"<public IP EC2 instance>\" }" "https://sub.dcdg.xyz/dns/records"` untuk mendapatkan subdomain**<br>
![Gambar dns server](screenshot/gambar46.png)<br>

**2. Masuk ke server aws, lalu jalankan perintah `sudo nano /etc/nginx/sites-available/default` untuk konfigurasi dns. lalu tulis dua hostname yang diberikan sebelumnya, masukkan ke server name.**<br>
![Gambar dns server](screenshot/gambar47.png)<br>

**3. Selanjutnya kita bisa merestart system nginx `sudo systemctl restart nginx`, dan masuk ke website, lalu akses dns yang telah di konfigurasi sebelumnya.**<br>
![Gambar dns server](screenshot/gambar48.png)<br><br>

## Implementasi HTTPS pada Server AWS <br>
**Setelah kita melakukan konfigurasi dan menambahkan domain name system, selanjutnya ialah implementasi https pada server aws yang telah kita miliki.**<br>

**1. Masuk ke terminal dan akses server aws.**<br>
**2. Jalankan update system dan install certbot dengan perintah `sudo apt-get install python3-certbot-nginx -y`**<br>
![Gambar https server](screenshot/gambar49.png)<br>

**3. Setelah proses instalasi selesai, selanjutnya buat TLS certificate dengan menjalankan perintah `sudo certbot --nginx -d <yourdomain.com> -d <www.yourdomain.com>`**<br>
![Gambar https server](screenshot/gambar50.png)<br>

**4. Setelah konfigurasi selesai, buka website dan arahkan ke domain yang telah dibuat. disini saya berhasil menerapkan https sebagai protokol.**<br>
![Gambar https server](screenshot/gambar51.png)<br>
