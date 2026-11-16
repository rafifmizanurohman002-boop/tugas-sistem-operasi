# Tugas Simulasi "Selamatkan Server" — Sistem Operasi

**Nama:** Rafif Mizanurohman
**NIM:** 312510377
**Mata Kuliah:** Sistem Operasi

## Skenario
Server Linux disusupi proses `stress --cpu 2 --timeout 3600 &` yang membakar CPU.
Penanganannya dilakukan berurutan tanpa restart server:

| Tahap | Perintah | Tujuan |
|---|---|---|
| 1 | `stress --cpu 2 --timeout 3600 &` | Suntik proses penyusup (background) |
| 2 | `htop` | Audit: CPU 100% + identifikasi proses |
| 3 | `pgrep stress` | Lacak PID presisi proses penyusup |
| 4 | `kill -9 <PID>` | Eksekusi SIGKILL ("Sinyal Dewa") |
| 5 | `pgrep stress \|\| echo ...`, `top -bn2 -d1 \| grep Cpu` | Verifikasi proses hilang & CPU normal (99% idle) |

## Isi Repositori
- `Laporan-Simulasi-Selamatkan-Server.pdf` — laporan lengkap (cover, analisis, kesimpulan)
- `screenshots/` — 5 screenshot berurutan:
  1. `01-inject-stress.png` — injeksi `stress`
  2. `02-htop-audit.png` — audit CPU dengan htop
  3. `03-pgrep-pid.png` — pelacakan PID dengan pgrep
  4. `04-kill-9.png` — eksekusi `kill -9`
  5. `05-verify.png` — verifikasi akhir

## Lingkungan
- Terminal Linux berbasis web: webminal.org
- Kernel: `5.4.168-1.el7.elrepo.x86_64`, 2 core CPU
