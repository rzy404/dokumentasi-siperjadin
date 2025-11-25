# 📱 SISTEM INFORMASI PERJALANAN DINAS (SiPerjadin) - DPRD

---

## 🏛️ STRUKTUR ORGANISASI

### Organisasi Perangkat Daerah (OPD)
1. **KOMISI-I** - Komisi Satu
2. **KOMISI-II** - Komisi Dua
3. **KOMISI-III** - Komisi Tiga
4. **KOMISI-IV** - Komisi Empat
5. **KOMISI-V** - Komisi Lima
6. **BK** - Badan Kehormatan
7. **BANGGAR** - Badan Anggaran
8. **BAPEMPERDA** - Badan Pembentukan Peraturan Daerah

---

## 👥 DAFTAR ROLE & FUNGSI

### 1. 👨‍💼 OPERATOR/ADMIN (Ketua Organisasi)
**Fungsi:**
- Membuat permohonan surat perjalanan dinas
- Pilih anggota yang akan ditugaskan
- Estimasi biaya perjalanan
- Revisi permohonan jika diminta Sekwan

---

### 2. 👔 PIMPINAN (Ketua DPRD)
**Fungsi:**
- Approve/reject permohonan (Level 1)
- QR Code approval otomatis ter-generate
- Monitoring seluruh perjalanan dinas DPRD

---

### 3. 📋 SEKWAN (Sekretaris Dewan)
**Fungsi:**
- Verifikasi anggaran (Level 2)
- **PENTING:** Bisa kurangi jumlah pegawai jika anggaran tidak cukup
- Atau minta operator revisi permohonan
- QR Code approval otomatis ter-generate

**Contoh Kasus:**
```
Permohonan: 3 pegawai, estimasi Rp 15.000.000
Sisa anggaran: Rp 10.000.000

Pilihan Sekwan:
1. REJECT: Minta operator kurangi jadi 2 pegawai
2. ADJUST: Sekwan sendiri kurangi jadi 2 pegawai
3. KONSULTASI: Diskusi dengan operator dulu
```

---

### 4. 👨‍💼 KASUBAG (Kepala Sub Bagian)
**Fungsi:**
- Approval administrasi (Level 3)
- QR Code approval otomatis ter-generate
- Koordinasi dengan Pengelola

---

### 5. 📝 PENGELOLA
**Fungsi:**
- Generate dokumen (ST, SPPD) dengan QR Code
- Printout berkas (optional, untuk arsip)
- Monitoring kelengkapan dokumen pegawai
- Arsip dokumen

**TIDAK LAGI:**
- ❌ Input rincian biaya (pegawai yang upload kwitansi fisik)
- ❌ Buat kwitansi pencairan (tidak ada sistem pencairan)

---

### 6. 👨‍💻 PEGAWAI
**Fungsi:**
- Download ST & SPPD (PDF dengan QR Code)
- Melaksanakan perjalanan dinas
- **Upload foto kegiatan** (min 3)
- **Upload kwitansi fisik** sebagai bukti pengeluaran:
  - Foto/scan tiket pesawat + boarding pass
  - Foto/scan invoice hotel
  - Foto/scan kwitansi makan
  - Foto/scan kwitansi transport
  - Bukti pengeluaran lainnya

**TIDAK ADA:**
- ❌ Input rincian biaya manual (cukup upload kwitansi fisik)
- ❌ Buat kwitansi pencairan (tidak ada sistem pencairan)

---

## 🔄 ALUR KERJA SISTEM

### 1️⃣ TAHAP PERMOHONAN

```
┌─────────────────────────────────────────────────────────┐
│ OPERATOR/ADMIN (Ketua Organisasi)                       │
│                                                          │
│ 1. Buat Permohonan:                                     │
│    • Perihal & tujuan perjalanan                        │
│    • Tanggal keberangkatan & kepulangan                 │
│    • Tempat tujuan                                      │
│    • Pilih anggota yang ditugaskan (misal: 3 orang)    │
│      - Tentukan ketua rombongan                         │
│      - Tentukan anggota rombongan                       │
│                                                          │
│ 2. Estimasi Biaya:                                      │
│    • Transport (pesawat/kereta/bus)                     │
│    • Akomodasi (hotel)                                  │
│    • Uang harian                                        │
│    • Lain-lain                                          │
│    • TOTAL ESTIMASI: Rp 15.000.000                     │
│                                                          │
│ 3. Submit Permohonan                                    │
│    → Nomor surat auto-generate: 001/KMS-I/06/14/2025  │
└─────────────────────────────────────────────────────────┘
                          ↓
                   📱 NOTIFIKASI
         (WhatsApp ke Pimpinan & Sekwan)
```

---

