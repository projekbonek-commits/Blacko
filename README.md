# Black Pixel Auto Overlay

Aplikasi Android untuk menutup dead/stuck pixel dengan overlay hitam.

Fitur:
- Auto rotate mengikuti orientasi layar.
- Maksimal 4 layer hitam.
- Tiap layer punya ON/OFF, Posisi X, Posisi Y, Lebar, dan Panjang.
- Overlay tidak menangkap touch, jadi layar di bawahnya tetap bisa dipakai.
- Preset tersimpan otomatis di SharedPreferences.

## Build APK pakai GitHub Actions

1. Upload semua file project ini ke repository GitHub.
2. Buka tab **Actions**.
3. Pilih workflow **Build APK**.
4. Tekan **Run workflow**.
5. Setelah selesai, buka hasil run-nya.
6. Download artifact **BlackPixelAutoOverlay-debug-apk**.
7. Extract ZIP artifact, lalu install file `.apk` di HP.

## Upload dari Termux

```bash
pkg update -y
pkg install -y git gh unzip

gh auth login
cd ~/storage/downloads
unzip BlackPixelAutoOverlay_GitHub.zip
cd BlackPixelAutoOverlay_GitHub

git init
git add .
git commit -m "Initial Android overlay app"
git branch -M main
gh repo create black-pixel-auto-overlay --public --source=. --remote=origin --push
```

Lalu buka repo di GitHub > **Actions** > **Build APK** > **Run workflow**.

## Cara pakai app

1. Install APK.
2. Buka aplikasi.
3. Tekan **Buka Izin Draw Over Apps** lalu aktifkan izin overlay.
4. Atur layer sesuai posisi dead pixel.
5. Tekan **START BLACK OVERLAY**.
6. Kalau posisi kurang pas, ubah slider lalu tekan **UPDATE OVERLAY**.

## Catatan rotasi

Koordinat disimpan sebagai posisi portrait. Saat layar rotate, rectangle diputar otomatis supaya area hitam tetap mengikuti posisi fisik panel.

Kalau di device tertentu arah landscape-nya kebalik, buka file:

`app/src/main/java/com/projek/blackpixeloverlay/OverlayDrawingView.kt`

Lalu tukar isi formula `Surface.ROTATION_90` dan `Surface.ROTATION_270`.
