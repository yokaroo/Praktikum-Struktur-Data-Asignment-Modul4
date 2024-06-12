# <h1 align="center">Laporan Praktikum Modul Searching</h1>
<p align="center">Yoka Romadani</p>
<p align="center">2311110060</p>>
<p align="center">SD04-B</p>

## Dasar Teori
Pencarian (Searching) yaitu proses menemukan suatu nilai tertentu 
pada kumpulan data. Hasil pencarian adalah salah satu dari tiga keadaan 
ini: data ditemukan, data ditemukan lebih dari satu, atau data tidak 
ditemukan. Searching juga dapat dianggap sebagai proses pencarian suatu 
data di dalam sebuah array dengan cara mengecek satu persatu pada 
setiap index baris atau setiap index kolomnya dengan menggunakan teknik 
perulangan untuk melakukan pencarian data.
## Guided
## 1. Buatlah sebuah project dengan menggunakan sequential search sederhana untuk melakukan pencarian data.
```C++
#include <iostream> 
using namespace std; 

int main() { 
    const int n = 10; 
    int data[n] = {9, 4, 1, 7, 5, 12, 4, 13, 4, 10}; 
    int cari = 10; 
    bool ketemu = false; 
    int i; 
    
    // Algoritma Sequential Search 
    for (i = 0; i < n; i++) { 
        if(data[i] == cari) { 
            ketemu = true; 
            break; 
        } 
    } 
    
    cout << "\t Program Sequential Search Sederhana\n" << endl; 
    cout << "Data: {9, 4, 1, 7, 5, 12, 4, 13, 4, 10}" << endl; 
    
    if (ketemu) { 
        cout << "\nAngka " << cari << " ditemukan pada indeks ke-" << i << endl; 
    } else { 
        cout << cari << " tidak dapat ditemukan pada data." << endl; 
    } 
    
    return 0; 
}
 
```
### Output
![Screenshot 2024-06-12 223737](https://github.com/yokaroo/Praktikum-Struktur-Data-Asignment-Modul4/blob/main/Screenshot%202024-06-12%20223737.png)
## Iterpretasi
Program ini adalah implementasi dari algoritma Sequential Search yang bertujuan untuk mencari sebuah angka dalam array. Array `data` yang telah ditentukan diinisialisasi dengan sepuluh elemen bilangan bulat. Program kemudian mencari nilai `cari` di dalam array menggunakan algoritma Sequential Search, yang bekerja dengan cara memeriksa setiap elemen array satu per satu hingga menemukan nilai yang dicari atau sampai akhir array. Jika nilai `cari` ditemukan dalam array, program akan mencetak pesan yang menunjukkan bahwa angka tersebut ditemukan beserta indeksnya. Jika tidak, program akan mencetak pesan yang menyatakan bahwa angka tersebut tidak ditemukan dalam array. Setelah itu, program selesai dieksekusi. Semua pesan keluaran termasuk informasi tentang algoritma, data yang diuji, dan hasil pencarian, dicetak ke layar untuk memudahkan pemahaman.
## 2. Buatlah sebuah project untuk melakukan pencarian data dengan menggunakan Binary Search
```C++
#include <iostream> 
using namespace std; 
#include <conio.h> 
#include <iomanip> 
 
int data[7] = {1, 8, 2, 5, 4, 9, 7}; 
int cari; 
 
void selection_sort() 
{ 
      int temp, min, i, j; 
 
      for(i=0; i<7;i++) 
      { 
            min = i; 
            for(j = i+1; j<7; j++) 
            { 
                  if(data[j]<data[min]) 
                  { 
                        min=j; 
                  } 
            } 
            temp = data[i]; 
            data[i]  = data[min]; 
            data[min] = temp; 
      } 
} 
 
void binarysearch() 
{ 
      //searching 
      int awal, akhir, tengah, b_flag = 0; 
      awal = 0; 
      akhir = 7; 
      while (b_flag == 0 && awal<=akhir) 
      { 
            tengah = (awal + akhir)/2; 
            if(data[tengah] == cari)
	 { 
                  b_flag = 1; 
                  break; 
            } 
            else if(data[tengah]<cari) 
                  awal = tengah + 1; 
            else 
                  akhir = tengah -1; 
      } 
 
        if(b_flag == 1) 
            cout<<"\n Data ditemukan pada index ke
"<<tengah<<endl; 
      else 
            cout<<"\n Data tidak ditemukan\n"; 
} 
 
int main() 
{ 
      cout<<"\t   BINARY SEARCH "<<endl; 
      cout<<"\n Data           : "; 
      //tampilkan data awal 
      for(int x = 0; x<7; x++) 
            cout<<setw(3)<<data[x]; 
      cout<<endl; 
 
      cout<<"\n Masukkan data yang ingin Anda cari : "; 
      cin>>cari; 
      cout<<"\n Data diurutkan : "; 
      //urutkan data dengan selection sort 
      selection_sort(); 
      //tampilkan data setelah diurutkan 
      for(int x = 0; x<7;x++) 
            cout<<setw(3)<<data[x]; 
 
      cout<<endl; 
 
        binarysearch(); 
 
      _getche(); 
      return EXIT_SUCCESS; 
 
 }
```
## Output
![Screenshot 2024-06-12 224443](https://github.com/yokaroo/Praktikum-Struktur-Data-Asignment-Modul4/blob/main/Screenshot%202024-06-12%20224443.png)
## Interpretasi Code
Program ini menggunakan algoritma Binary Search untuk mencari angka dalam array yang telah diurutkan menggunakan algoritma Selection Sort. Setelah pengguna memasukkan angka yang dicari, array diurutkan dengan Selection Sort. Kemudian, program melakukan pencarian menggunakan Binary Search. Jika angka ditemukan dalam array, program mencetak indeksnya. Jika tidak, program memberi tahu bahwa angka tidak ditemukan. Seluruh output, termasuk data awal, data setelah diurutkan, dan hasil pencarian, dicetak ke layar. Program berakhir setelah pengguna memberikan input.
### UnGuided
## 1. Buatlah sebuah program untuk mencari sebuah huruf pada sebuah kalimat yang sudah di input dengan menggunakan Binary Search! 
```C++
#include <iostream>
#include <string>
#include <algorithm>

using namespace std;

// Fungsi untuk mengubah huruf kecil menjadi huruf besar
char toUpperCase(char ch) {
    if (ch >= 'a' && ch <= 'z') {
        return ch - 'a' + 'A';
    }
    return ch;
}

// Fungsi untuk mengurutkan string secara ascending
void sortString(string &str) {
    sort(str.begin(), str.end());
}

// Fungsi Binary Search untuk mencari huruf dalam string
bool binarySearch(const string &str, char target) {
    int left = 0;
    int right = str.length() - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        // Ubah huruf kecil menjadi huruf besar untuk pencarian
        char current = toUpperCase(str[mid]);

        if (current == target) {
            return true;
        } else if (current < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return false;
}

int main() {
    string sentence;
    cout << "Masukkan kalimat: ";
    getline(cin, sentence);

    // Urutkan kalimat
    sortString(sentence);

    char target;
    cout << "Masukkan huruf yang ingin dicari: ";
    cin >> target;

    // Ubah huruf kecil menjadi huruf besar untuk pencarian
    target = toUpperCase(target);

    // Cari huruf menggunakan Binary Search
    if (binarySearch(sentence, target)) {
        cout << "Huruf " << target << " ditemukan dalam kalimat." << endl;
    } else {
        cout << "Huruf " << target << " tidak ditemukan dalam kalimat." << endl;
    }

    return 0;
}

```
### Output
![Screenshot 2024-06-12 225137](https://github.com/yokaroo/Praktikum-Struktur-Data-Asignment-Modul4/blob/main/Screenshot%202024-06-12%20225137.png)

## 2. Buatlah sebuah program yang dapat menghitung banyaknya huruf vocal dalam sebuah kalimat! 
```C++
#include <iostream>
#include <string>
#include <cctype> // Untuk fungsi isalpha dan tolower

using namespace std;

// Fungsi untuk menghitung banyaknya huruf vokal dalam sebuah kalimat
int countVowels(const string &sentence) {
    int count = 0;
    for (char ch : sentence) {
        char lowerCh = tolower(ch); // Ubah huruf menjadi huruf kecil
        if (lowerCh == 'a' || lowerCh == 'e' || lowerCh == 'i' || lowerCh == 'o' || lowerCh == 'u') {
            count++;
        }
    }
    return count;
}

int main() {
    string sentence;
    cout << "Masukkan sebuah kalimat: ";
    getline(cin, sentence);

    int vowelsCount = countVowels(sentence);

    cout << "Jumlah huruf vokal dalam kalimat adalah: " << vowelsCount << endl;

    return 0;
}

```

## Output
![Screenshot 2024-06-12 225531](https://github.com/yokaroo/Praktikum-Struktur-Data-Asignment-Modul4/blob/main/Screenshot%202024-06-12%20225531.png)

### 3. Diketahui data = 9, 4, 1, 4, 7, 10, 5, 4, 12, 4. Hitunglah berapa banyak angka 4 dengan menggunakan algoritma Sequential Search!
```C++
#include <iostream>

using namespace std;

// Fungsi untuk menghitung berapa kali angka 4 muncul dalam data menggunakan Sequential Search
int countFour(int arr[], int length) {
    int count = 0;
    for (int i = 0; i < length; ++i) {
        if (arr[i] == 4) {
            count++;
        }
    }
    return count;
}

int main() {
    int data[] = {9, 4, 1, 4, 7, 10, 5, 4, 12, 4};
    int length = sizeof(data) / sizeof(data[0]);

    int countOfFour = countFour(data, length);

    cout << "Jumlah angka 4 dalam data adalah: " << countOfFour << endl;

    return 0;
}

```
## output
![Screenshot 2024-06-12 225837](https://github.com/yokaroo/Praktikum-Struktur-Data-Asignment-Modul4/blob/main/Screenshot%202024-06-12%20225837.png)

### Kesimpulan 
Dalam pencarian data, terdapat dua metode utama: Sequential Search dan Binary Search. Sequential Search digunakan untuk data yang tidak terurut, dengan konsep membandingkan setiap elemen satu per satu dari awal hingga akhir array. Binary Search, di sisi lain, digunakan untuk data yang telah terurut, dengan konsep membagi data menjadi dua bagian pada setiap tahap pencarian. Dalam Binary Search, elemen tengah diambil sebagai acuan untuk membagi data, dan pencarian dilanjutkan berdasarkan relasi antara nilai yang dicari dengan nilai tengah tersebut. Jika nilai yang dicari lebih besar dari nilai tengah, pencarian dilanjutkan ke bagian kanan; jika lebih kecil, ke bagian kiri. Jika nilai yang dicari sama dengan nilai tengah, pencarian selesai. Dengan Binary Search, proses pencarian dapat lebih efisien dibandingkan dengan Sequential Search, terutama untuk data yang besar dan telah terurut.