### 2️⃣ TAHAP APPROVAL MULTI-LEVEL (dengan QR Code)

```
┌─────────────────────────────────────────────────────────┐
│ LEVEL 1: PIMPINAN (Ketua DPRD)                         │
│                                                          │
│ • Review permohonan                                      │
│ • Cek kelayakan perjalanan dinas                        │
│                                                          │
│ APPROVE:                                                 │
│ ✅ Sistem auto-generate QR Code Approval                │
│    QR Code berisi:                                       │
│    - Nama & NIP Pimpinan                                │
│    - Nomor surat permohonan                             │
│    - Status: APPROVED                                    │
│    - Timestamp approval                                  │
│    - Hash untuk validasi                                 │
│    - Link verifikasi                                     │
│                                                          │
│ REJECT:                                                  │
│ ❌ Input alasan → Kembali ke Operator                   │
└─────────────────────────────────────────────────────────┘
                          ↓
                   📱 NOTIFIKASI
                (WhatsApp ke Sekwan)
                          ↓
┌─────────────────────────────────────────────────────────┐
│ LEVEL 2: SEKWAN (Sekretaris Dewan) - CRITICAL!         │
│                                                          │
│ • Review permohonan                                      │
│ • CEK ANGGARAN:                                         │
│   - Estimasi biaya: Rp 15.000.000                      │
│   - Sisa anggaran Komisi I: Rp 10.000.000 ❌           │
│   - TIDAK CUKUP!                                        │
│                                                          │
│ PILIHAN SEKWAN:                                         │
│                                                          │
│ 🔹 OPSI 1: REJECT & MINTA REVISI                       │
│    ❌ Reject permohonan                                 │
│    📝 Catatan: "Anggaran tidak cukup untuk 3 orang.    │
│                 Mohon revisi jadi 2 orang"              │
│    → Kembali ke Operator untuk revisi                   │
│                                                          │
│ 🔹 OPSI 2: ADJUST JUMLAH PEGAWAI (RECOMMENDED)         │
│    ✏️ Sekwan kurangi anggota dari 3 → 2 orang          │
│    📋 Pilih pegawai yang tetap berangkat:              │
│       ☑️ Dr. Budi Santoso (Ketua) - TETAP              │
│       ☑️ Siti Nurhaliza (Anggota) - TETAP              │
│       ☐ Andi Wijaya (Anggota) - DIBATALKAN             │
│    💰 Estimasi biaya disesuaikan: Rp 10.000.000        │
│    📱 Notifikasi ke Andi: "Penugasan dibatalkan"       │
│    ✅ APPROVE dengan penyesuaian                        │
│    → Generate QR Code Approval                          │
│    → Pencadangan anggaran otomatis                      │
│                                                          │
│ 🔹 OPSI 3: KONSULTASI                                   │
│    💬 Diskusi dengan Operator via chat/telpon           │
│    🤝 Sepakat solusi terbaik                            │
│    → Lanjut ke Opsi 1 atau 2                           │
└─────────────────────────────────────────────────────────┘
                          ↓
                   📱 NOTIFIKASI
        (WhatsApp ke Kasubag & Pegawai yang dibatalkan)
                          ↓
┌─────────────────────────────────────────────────────────┐
│ LEVEL 3: KASUBAG                                        │
│                                                          │
│ • Review kelengkapan administrasi                       │
│ • Koordinasi dengan Pengelola                           │
│                                                          │
│ APPROVE:                                                 │
│ ✅ Sistem auto-generate QR Code Approval                │
│                                                          │
│ REJECT:                                                  │
│ ❌ Input alasan → Kembali ke Operator                   │
└─────────────────────────────────────────────────────────┘
                          ↓
                   📱 NOTIFIKASI
               (WhatsApp ke Pengelola)
```

---

### 3️⃣ TAHAP GENERATE BERKAS (dengan QR Code)

```
┌─────────────────────────────────────────────────────────┐
│ PENGELOLA                                               │
│                                                          │
│ 1. GENERATE DOKUMEN OTOMATIS:                           │
│    Klik "Generate Dokumen"                              │
│                                                          │
│    Sistem auto-generate PDF:                            │
│    📄 Surat Tugas (ST)                                  │
│       • Berisi data perjalanan dinas                    │
│       • Daftar pegawai yang berangkat: 2 orang         │
│         (sudah disesuaikan Sekwan)                      │
│       • Embedded 3 QR Code:                             │
│         [QR Pimpinan] [QR Sekwan] [QR Kasubag]         │
│       • QR Code = Bukti approval (bukan TTD)           │
│                                                          │
│    📄 SPPD                                              │
│       • Berisi estimasi biaya yang sudah disesuaikan   │
│       • Daftar pegawai: 2 orang                        │
│       • Embedded 3 QR Code approval                     │
│                                                          │
│    📄 Surat Penyampaian                                 │
│       • Surat pengantar                                 │
│                                                          │
│ 2. PRINTOUT (OPTIONAL):                                 │
│    • Download PDF                                       │
│    • Printout untuk arsip fisik (jika perlu)           │
│    • Dokumen digital = Dokumen resmi                    │
│                                                          │
│ 3. KIRIM NOTIFIKASI:                                    │
│    📱 WhatsApp ke 2 pegawai yang berangkat:            │
│       - Dr. Budi Santoso                                │
│       - Siti Nurhaliza                                  │
│    Pesan: "Dokumen ST & SPPD siap didownload"          │
└─────────────────────────────────────────────────────────┘
                          ↓
              📱 NOTIFIKASI KE PEGAWAI
         "Dokumen siap didownload dengan QR Code"
```

