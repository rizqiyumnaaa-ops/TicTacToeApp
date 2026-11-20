# Tic Tac Toe

Aplikasi Tic Tac Toe untuk dua pemain pada satu perangkat. Pemain X dan O
bergantian mengisi papan 3 × 3. Tiga simbol yang sama dalam satu garis
horizontal, vertikal, atau diagonal menghasilkan kemenangan; papan penuh tanpa
pemenang menghasilkan seri.

## Teknologi

- React Native dan Expo SDK 58
- TypeScript
- React Hooks (`useState`)
- `StyleSheet`, Flexbox, dan `Pressable`
- `react-native-safe-area-context` untuk menjaga konten dari notch dan indikator
  Home iPhone

## Cara kerja program

1. **`useState`** menyimpan data yang dapat berubah selama permainan. Aplikasi
   memiliki state untuk papan, giliran pemain (`xIsNext`), pemenang, dan kondisi
   seri. Perubahan state membuat React menampilkan ulang tampilan terbaru.
2. **Array `board`** berisi sembilan nilai. Setiap nilai mewakili satu kotak dan
   berisi `'X'`, `'O'`, atau `null` jika masih kosong.
3. **`calculateWinner(cells)`** memeriksa delapan kombinasi kemenangan. Jika
   tiga posisi dalam satu kombinasi berisi simbol yang sama, fungsi
   mengembalikan simbol tersebut; jika belum ada pemenang, hasilnya `null`.
4. **`handlePress(index)`** mengabaikan kotak terisi dan permainan yang sudah
   selesai. Fungsi menyalin papan, menaruh simbol pemain saat ini, memperbarui
   papan, lalu memeriksa kemenangan atau seri dan mengganti giliran.
5. **`resetGame()`** mengosongkan papan, mengembalikan giliran ke X, dan
   menghapus hasil permainan sebelumnya.
6. **Immutability dan spread operator:** `const nextBoard = [...board]` membuat
   salinan array sebelum satu kotak diubah. State lama tidak dimutasi langsung,
   sehingga React dapat mendeteksi perubahan dengan benar.
7. **Flexbox** mengatur susunan pemain, baris dan kotak papan, serta posisi
   konten. Ukuran papan mengikuti lebar layar dan konten dapat digulir jika
   tinggi layar terbatas.

## Menjalankan di Expo Go pada iPhone

1. Buka terminal di VS Code dan pastikan lokasinya berada di folder proyek
   `TicTacToeApp`.
2. Jalankan:

   ```bash
   npx expo start
   ```

3. Sambungkan PC dan iPhone ke jaringan Wi-Fi yang sama.
4. Buka Expo Go di iPhone, lalu pindai QR code yang ditampilkan Expo.
5. Tunggu bundel aplikasi dimuat di Expo Go.

Jika koneksi jaringan lokal tidak berhasil, jalankan:

```bash
npx expo start --tunnel
```

## Skenario pemeriksaan

- X mengisi kotak kosong terlebih dahulu, lalu giliran berpindah ke O.
- Kotak yang sudah diisi tidak berubah ketika ditekan lagi.
- Kemenangan terdeteksi untuk setiap garis horizontal, vertikal, dan diagonal.
- Sembilan kotak terisi tanpa pemenang menampilkan status seri.
- Setelah menang atau seri, kotak lain tidak dapat diisi.
- **New Game** mengosongkan papan dan mengembalikan giliran ke X.
