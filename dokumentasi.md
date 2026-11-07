# Dokumentasi Workshop Day 1

**Tema:** From AI to GitHub: Building with AI, Managing Change with GitHub
**Pemateri:** Nugi Farhan (Senior Product Designer)
**Peserta:** Sjambas Alfaridzi Machmud

---

## 1. Rangkuman Materi

Workshop terbagi menjadi dua topik besar:
1. **Membuat dan mengembangkan** sesuatu dengan bantuan AI (prompt engineering).
2. **Manajemen perubahan dan kolaborasi** menggunakan Git dan GitHub.

### 1.1 Capaian Pembelajaran
- Menjelaskan bagaimana prompt AI yang lebih spesifik menghasilkan hasil yang lebih baik.
- Membedakan Git dan GitHub.
- Mengidentifikasi repository, commit, branch, dan pull request.
- Melakukan version controlling.

### 1.2 Prompt Engineering
**Prompt** adalah instruksi atau masukan yang diberikan kepada model AI untuk mendapatkan hasil tertentu. Bentuknya bisa berupa pertanyaan sederhana, kata kunci, instruksi yang rumit, atau potongan kode.

**Prompt engineering** adalah cara merancang instruksi agar AI memberikan jawaban yang tepat, relevan, dan layak digunakan.

**Context is key.** Prompt tanpa konteks (misalnya hanya "Create student task planner") menghasilkan jawaban yang umum. Prompt dengan konteks yang jelas menghasilkan hasil yang jauh lebih sesuai kebutuhan.

**Struktur prompt yang baik:**

| Komponen | Fungsi |
|----------|--------|
| Role | Peran atau situasi yang diberikan kepada AI |
| Task | Tujuan atau tugas yang harus dikerjakan |
| Context | Kebutuhan (requirements) dan batasan (constraints) |
| Format | Bentuk output yang diinginkan |

**Taktik prompt yang efektif** (sumber: Google Cloud):
- Gunakan kata kerja aksi untuk menentukan tindakan yang diinginkan.
- Tentukan panjang dan format output.
- Tentukan target audiens.
- Sertakan fakta dan data yang relevan.
- Rujuk sumber atau dokumen tertentu.
- Definisikan istilah dan konsep kunci.

**Keuntungan prompt engineering:**
- Meningkatkan performa model AI.
- Mengurangi bias dan respons yang offensive.
- Meningkatkan kontrol dan prediktabilitas.
- Memberikan pengalaman yang lebih baik.

### 1.3 Git
Git adalah *version control system* yang melacak siapa, kapan, dan apa saja yang diubah dalam suatu file. Git diciptakan oleh Linus Torvalds pada tahun 2005.

**Alur kerja Git (Git workflow)** terdiri dari tiga area:
- **Working directory**: salinan satu versi proyek yang sedang dikerjakan di komputer.
- **Staging area (index)**: tempat menyimpan informasi perubahan yang akan masuk ke commit berikutnya.
- **Git directory (repository)**: tempat Git menyimpan metadata dan object database proyek. Bagian inilah yang disalin saat melakukan clone.

Alurnya: **Working directory → (stage) → Staging area → (commit) → Repository**.

### 1.4 Git vs GitHub

| | Git | GitHub |
|---|-----|--------|
| Jenis | Sistem version control terdistribusi (DVCS) | Platform berbasis web |
| Fungsi | Melacak dan mengelola perubahan kode secara lokal | Menyimpan repository Git secara online dan mendukung kolaborasi |

### 1.5 Perintah Git Dasar

```bash
git init                      # memulai repository baru
git add .                     # memindahkan file ke staging area
git commit -m "message"       # menyimpan perubahan ke repository
```

**Menghubungkan ke GitHub:**

```bash
git remote add origin <url>   # menghubungkan repo lokal dengan repo di GitHub
git push origin main          # mengirim branch saat ini ke remote
git pull origin main          # mengambil perubahan lalu menggabungkannya ke branch saat ini
```

**Variasi perintah `git add`:**
- `git add --all` / `git add -A`: menambahkan semua perubahan di repository ke staging area.
- `git add .`: menambahkan semua file di direktori saat ini beserta isinya.
- `git add *`: menambahkan file yang dimodifikasi atau baru, tetapi tidak file yang dihapus.