---

### 4️⃣ TAHAP PELAKSANAAN

```
┌─────────────────────────────────────────────────────────┐
│ PEGAWAI (2 orang yang berangkat)                       │
│                                                          │
│ 1. DOWNLOAD DOKUMEN:                                    │
│    • Download ST & SPPD (PDF dengan QR Code)           │
│    • Verifikasi QR Code (scan untuk cek keaslian)     │
│                                                          │
│ 2. MELAKSANAKAN PERJALANAN DINAS:                      │
│    • Berangkat sesuai jadwal                            │
│    • Laksanakan kegiatan                                │
│                                                          │
│ 3. KUMPULKAN BUKTI (KWITANSI FISIK):                   │
│    📸 Foto/Scan:                                        │
│       • Tiket pesawat + boarding pass                   │
│       • Invoice hotel                                   │
│       • Kwitansi makan (breakfast, lunch, dinner)      │
│       • Kwitansi transport lokal (taxi, grab, dll)     │
│       • Bukti pengeluaran lainnya                       │
│                                                          │
│ 4. FOTO KEGIATAN:                                       │
│    📸 Ambil foto kegiatan (min 3 foto):                │
│       • Foto presentasi                                 │
│       • Foto diskusi/rapat                             │
│       • Foto kunjungan lapangan                         │
│       • Foto bersama peserta                            │
└─────────────────────────────────────────────────────────┘
```

---

### 5️⃣ TAHAP PELAPORAN (Upload Kwitansi Fisik)

```
┌─────────────────────────────────────────────────────────┐
│ PEGAWAI (Setelah perjalanan selesai)                   │
│                                                          │
│ STEP 1: Upload Foto Kegiatan                            │
│ ├─ Pilih perjalanan dinas                              │
│ ├─ Upload minimal 3 foto kegiatan                      │
│ ├─ Input keterangan per foto                           │
│ └─ Submit                                               │
│                                                          │
│ STEP 2: Upload Kwitansi Fisik (Bukti Pengeluaran)     │
│ ├─ Pilih perjalanan dinas                              │
│ │                                                       │
│ ├─ Upload Kwitansi Transport:                          │
│ │  📸 Foto tiket pesawat PP                           │
│ │  📸 Foto boarding pass keberangkatan                 │
│ │  📸 Foto boarding pass kepulangan                    │
│ │  📸 Foto/scan kwitansi taxi/grab                     │
│ │  💰 Total: Rp 2.100.000                             │
│ │                                                       │
│ ├─ Upload Kwitansi Akomodasi:                          │
│ │  📸 Foto invoice hotel (2 malam)                     │
│ │  💰 Total: Rp 2.000.000                             │
│ │                                                       │
│ ├─ Upload Kwitansi Makan:                              │
│ │  📸 Kwitansi makan hari 1 (breakfast, lunch, dinner)│
│ │  📸 Kwitansi makan hari 2                            │
│ │  📸 Kwitansi makan hari 3                            │
│ │  💰 Total: Rp 900.000                               │
│ │                                                       │
│ ├─ Upload Kwitansi Lain-lain:                          │
│ │  📸 Pulsa/internet                                    │
│ │  📸 Fotocopy dokumen                                 │
│ │  💰 Total: Rp 200.000                               │
│ │                                                       │
│ ├─ TOTAL PENGELUARAN: Rp 5.200.000                     │
│ │   (per pegawai)                                       │
│ │                                                       │
│ ├─ Input Catatan/Keterangan (optional)                 │
│ └─ Submit                                               │
│                                                          │
│ 💡 CATATAN PENTING:                                     │
│ • Semua kwitansi fisik harus difoto/scan dengan jelas │
│ • Format: JPG, PNG, PDF                                 │
│ • Max 5MB per file                                      │
│ • Kwitansi fisik WAJIB ada untuk setiap pengeluaran   │
└─────────────────────────────────────────────────────────┘
                          ↓
                   📱 NOTIFIKASI
            (WhatsApp ke Pengelola)
         "Pegawai sudah upload bukti pengeluaran"
```

