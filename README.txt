ESPORTPEDIA – Panduan Upload
============================

ISI FOLDER
  index.html  – halaman utama
  style.css   – tampilan
  app.js      – logika situs + panel admin
  data.json   – SEMUA data situs (tim, logo, pemain, skor, hadiah, dll)

CARA UPLOAD (pilih salah satu, semuanya gratis)
  1. Netlify : buka app.netlify.com/drop lalu seret folder ini.
  2. GitHub Pages : upload 4 file ke repository, aktifkan Pages.
  3. cPanel / hosting biasa : upload 4 file ke folder public_html.
  Catatan: jangan buka index.html langsung dari file (double-click); data.json
  hanya terbaca lewat hosting/server. Untuk tes lokal:  python3 -m http.server

SEBELUM UPLOAD
  Buka app.js, ganti ADMIN_PASSWORD di baris paling atas (saat ini: #1&$_4).

CARA MENGELOLA (ADMIN)
  1. Buka  alamat-situs/#/admin  (atau link "Login admin" di footer) dan masuk.
  2. Edit apa saja: turnamen, hadiah, jumlah tim (4 / 8 / 16), tim, logo,
     pemain, negara, pencapaian, skor bracket, riwayat.
     Di tab Turnamen / Peserta / Skor ada pemilih turnamen di atas: bisa
     tambah turnamen baru, hapus, dan pilih satu sebagai "unggulan" (tampil
     di beranda).
  3. Edit tersimpan sebagai DRAF di browser kamu. Klik "Unduh data.json".
  4. Upload file data.json itu ke hosting, timpa yang lama.
  5. Pengunjung langsung melihat data terbaru (refresh halaman).
  Pengunjung biasa hanya bisa MELIHAT. Mereka tidak punya akses mengubah
  data.json di hosting kamu.

CATATAN KEAMANAN
  Password di app.js hanya "pintu" tampilan admin. Keamanan sebenarnya ada di
  data.json: hanya orang yang bisa upload ke hosting kamu yang bisa mengubah
  apa yang dilihat pengunjung. Kalau suatu saat butuh login multi-admin dan
  edit langsung online (tanpa unduh/upload), perlu backend + database.

FITUR BARU (v4)
  - Format 16 tim: double elimination lengkap (30 pertandingan), pembagian
    hadiah per posisi sampai peringkat 13-16.
  - Banyak turnamen: halaman daftar turnamen (#/t), tiap turnamen punya
    bracket, skor, peserta, dan hadiah sendiri. Halaman tim merangkum semua
    turnamen yang diikuti.
  - data.json lama (versi 1 turnamen) otomatis dikonversi saat dibuka.

FITUR BARU (v5)
  - Mata uang dolar (USD). Isi angka hadiah di admin dengan nilai dolar.
  - Game / Divisi: admin > tab Game. Tiap tim dan turnamen dipilih game-nya.
    Tim organisasi yang sama di game berbeda dibuat sebagai tim terpisah
    dengan kolom Organisasi sama (mis. REXC); lawan & roster bebas berbeda.
    Pengunjung bisa memfilter per game di beranda, Turnamen, dan Tim.
  - Profil tim otomatis mengikuti turnamen: posisi akhir, hadiah (sesuai
    persentase), jumlah juara, total hadiah, seri, map, win rate.
  - Login peserta: admin > tab Akun. Aktifkan "Wajib login", tambah akun.
    Ini pembatas tampilan; data.json tetap bisa dibuka publik.
  - Login admin kini per-sesi (hilang saat tab/browser ditutup) + tombol
    "Keluar admin" di menu.

FITUR BARU (v6)
  - Tim Pusat: admin > tab "Tim Pusat". Buat organisasi induk (mis. REXC),
    lalu pada tab "Tim & Pemain" pilih tim pusatnya untuk tiap tim. Halaman
    tim pusat (#/org/...) menampilkan bagian "Divisi" berisi tim-tim di
    bawahnya (mis. REXC AKARI, REXC KONAN); klik untuk masuk ke halaman tim.
    Data lama yang mengisi kolom Organisasi diubah otomatis jadi tim pusat.
  - Divisi game boleh kosong: pada tim dan turnamen ada opsi "tanpa divisi".
    Kalau kosong, label game/divisi tidak ditampilkan di situs.
  - Pemilih seed turnamen kini menampilkan SEMUA tim (tidak lagi dibatasi
    game yang sama dengan turnamen).

CARA PAKAI SINGKAT (ADMIN)
  1. Klik "Admin" di menu, masuk dengan kata sandi admin.
  2. Tab "Tim Pusat" (atau "Tim & Pemain"): pakai kotak "Tambah divisi cepat".
     Pilih tim pusat (atau ketik nama baru), pilih game, isi ID pemain
     (kosong = TBD), klik "+ Buat divisi".
  3. Tab "Turnamen" > "Peserta": pilih tim/divisi yang ikut.
  4. Setelah selesai, klik "Unduh data.json" di bar atas.
  5. Upload data.json (dan app.js kalau ada versi baru) ke hosting, timpa file
     lama. TANPA langkah 4-5 perubahan hanya jadi draf di browser sendiri.
  6. Buka situs dengan refresh keras (Ctrl+Shift+R).

JUMLAH TIM BEBAS (v7)
  - Admin > Turnamen > Peserta: isi "Jumlah tim" 3 sampai 32 (mis. 10).
    Bracket upper/lower, jadwal, skor, posisi akhir, dan pembagian hadiah (%)
    dibuat otomatis. Jika jumlahnya bukan 4/8/16/32, seed teratas dapat bye
    (langsung lolos babak pertama). Ukuran 4, 8, 16 tetap memakai bracket lama.

SIMPAN OTOMATIS KE FOLDER (v8)
  - Admin > Data > "Hubungkan folder" (atau tombol di bar bawah), pilih folder
    situs yang berisi data.json. Sesudah itu setiap perubahan otomatis ditulis
    ke data.json di folder itu. Butuh Chrome/Edge desktop; situs dibuka lewat
    https atau localhost. Kalau browser ditutup, klik "Izinkan folder" sekali
    lagi saat membuka admin.

UNDUH PAKET SITUS (v9)
  - Admin > Data (atau bar bawah) > "Unduh zip": mengunduh
    esportpedia.zip berisi seluruh file situs + data.json terbaru. Ekstrak,
    lalu upload folder esportpedia ke Netlify (drag and drop).

CARA PINDAH HOSTING (bebas, tidak terkunci ke Netlify)
  - Situs ini murni file statis. Setelah mengubah data di Admin, klik "Unduh zip"
    (isinya semua file situs + data.json terbaru), ekstrak, lalu upload folder
    esportpedia ke hosting mana pun (Netlify, GitHub Pages, hosting biasa, dll).
  - Perubahan Admin tersimpan sementara di browser yang dipakai; unduh zip setelah
    selesai mengedit agar data aman.

PEMBARUAN (v10)
  - Nama profil di kotak info (di atas logo) kini tebal.
  - Filter game di beranda/Turnamen/Tim jadi dropdown "detail" vertikal (tidak menyamping).
  - Beranda menampilkan maksimal 3 turnamen; sisanya lewat tombol "Lebih banyak".
  - Pencarian cepat: ketik di kolom cari (ikon 🔍 di HP) untuk tim, tim pusat, turnamen,
    pemain, pertandingan (mis. "liquid vs akari"), game, dan halaman. Panah/Enter didukung.
