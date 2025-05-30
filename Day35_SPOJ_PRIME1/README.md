The initial program got time limit exit, the function isPrime check all the way from 2 until n-1, if we check for lets say 10^6 this is computationally expensive. Also the nested loop got another time complex problem

The second soluton get sigsev
"SIGSEGV" (Segmentation Fault) biasanya terjadi karena program mencoba mengkases memori yang tidak seharusnya diakses, seperti akses memory array yang kosong dsb.

## Iterator
Iterator adalah konsep dalam C++ yang berfungsi sebagai abstraksi untuk menelusuri elemen-elemen dalam sebuah kontainer (seperti vector, list, set, dsb). Iterator ini dirancang untuk 
- Memberikan cara yang seragam untuk mengakses isi kontainer, tanpa peduli bagaikana kontainer itu diimplementasikan di belakang layar.
- Menyerupai pointer (tapi lebih cerdas dan aman), sehingga kita bisa "berjalan" melalui elemen2 dengan cara yang terkontrol

## Mengapa Harus vector<int>::iterator p?
Deklarasi ini diperlukan karena:
1. primes.begin() bukan angka biasa
Fungsi `primes.begin()` mengembalikan sebuah **iterator**, bukan int. Iterator adalah tipe data khusus yang dibuat oleh kelas vector untuk menunjuk ke elemen-elemen di dalamnya. jika ditulis seperti **int p = primes.begins()**, kompiler akan mengeluh karena tipe data tidak cocok. **begin*()** tidak mengembalikan indeks (seperti 0) atau nilai elemen (seperti 2), melainkan object iterator yang tahu posisi elemen pertama.

2. **Iterator Bukan Hanya Indeks**
Meskipun dalam vektor iterator sering diasosiasikan dengan posisi (karena vektor adalah array dinamis), iterator lebih umum dari itu. Iterator bisa digunakan pada kontainer lain seperti list atau set, yang tidak punya indeks langsung. Dengan mendeklarasikan vector<int>::iterator, kamu memastikan p punya tipe yang sesuai untuk menelusuri vektor dengan benar.

## Kenapa tidak bisa pakai loop biasa dengan integer?
**Jawabannya: Bisa**, tetapi iterator sering dipilih karena pendekatan yang lebih generik, efisien dan modern (sesuai STL)

Apa itu "Generik" dalam Pemrograman?
Dalam pemrograman, "generik" berarti sesuatu yang dapat digunakan secara umum untuk berbagai situasi atau tipe data yang bebereda tanpa harus menulis ulang kode khusus untuk setiap kasus. 

Dalam konteks iterator dan kode ini, "generik" merujuk pada kemampuan iterator untuk bekerja dengan berbagai jenis kontainer (vector, list, list dsb) tanpa harus mengubah logika utama kode

# Tentang Sieve of Eratosthenes
Sieve of Eratosthenes adalah algoritma klasik untuk menemukan bilangan prima. Cara kerjanya adalah dengan "menyaring" bilangan yang bukan prima (komposit) dari daftar angka, sehingga yang tersisa adalah bilangan prima. Dalam program ini, algoritma dimodifikasi untuk dua tahap:

Tahap Pertama:
- Membuat daftar bilangan prima awal hingga 32,000.
- Mulai dengan 2 sebagai prima pertama, lalu periksa bilangan ganjil (3, 5, 7, dst.) hingga akar kuadrat dari batas atas (√i).
- Jika suatu bilangan tidak habis dibagi prima sebelumnya, maka itu prima dan ditambahkan ke daftar.

Tahap Kedua:
- Menggunakan daftar prima awal untuk menyaring bilangan komposit dalam rentang M hingga N (input pengguna).
- Menandai kelipatan dari setiap bilangan prima yang lebih kecil dari √N sebagai bukan prima.
- Bilangan yang tidak ditandai dalam rentang tersebut adalah bilangan prima dan dicetak.

Algoritma ini efisien karena hanya memeriksa bislangan prima yang diperlukan dan mengurangi jumlah operasi pembagian.