---

### 6️⃣ TAHAP MONITORING & ARSIP

```
┌─────────────────────────────────────────────────────────┐
│ PENGELOLA                                               │
│                                                          │
│ 1. MONITORING UPLOAD PEGAWAI:                           │
│    • Dashboard: Lihat status upload per pegawai         │
│    • Cek kelengkapan:                                   │
│      ✅ Foto kegiatan (min 3)                           │
│      ✅ Kwitansi transport                              │
│      ✅ Kwitansi akomodasi                              │
│      ✅ Kwitansi makan                                  │
│      ⚠️  Jika belum lengkap → Notif ke pegawai         │
│                                                          │
│ 2. REVIEW BUKTI:                                        │
│    • View semua foto kwitansi                           │
│    • Cek kejelasan foto                                 │
│    • Cek kewajaran nominal                              │
│    • Bandingkan dengan estimasi SPPD                    │
│                                                          │
│ 3. VALIDASI:                                            │
│    ✅ Approve: Jika semua lengkap & wajar              │
│    ❌ Reject: Jika ada yang tidak sesuai               │
│       → Notif ke pegawai untuk perbaiki                 │
│                                                          │
│ 4. ARSIP DIGITAL:                                       │
│    • Simpan semua dokumen                               │
│    • ST & SPPD (dengan QR Code)                        │
│    • Foto kegiatan                                      │
│    • Kwitansi fisik (foto/scan)                        │
│    • Generate laporan realisasi anggaran                │
└─────────────────────────────────────────────────────────┘
                          ↓
                      SELESAI
      (Proses perjalanan dinas selesai, dokumen lengkap)
```

---

## 📋 MENU PER ROLE

### 1. 👨‍💼 OPERATOR/ADMIN

```
🏠 Dashboard
📝 Permohonan Surat
   ├─ Buat Permohonan Baru
   ├─ Daftar Permohonan
   ├─ Edit Permohonan (jika di-reject)
   └─ Detail Permohonan & Status Approval
👥 Anggota Organisasi
📊 Laporan
🔔 Notifikasi
👤 Profil
```

---

### 2. 👔 PIMPINAN

```
🏠 Dashboard
✅ Approval Level 1
   ├─ Daftar Permohonan Menunggu
   ├─ Review Detail Permohonan
   ├─ APPROVE (auto-generate QR Code)
   └─ REJECT (dengan alasan)
📄 Daftar Permohonan (semua)
📊 Monitoring
🔍 Verifikasi QR Code
🔔 Notifikasi
👤 Profil
```

---

### 3. 📋 SEKWAN

```
🏠 Dashboard
✅ Approval Level 2 (CRITICAL!)
   ├─ Daftar Permohonan dari Pimpinan
   ├─ Review Permohonan
   ├─ CEK ANGGARAN:
   │  ├─ Pagu anggaran organisasi
   │  ├─ Sisa anggaran
   │  ├─ Estimasi biaya permohonan
   │  └─ Validasi: Cukup/Tidak
   │
   ├─ JIKA ANGGARAN CUKUP:
   │  └─ APPROVE (auto-generate QR Code)
   │
   ├─ JIKA ANGGARAN TIDAK CUKUP:
   │  ├─ OPSI 1: REJECT & MINTA REVISI
   │  │  ├─ Input alasan detail
   │  │  └─ Saran: Kurangi jadi X orang
   │  │
   │  ├─ OPSI 2: ADJUST JUMLAH PEGAWAI ⭐
   │  │  ├─ Kurangi anggota yang berangkat
   │  │  ├─ Pilih pegawai yang tetap & dibatalkan
   │  │  ├─ Sistem adjust estimasi biaya
   │  │  ├─ Notif ke pegawai yang dibatalkan
   │  │  └─ APPROVE dengan penyesuaian
   │  │
   │  └─ OPSI 3: KONSULTASI OPERATOR
   │     └─ Chat/telpon untuk diskusi
   │
   └─ History Approval
💰 Anggaran
   ├─ Monitoring Anggaran per Organisasi
   ├─ Realisasi Anggaran
   └─ Pencadangan Anggaran
📊 Monitoring
🔍 Verifikasi QR Code
🔔 Notifikasi
👤 Profil
```

---

### 4. 👨‍💼 KASUBAG

```
🏠 Dashboard
✅ Approval Level 3
   ├─ Daftar Permohonan dari Sekwan
   ├─ Review Kelengkapan Administrasi
   ├─ APPROVE (auto-generate QR Code)
   └─ REJECT (dengan alasan)
📄 Daftar Permohonan
📊 Monitoring
🔍 Verifikasi QR Code
🔔 Notifikasi
👤 Profil
```