**Menambahkan repository ke Git** bisa dengan dua cara:
1. `git init` untuk membuat repository baru di lokal, atau
2. Membuat repository di GitHub, salin link dari tombol **Code**, lalu jalankan `git clone "url"`.

### 1.6 Setup Git dan VS Code
1. Install Git, pilih versi sesuai perangkat.
2. Cek instalasi dengan `git --version`.
3. Atur identitas Git:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your-email@example.com"
   ```
4. Cek konfigurasi dengan `git config --global --list`.
5. Install VS Code, lalu aktifkan perintah `code` lewat *Shell Command: Install 'code' command in PATH* dan cek dengan `code --version`.

### 1.7 SSH Key untuk GitHub
1. Buat key baru: `ssh-keygen -t ed25519 -C "email@domain.com"`.
2. Tekan Enter untuk lokasi file default, lalu isi passphrase (atau Enter dua kali tanpa passphrase).
3. Jalankan SSH agent dan tambahkan key ke agent (di macOS bisa disimpan di Keychain).
4. Salin public key (`~/.ssh/id_ed25519.pub`) lalu tambahkan di GitHub lewat *Settings → SSH and GPG keys → New SSH key*.
5. Verifikasi koneksi dengan `ssh -T git@github.com`. Jika berhasil muncul pesan *"Hi username! You've successfully authenticated, but GitHub does not provide shell access."*

Ed25519 adalah skema tanda tangan digital kurva eliptik (EdDSA dengan Curve25519) yang aman, cepat, dan tahan terhadap serangan implementasi kriptografi umum.

### 1.8 Praktik: Student Task Planner
Proyek praktik hari ini adalah membuat aplikasi web sederhana **Student Task Planner**. Alurnya:
1. Install platform AI pendukung (Claude, Antigravity, ChatGPT).
2. Tulis prompt untuk membuat web/aplikasi.
3. Tambahkan ke Git dengan `git init`.
4. Commit dan push ke GitHub.
5. Lakukan perubahan.
6. Commit dan push lagi ke GitHub.

---

## 2. Poin Penting dan Pengetahuan Baru

- Kualitas hasil AI sangat bergantung pada kualitas prompt. Prompt dengan **Role, Task, Context, dan Format** yang jelas menghasilkan output yang lebih tepat.
- **Git dan GitHub itu berbeda.** Git adalah alat version control yang berjalan di lokal, sedangkan GitHub adalah platform online untuk menyimpan repository dan berkolaborasi.
- Perubahan di Git melewati tiga tahap: **working directory, staging area, lalu repository** (lewat `add` dan `commit`).
- Perintah dasar yang wajib dikuasai: `git init`, `git add`, `git commit`, `git remote add`, `git push`, `git pull`, dan `git clone`.
- Identitas Git (`user.name` dan `user.email`) harus diatur sebelum commit pertama.
- Koneksi ke GitHub bisa diamankan dengan **SSH key**, sehingga tidak perlu memasukkan kredensial setiap kali push.
- Di akhir prompt, instruksi seperti "jangan klaim aplikasi berfungsi sebelum diverifikasi" membantu mengurangi jawaban AI yang terlalu percaya diri.

---

## 3. Pendapat Pribadi tentang Day 1 Proyek Workshop

> *Draf, silakan sesuaikan dengan pengalaman dan kesanmu sendiri.*

Menurut saya, Day 1 Proyek Workshop sangat bermanfaat sebagai pengantar bagi mahasiswa baru di bidang teknologi informasi. Materi Day 1 Proyek Workshop menggabungkan dua hal yang saling berkaitan: menggunakan AI untuk membangun sesuatu, lalu menggunakan Git dan GitHub untuk mengelola hasilnya. Dari Day 1 Proyek Workshop saya jadi paham bahwa AI akan jauh lebih berguna bila diberi prompt yang jelas dan terstruktur, dan bahwa hasil kerja perlu dicatat dengan version control agar perubahannya rapih dan bisa dilacak.

Bagian setup, yaitu instalasi Git, konfigurasi identitas, dan pembuatan SSH key, cukup menantang bagi pemula, tetapi penting karena menjadi fondasi bagi pekerjaan selanjutnya. Praktik membuat Student Task Planner membuat materi terasa nyata, karena kami langsung mencoba alur dari menulis prompt sampai push ke GitHub. Ke depan, saya ingin lebih banyak latihan soal branch dan pull request supaya siap berkolaborasi dalam tim.
