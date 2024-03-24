# TP2DPBO2024C1
## Janji
Saya Salma Ghaida dengan NIM 2207186 mengerjakan Tugas Praktikum 2 dalam mata kuliah Desain Pemrograman Berbasis Objek untuk keberkahanNya maka saya tidak melakukan kecurangan seperti yang telah dispesifikasikan. Aamiin...

## Penjelasan Kelas
### Kelas Mahasiswa
**Atribut :**
1. nim (TextField)
2. nama (TextField)
3. jenisKelamin (ComboBox)
4. kelas (ComboBox)

Kelas Mahasiswa memiliki konstruktor untuk membuat objek Mahasiswa baru dengan memberikan nilai untuk setiap atributnya. Selain itu, terdapat metode-metode setter (setNim, setNama, setJenisKelamin, setKelas) yang digunakan untuk mengatur nilai atribut, dan metode-metode getter (getNim, getNama, getJenisKelamin, getKelas) yang digunakan untuk mengambil nilai atribut.

### Kelas Menu
1. **Struktur Kelas `Menu`**:
   - Kelas `Menu` merupakan kelas utama yang mengextends `JFrame`, yang digunakan untuk membuat jendela aplikasi.
   - Di dalamnya terdapat komponen-komponen antarmuka pengguna seperti `JTextField`, `JComboBox`, `JTable`, dan `JButton` yang digunakan untuk memasukkan data mahasiswa, menampilkan data dalam tabel, dan mengatur interaksi dengan pengguna.

2. **Metode `main`**:
   - Metode `main` digunakan untuk membuat instance dari kelas `Menu` dan menampilkan jendela aplikasi.

3. **Metode `setTable`**:
   - Metode ini digunakan untuk mengisi tabel dengan data mahasiswa yang diambil dari database.
   - Menggunakan objek `DefaultTableModel` untuk menyimpan data yang akan ditampilkan dalam tabel.

4. **Metode `insertData`**:
   - Metode ini dipanggil ketika pengguna ingin menambahkan data mahasiswa baru.
   - Mengambil nilai dari komponen-komponen antarmuka pengguna (textfield dan combobox) untuk memasukkan data ke dalam database.
   - Setelah data dimasukkan, tabel diperbarui dengan memanggil metode `setTable` dan formulir dibersihkan.

5. **Metode `updateData`**:
   - Metode ini dipanggil ketika pengguna ingin memperbarui data mahasiswa yang telah ada.
   - Mengambil nilai dari komponen antarmuka pengguna untuk memperbarui data dalam database.
   - Setelah data diperbarui, tabel diperbarui dan formulir dibersihkan.

6. **Metode `deleteData`**:
   - Metode ini dipanggil ketika pengguna ingin menghapus data mahasiswa.
   - Menampilkan dialog konfirmasi sebelum menghapus data.
   - Jika pengguna mengonfirmasi penghapusan, data dihapus dari database, tabel diperbarui, dan formulir dibersihkan.

7. **Metode `clearForm`**:
   - Metode ini digunakan untuk membersihkan semua komponen antarmuka pengguna setelah operasi penambahan atau pengubahan data.
   - Juga mengatur kembali nilai `selectedIndex` dan mengubah teks tombol "Update" menjadi "Add".

8. **Event Listeners**:
   - Terdapat beberapa event listeners yang menangani interaksi pengguna, seperti saat tombol "Add/Update", "Delete", atau "Cancel" ditekan, serta saat salah satu baris tabel diklik. Event listeners ini memanggil metode yang sesuai untuk melakukan operasi yang diinginkan.

### Kelas Database
Kelas `Database` merupakan kelas yang bertanggung jawab untuk mengelola koneksi dan eksekusi query ke database MySQL.

1. **Koneksi ke Database**:
   - Di dalam konstruktor `Database()`, koneksi ke database MySQL dibuat menggunakan `DriverManager.getConnection()`.
   - URL JDBC,`"jdbc:mysql://localhost:3306/db_mahasiswa"`, di mana `db_mahasiswa` adalah nama database, `root` adalah nama pengguna, dan string kosong `""` adalah kata sandi.

2. **Statement**:
   - Objek `Statement` digunakan untuk membuat dan mengeksekusi pernyataan SQL.
   - Dalam konstruktor, objek `Statement` dibuat dengan menggunakan metode `connection.createStatement()`.

3. **Metode `selectQuery`**:
   - Metode ini digunakan untuk menjalankan pernyataan `SELECT` ke database.
   - Eksekusi query dilakukan dengan menggunakan metode `statement.executeQuery(sql)`.
   - Hasil dari query diperoleh dengan memanggil `statement.getResultSet()` dan dikembalikan sebagai objek `ResultSet`.

4. **Metode `insertUpdateDeleteQuery`**:
   - Metode ini digunakan untuk menjalankan pernyataan `INSERT`, `UPDATE`, atau `DELETE` ke database.
   - Eksekusi query dilakukan dengan menggunakan metode `statement.executeUpdate(sql)`.
   - Metode ini mengembalikan jumlah baris yang terpengaruh oleh operasi query.

5. **Penanganan Pengecualian**:
   - Terdapat penanganan pengecualian menggunakan blok `try-catch` untuk menangani kemungkinan kesalahan dalam eksekusi query atau koneksi database.
   - Jika terjadi kesalahan, pengecualian akan dilempar menggunakan `throw new RuntimeException(e)`.

6. **Getter `getStatement`**:
   - Metode `getStatement()` digunakan untuk mendapatkan objek `Statement` yang telah dibuat, yang dapat berguna dalam situasi di mana Anda perlu mengakses objek `Statement` secara langsung.