---

### 5. 📝 PENGELOLA

```
🏠 Dashboard
📄 Pengelolaan Berkas
   ├─ Daftar Permohonan Approved
   ├─ Generate Dokumen (ST, SPPD) dengan QR
   ├─ Download PDF
   ├─ Printout (optional)
   └─ Status Berkas
📸 Monitoring Upload Pegawai
   ├─ Foto Kegiatan
   │  ├─ View foto yang diupload
   │  ├─ Cek kelengkapan (min 3 foto)
   │  └─ Approve/Reject
   │
   └─ Kwitansi Fisik (Bukti Pengeluaran)
      ├─ View semua kwitansi yang diupload
      ├─ Cek kelengkapan per jenis:
      │  • Transport ✓
      │  • Akomodasi ✓
      │  • Makan ✓
      │  • Lain-lain ✓
      ├─ Cek kejelasan foto
      ├─ Validasi nominal
      └─ Approve/Reject
📁 Arsip Digital
   ├─ ST & SPPD (dengan QR)
   ├─ Foto Kegiatan
   ├─ Kwitansi Fisik
   └─ Laporan Realisasi
📊 Laporan
🔍 Verifikasi QR Code
🔔 Notifikasi
👤 Profil
```

---

### 6. 👨‍💻 PEGAWAI

```
🏠 Dashboard
   └─ Penugasan Saya (Aktif/Dibatalkan)
   └─ Status Upload Dokumen
📋 Penugasan Saya
   ├─ Surat Tugas Aktif
   │  ├─ Detail ST
   │  ├─ Download ST (PDF dengan QR Code)
   │  └─ Verifikasi QR Code
   │
   └─ SPPD Aktif
      ├─ Detail SPPD
      ├─ Download SPPD (PDF dengan QR Code)
      └─ Verifikasi QR Code
📸 Upload Foto Kegiatan
   ├─ Pilih Perjalanan Dinas
   ├─ Upload Foto (min 3)
   │  • Drag & drop atau browse
   │  • Format: JPG, PNG
   │  • Max 5MB per file
   ├─ Input Keterangan per Foto
   └─ Submit
🧾 Upload Kwitansi Fisik (PENTING!)
   ├─ Pilih Perjalanan Dinas
   │
   ├─ Upload Kwitansi Transport:
   │  ├─ [📤 Upload] Tiket pesawat
   │  ├─ [📤 Upload] Boarding pass
   │  ├─ [📤 Upload] Kwitansi taxi/transport lokal
   │  └─ Input total: Rp _______
   │
   ├─ Upload Kwitansi Akomodasi:
   │  ├─ [📤 Upload] Invoice hotel
   │  └─ Input total: Rp _______
   │
   ├─ Upload Kwitansi Makan:
   │  ├─ [📤 Upload] Kwitansi hari 1
   │  ├─ [📤 Upload] Kwitansi hari 2
   │  ├─ [📤 Upload] Kwitansi hari 3
   │  └─ Input total: Rp _______
   │
   ├─ Upload Kwitansi Lain-lain:
   │  ├─ [📤 Upload] Pulsa/internet
   │  ├─ [📤 Upload] Lainnya
   │  └─ Input total: Rp _______
   │
   ├─ TOTAL PENGELUARAN (auto-calculate)
   ├─ Input Catatan (optional)
   └─ Submit
📖 Riwayat
   ├─ Riwayat Perjalanan Dinas
   └─ Riwayat Upload Dokumen
🔍 Verifikasi QR Code
🔔 Notifikasi
👤 Profil
```

---

## 🎨 WIREFRAME

### 1. Modal Approval Sekwan (Adjust Pegawai)

