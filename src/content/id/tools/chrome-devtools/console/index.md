project_path: /web/tools/_project.yaml
book_path: /web/tools/_book.yaml
description: Pelajari cara menavigasi Konsol JavaScript di Chrome DevTools.

{# wf_updated_on: 2019-02-06 #}
{# wf_published_on: 2015-05-10 #}
{# wf_blink_components: Platform>DevTools #}

# Menggunakan Console {: .page-title }

{% include "web/_shared/contributors/kaycebasques.html" %}
{% include "web/_shared/contributors/andismith.html" %}
{% include "web/_shared/contributors/megginkearney.html" %}
{% include "web/_shared/contributors/pbakaus.html" %}

Pelajari cara: membuka DevTools Console, menumpuk pesan 
berlebihan atau menampilkannya di baris masing-masing, menghapus atau mempertahankan 
keluaran atau menyimpannya ke file, memfilter keluaran, dan mengakses setelan
Console tambahan.

### TL;DR {: .hide-from-toc }
- Buka Console sebagai panel tersendiri atau sebagai panel samping di sebelah panel lain.
- Tumpuk pesan yang berlebihan, atau tampilkan di barisnya masing-masing.
- Hapus atau pertahankan output antarhalaman, atau simpan ke file.
- Filter output menurut tingkat keseriusannya, dengan menyembunyikan pesan jaringan, atau dengan pola ekspresi reguler.

## Membuka Console

Akses Console sebagai panel layar-penuh tersendiri:

![Panel Console](images/console-panel.png)

Atau berupa panel samping yang dibuka di sebelah panel lain:

![Panel samping Console](images/console-drawer.png)

### Buka sebagai panel

Untuk membuka panel **Console**:

* Tekan <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>J</kbd> (Windows / Linux) atau
  <kbd>Cmd</kbd>+<kbd>Opt</kbd>+<kbd class="kbd">J</kbd> (Mac).
* Jika DevTools terbuka, tekan tombol **Console**.

Bila Anda membuka panel Console, panel samping Console akan diciutkan secara otomatis.

### Buka sebagai panel samping

Untuk membuka Console sebagai panel samping di sebelah panel lain, lakukan salah satu hal berikut:

* Tekan <kbd>Esc</kbd> saat DevTools terfokus.
* Tekan tombol **Customize and control DevTools** dan tekan tombol 
  **Show console**.

![Show console](images/show-console.png)

## Penumpukan pesan

Jika pesan diulang secara berturutan, Console tidak akan mencetak setiap
contoh pesan pada baris baru, tetapi "menumpuk" pesan tersebut
dan menampilkan angka di margin kiri. Angka itu menunjukkan berapa kali
pesan diulangi.

![Penumpukan pesan](images/message-stacking.png)

Jika Anda lebih menyukai entri baris sendiri-sendiri untuk setiap log, aktifkan **Show timestamps**
dari pengaturan DevTools.

![Show timestamps](images/show-timestamps.png)

Karena stempel waktu setiap pesan berbeda, setiap pesan akan ditampilkan
pada barisnya sendiri.

![Konsol stempel waktu](images/timestamped-console.png)

## Menggunakan histori Console

### Mengosongkan histori {: #clearing}

Anda bisa mengosongkan histori konsol dengan melakukan salah satu hal berikut:

* Klik kanan Console dan tekan **Clear console**.
* Ketikkan `clear()` di Console.
* Panggil `console.clear()` dari dalam kode JavaScript.
* Tekan <kbd class="kbd">Ctrl</kbd>+<kbd class="kbd">L</kbd> 
  (Mac, Windows, Linux).

### Mempertahankan histori {: #preserve-log}

Aktifkan kotak centang **Preserve log** di bagian atas konsol untuk mempertahankan
histori konsol di sela penyegaran atau perubahan laman. Pesan akan disimpan
hingga Anda mengosongkan Console atau menutup tab.

### Menyimpan histori

Klik kanan di Console dan pilih **Save as** untuk menyimpan keluaran
konsol ke file log.

![Simpan Console ke file log](images/console-save-as.png)

## Memilih konteks eksekusi {: #execution-context }

Menu tarik-turun yang disorot biru di tangkapan layar berikut disebut
**Pemilih Konteks Eksekusi**.

![Pemilih Konteks Eksekusi](images/execution-context-selector.png)

Biasanya konteks disetel ke `top` (bingkai atas laman).

Bingkai dan ekstensi lain beroperasi di konteksnya masing-masing. Untuk menggarap konteks
lain ini, Anda perlu memilihnya dari menu tarik-turun. Misalnya,
jika ingin melihat keluaran log elemen `<iframe>` dan mengubah
variabel yang berada di konteks itu, Anda perlu memilihnya dari
menu tarik-turun Pemilih Konteks Eksekusi.

Secara default Console berada dalam konteks `top`, kecuali jika Anda mengakses DevTools dengan
memeriksa elemen di dalam konteks lain. Misalnya, jika Anda memeriksa
elemen `<p>` di dalam konteks `<iframe>`, DevTools menyetel Pemilih
Konteks Eksekusi ke konteks `<iframe>` tersebut.

Saat Anda sedang menggarap konteks selain `top`, DevTools menyoroti
Pemilih Konteks Eksekusi dengan warna merah, seperti dalam screenshot berikut. Ini karena
developer jarang perlu menggarap konteks selain `top`. Tentu
membingungkan kalau kita mengetikkan suatu variabel, mengharapkan suatu nilai, tetapi malah melihat bahwa
variabel itu `undefined` (karena definisinya berada di konteks lain).

![Pemilih Konteks Eksekusi disorot merah](images/non-top-context.png)

## Memfilter keluaran Console

Klik tombol **Filter** 
(![tombol filter](images/filter-button.png){:.inline})
untuk memfilter keluaran console. Anda bisa memfilter menurut tingkat keseriusan, menurut ekspresi 
reguler, atau dengan menyembunyikan pesan jaringan.

![Keluaran Konsol Difilter](images/filtered-console.png)

Memfilter menurut tingkat keparahan setara dengan yang berikut ini:

<table class="responsive">
  <thead>
     <tr>
      <th colspan="2">Opsi &amp; Tampilan</th>
    </tr>   
  </thead>
  <tbody>
  <tr>
    <td>Semua</td>
    <td>Menampilkan semua keluaran konsol</td>
  </tr>
  <tr>
    <td>Errors</td>
    <td>Hanya menampilkan keluaran dari <a href="/web/tools/chrome-devtools/debug/console/console-reference#consoleerrorobject--object-">console.error()</a>.</td>
  </tr>
  <tr>
    <td>Warnings</td>
    <td>Hanya menampilkan keluaran dari <a href="/web/tools/chrome-devtools/debug/console/console-reference#consolewarnobject--object-">console.warn()</a>.</td>
  </tr>
  <tr>
    <td>Info</td>
    <td>Hanya menampilkan keluaran dari <a href="/web/tools/chrome-devtools/debug/console/console-reference#consoleinfoobject--object-">console.info()</a>.</td>
  </tr>
  <tr>
    <td>Logs</td>
    <td>Hanya menampilkan keluaran dari <a href="/web/tools/chrome-devtools/debug/console/console-reference#consolelogobject--object-">console.log()</a>.</td>
  </tr>
  <tr>
    <td>Debug</td>
    <td>Hanya menampilkan keluaran dari <a href="/web/tools/chrome-devtools/debug/console/console-reference#consoletimeendlabel">console.timeEnd()</a> dan <a href="/web/tools/chrome-devtools/debug/console/console-reference#consoledebugobject--object-">console.debug()</a>.</td>
  </tr>
  </tbody>
</table>

## Setelan tambahan

Buka setelan DevTools, masuk ke tab **General**, dan scroll ke bawah hingga
bagian **Console** untuk melihat setelan Console lebih lanjut.

![Setelan konsol](images/console-settings.png)

<table class="responsive">
  <thead>
     <tr>
      <th colspan="2">Setelan &amp; Keterangan</th>
    </tr>   
  </thead>
  <tbody>
  <tr>
    <td>Hide network messages</td>
    <td>Secara default, konsol melaporkan masalah jaringan. Mengaktifkannya akan menginstruksikan konsol agar tidak menampilkan log error ini. Misalnya, error seri 404 dan 500 tidak akan dimasukkan ke log.</td>
  </tr>
  <tr>
    <td>Log XMLHttpRequests</td>
    <td>Menentukan apakah konsol merekam log setiap XMLHttpRequest.</td>
  </tr>
  <tr>
    <td>Preserve log upon navigation</td>
    <td>Mempertahankan histori konsol selama penyegaran laman atau navigasi.</td>
  </tr>
  <tr>
    <td>Show timestamps</td>
    <td>Menyertakan stempel waktu ke setiap pesan konsol, menunjukkan kapan panggilan itu dibuat. Berguna untuk men-debug saat terjadi kejadian tertentu. Ini akan menonaktifkan penumpukan pesan.</td>
  </tr>
  <tr>
    <td>Enable custom formatters</td>
    <td>Mengontrol <a href="https://docs.google.com/document/d/1FTascZXT9cxfetuPRT2eXPQKXui4nWFivUnS_335T3U/preview">format</a> objek JavaScript.</td>
  </tr>
  </tbody>
</table>

## Masukan {: #feedback }

{% include "web/_shared/helpful.html" %}