```
┌────────────────────────────────────────────────────────────┐
│ ✅ APPROVAL LEVEL 2 - VERIFIKASI ANGGARAN         [✕]    │
├────────────────────────────────────────────────────────────┤
│                                                             │
│ Nomor: 001/KMS-I/06/14/2025                                │
│ Organisasi: KOMISI-I                                       │
│ Perihal: Studi Banding Pelayanan Publik Jakarta           │
│                                                             │
│ ┌────────────────────────────────────────────────────────┐│
│ │ 💰 CEK ANGGARAN                                        ││
│ ├────────────────────────────────────────────────────────┤│
│ │ Pagu Anggaran Komisi I:       Rp 100.000.000         ││
│ │ Terpakai:                     Rp  80.000.000          ││
│ │ Dicadangkan:                  Rp  10.000.000          ││
│ │ ─────────────────────────────────────────────────────  ││
│ │ Sisa Anggaran:                Rp  10.000.000          ││
│ │                                                         ││
│ │ Estimasi Permohonan:          Rp  15.000.000 ❌       ││
│ │ Status: ⚠️ ANGGARAN TIDAK CUKUP!                      ││
│ │ Kurang: Rp 5.000.000                                   ││
│ └────────────────────────────────────────────────────────┘│
│                                                             │
│ ┌────────────────────────────────────────────────────────┐│
│ │ 👥 DAFTAR PEGAWAI YANG DIAJUKAN (3 orang)             ││
│ ├────────────────────────────────────────────────────────┤│
│ │                                                         ││
│ │ ☑️ 1. Dr. Budi Santoso (Ketua Rombongan)              ││
│ │    Estimasi: Rp 5.000.000                             ││
│ │    [Tetap Berangkat]                                   ││
│ │                                                         ││
│ │ ☑️ 2. Siti Nurhaliza (Anggota)                        ││
│ │    Estimasi: Rp 5.000.000                             ││
│ │    [Tetap Berangkat]                                   ││
│ │                                                         ││
│ │ ☐ 3. Andi Wijaya (Anggota)                            ││
│ │    Estimasi: Rp 5.000.000                             ││
│ │    [❌ Batalkan Penugasan]                            ││
│ │                                                         ││
│ │ ─────────────────────────────────────────────────────  ││
│ │ Total Pegawai Berangkat: 2 orang                       ││
│ │ Total Estimasi Baru:     Rp 10.000.000 ✅             ││
│ │ Status: ✅ ANGGARAN CUKUP!                            ││
│ └────────────────────────────────────────────────────────┘│
│                                                             │
│ ┌────────────────────────────────────────────────────────┐│
│ │ 📝 PILIHAN TINDAKAN                                    ││
│ ├────────────────────────────────────────────────────────┤│
│ │                                                         ││
│ │ ⚪ OPSI 1: REJECT & MINTA REVISI                      ││
│ │    Kembalikan ke Operator untuk revisi                 ││
│ │    [Input Alasan...]                                   ││
│ │                                                         ││
│ │ ⚫ OPSI 2: ADJUST JUMLAH PEGAWAI (Aktif)              ││
│ │    Saya kurangi sendiri dari 3 → 2 orang             ││
│ │    Pegawai yang dibatalkan akan dapat notifikasi       ││
│ │                                                         ││
│ │ ⚪ OPSI 3: KONSULTASI OPERATOR                        ││
│ │    Diskusi dulu sebelum keputusan                      ││
│ │                                                         ││
│ └────────────────────────────────────────────────────────┘│
│                                                             │
│ Catatan untuk Operator (optional):                        │
│ ┌─────────────────────────────────────────────────────┐  │
│ │ Anggaran tidak mencukupi untuk 3 orang. Saya         │  │
│ │ batalkan penugasan Andi Wijaya agar sesuai anggaran. │  │
│ └─────────────────────────────────────────────────────┘  │
│                                                             │
│ [⬅️ Batal]  [❌ Reject]  [✅ Approve dengan Penyesuaian]  │
│                                                             │
│ ℹ️ Jika approve, QR Code akan otomatis ter-generate       │
└────────────────────────────────────────────────────────────┘
```

---

### 2. Form Upload Kwitansi Fisik (Pegawai)

```
┌─────────────────────────────────────────────────────────────────────┐
│ 🧾 UPLOAD KWITANSI FISIK (Bukti Pengeluaran)     [💾 Simpan Draft] │
│                                                   [❌ Batal]         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│ SPPD: 001/KMS-I/06/14/2025                                          │
│ Kegiatan: Studi Banding Pelayanan Publik Jakarta                   │
│ Periode: 20-22 Juni 2025 (3 hari)                                  │
│ Estimasi SPPD: Rp 5.000.000,- (per orang)                          │
│                                                                      │
│ ┌──────────────────────────────────────────────────────┐           │
│ │ 📸 UPLOAD KWITANSI FISIK                             │           │
│ ├──────────────────────────────────────────────────────┤           │
│ │                                                       │           │
│ │ ✈️ TRANSPORT                                         │           │
│ │ ┌─────────────────────────────────────────────────┐  │           │
│ │ │ [📤 Drop files or click to upload]             │  │           │
│ │ │ Format: JPG, PNG, PDF | Max: 5MB per file      │  │           │
│ │ └─────────────────────────────────────────────────┘  │           │
│ │                                                       │           │
│ │ ✅ tiket_pesawat_pp.pdf (1.2 MB)                     │           │
│ │    [👁️ Preview] [🗑️ Hapus]                          │           │
│ │                                                       │           │
│ │ ✅ boarding_pass_berangkat.jpg (890 KB)              │           │
│ │    [👁️ Preview] [🗑️ Hapus]                          │           │
│ │                                                       │           │
│ │ ✅ boarding_pass_pulang.jpg (920 KB)                 │           │
│ │    [👁️ Preview] [🗑️ Hapus]                          │           │
│ │                                                       │           │
│ │ ✅ kwitansi_taxi.jpg (650 KB)                        │           │
│ │    [👁️ Preview] [🗑️ Hapus]                          │           │
│ │                                                       │           │
│ │ Total Transport: [Rp 2.100.000__________]           │           │
│ │                                                       │           │
│ │ ─────────────────────────────────────────────────── │           │
│ │                                                       │           │
│ │ 🏨 AKOMODASI                                         │           │
│ │ ┌─────────────────────────────────────────────────┐  │           │
│ │ │ [📤 Upload invoice hotel]                       │  │           │
│ │ └─────────────────────────────────────────────────┘  │           │
│ │                                                       │           │
│ │ ✅ invoice_hotel_hyatt.pdf (1.1 MB)                  │           │
│ │    [👁️ Preview] [🗑️ Hapus]                          │           │
│ │                                                       │           │
│ │ Total Akomodasi: [Rp 2.000.000__________]           │           │
│ │                                                       │           │
│ │ ─────────────────────────────────────────────────── │           │
│ │                                                       │           │
│ │ 🍽️ MAKAN                                             │           │
│ │ ┌─────────────────────────────────────────────────┐  │           │
│ │ │ [📤 Upload kwitansi makan]                      │  │           │
│ │ └─────────────────────────────────────────────────┘  │           │
│ │                                                       │           │
│ │ ✅ kwitansi_makan_hari1.jpg (3 file - 2.1 MB)       │           │
│ │ ✅ kwitansi_makan_hari2.jpg (3 file - 1.9 MB)       │           │
│ │ ✅ kwitansi_makan_hari3.jpg (2 file - 1.3 MB)       │           │
│ │    [👁️ Preview All] [🗑️ Hapus]                      │           │
│ │                                                       │           │
│ │ Total Makan: [Rp 900.000__________]                  │           │
│ │                                                       │           │
│ │ ─────────────────────────────────────────────────── │           │
│ │                                                       │           │
│ │ 📱 LAIN-LAIN                                         │           │
│ │ ┌─────────────────────────────────────────────────┐  │           │
│ │ │ [📤 Upload bukti lainnya]                       │  │           │
│ │ └─────────────────────────────────────────────────┘  │           │
│ │                                                       │           │
│ │ ✅ struk_pulsa.jpg (450 KB)                          │           │
│ │ ✅ kwitansi_fotocopy.jpg (380 KB)                    │           │
│ │    [👁️ Preview] [🗑️ Hapus]                          │           │
│ │                                                       │           │
│ │ Total Lain-lain: [Rp 200.000__________]             │           │
│ │                                                       │           │
│ │ ═══════════════════════════════════════════════════ │           │
│ │ TOTAL PENGELUARAN:        Rp 5.200.000              │           │
│ │ Estimasi SPPD:            Rp 5.000.000              │           │
│ │ Selisih:                  Rp   200.000 (Lebih)      │           │
│ │ Status: ⚠️ Melebihi estimasi (perlu catatan)        │           │
│ │                                                       │           │
│ └──────────────────────────────────────────────────────┘           │
│                                                                      │
│ Catatan Tambahan (Wajib jika melebihi estimasi):                   │
│ ┌──────────────────────────────────────────────────────┐           │
│ │ Biaya transport lokal melebihi estimasi karena       │           │
│ │ tidak ada transportasi umum ke lokasi kegiatan.     │           │
│ │ Terpaksa menggunakan taxi.                           │           │
│ └──────────────────────────────────────────────────────┘           │
│                                                                      │
│ [⬅️ Kembali]  [💾 Simpan Draft]  [✅ Submit]                       │
│                                                                      │
│ ℹ️ Pastikan semua kwitansi fisik difoto/scan dengan jelas          │
└─────────────────────────────────────────────────────────────────────┘
```

---

### 3. Dashboard Monitoring Pengelola

```
┌─────────────────────────────────────────────────────────────────────┐
│ [Logo DPRD] Sistem Perjalanan Dinas DPRD     👤 Rina Marlina       │
│                                               Pengelola              │
├─────────────────────────────────────────────────────────────────────┤
│ 🏠 Dashboard  📄 Berkas  📸 Monitoring  📁 Arsip  🔍 Verifikasi    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│ 📊 DASHBOARD MONITORING                                             │
│                                                                      │
│ ┌──────────────────┬──────────────────┬──────────────────┐         │
│ │ 📄 Generate      │ 📸 Upload Foto   │ 🧾 Upload Kwitansi│         │
│ │                  │                  │                  │         │
│ │      3           │      2           │      5           │         │
│ │   Perlu Generate │   Belum Lengkap  │   Menunggu Review│         │
│ └──────────────────┴──────────────────┴──────────────────┘         │
│                                                                      │
│ ┌─────────────────────────────────────────────────────────┐        │
│ │ 📸 MONITORING UPLOAD PEGAWAI                             │        │
│ ├─────────────────────────────────────────────────────────┤        │
│ │                                                           │        │
│ │ 👤 Dr. Budi Santoso - SPPD 001/KMS-I/06/14/2025         │        │
│ │ Studi Banding Jakarta | Selesai: 22 Jun 2025            │        │
│ │                                                           │        │
│ │ Status Upload:                                            │        │
│ │ ✅ Foto Kegiatan: 5 foto (Lengkap)                       │        │
│ │ ⏰ Kwitansi Fisik: Belum upload                          │        │
│ │                                                           │        │
│ │ [👁️ Lihat Foto] [📱 Kirim Reminder]                     │        │
│ │                                                           │        │
│ │ ─────────────────────────────────────────────────────── │        │
│ │                                                           │        │
│ │ 👤 Siti Nurhaliza - SPPD 001/KMS-I/06/14/2025           │        │
│ │ Studi Banding Jakarta | Selesai: 22 Jun 2025            │        │
│ │                                                           │        │
│ │ Status Upload:                                            │        │
│ │ ✅ Foto Kegiatan: 4 foto (Lengkap)                       │        │
│ │ ⏰ Kwitansi Fisik: Submitted (Menunggu review)           │        │
│ │    • Transport: 4 file ✅                                │        │
│ │    • Akomodasi: 1 file ✅                                │        │
│ │    • Makan: 8 file ✅                                    │        │
│ │    • Lain-lain: 2 file ✅                                │        │
│ │    Total: Rp 5.200.000 (Melebihi estimasi Rp 200.000)  │        │
│ │                                                           │        │
│ │ [👁️ Review Kwitansi] [✅ Approve] [❌ Reject]           │        │
│ └─────────────────────────────────────────────────────────┘        │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🔐 PERMISSION MATRIX V3.0 FINAL

| Fitur | Operator | Pimpinan | Sekwan | Kasubag | Pengelola | Pegawai |
|-------|----------|----------|--------|---------|-----------|---------|
| **Buat Permohonan** | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| **Edit Permohonan** | ✅ (Jika reject) | ❌ | ❌ | ❌ | ❌ | ❌ |
| **Approve Level 1 + QR** | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Approve Level 2 + QR** | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| **Adjust Jumlah Pegawai** | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| **Approve Level 3 + QR** | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ |
| **Generate Berkas QR** | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |
| **Upload Foto Kegiatan** | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| **Upload Kwitansi Fisik** | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| **Review Upload Pegawai** | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |
| **Approve Upload** | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |
| **Verifikasi QR Code** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Arsip Digital** | View Own | View All | View All | View All | ✅ | View Own |

---

## 📊 CONTOH KASUS LENGKAP

### **KASUS: Anggaran Tidak Cukup**

```
PERMOHONAN AWAL:
- Organisasi: KOMISI-I
- Perihal: Studi Banding ke Jakarta
- Pegawai: 3 orang (Budi, Siti, Andi)
- Estimasi: Rp 15.000.000
- Sisa Anggaran: Rp 10.000.000
- Status: ❌ TIDAK CUKUP (Kurang Rp 5.000.000)

ALUR:
1. Operator submit permohonan
   → Notif ke Pimpinan

2. Pimpinan approve (Level 1)
   → QR Code ter-generate
   → Notif ke Sekwan

3. Sekwan cek anggaran:
   ❌ Tidak cukup!
   
   SEKWAN PILIH OPSI 2: Adjust Pegawai
   
   Action:
   - Batalkan Andi Wijaya
   - Yang berangkat: Budi + Siti (2 orang)
   - Estimasi baru: Rp 10.000.000
   - ✅ Anggaran cukup!
   
   Sekwan APPROVE
   → QR Code ter-generate
   → Notif ke:
      • Kasubag (untuk approval lanjut)
      • Andi Wijaya (penugasan dibatalkan)
      • Operator (info penyesuaian)

4. Kasubag approve (Level 3)
   → QR Code ter-generate
   → Notif ke Pengelola

5. Pengelola generate dokumen:
   ST & SPPD untuk 2 orang (Budi + Siti)
   → Embedded 3 QR Code approval
   → Notif ke Budi & Siti

6. Budi & Siti:
   - Download ST & SPPD
   - Laksanakan perjalanan dinas
   - Upload foto kegiatan
   - Upload kwitansi fisik

7. Pengelola:
   - Review upload
   - Approve
   - Arsip
