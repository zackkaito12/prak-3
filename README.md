#include <iostream>
using namespace std;

void fibonacci(int n, long long& result) {
    if (n <= 2) {
        result = 1;
    } else {
        long long a = 1, b = 1;
        for (int i = 3; i <= n; ++i) {
            long long temp = a + b;
            a = b;
            b = temp;
        }
        result = b;
    }
}

void fibonacciSum(int n, long long& sum) {
    sum = 0;
    for (int i = 1; i <= n; ++i) {
        long long fib;
        fibonacci(i, fib);
        sum += fib;
    }
}

int main() {
    char z;
    do {
        int n;
        cout << "Masukkan nilai n (3 <= n <= 100 atau 109 <= n <= 199): ";
        cin >> n;
        if ((n >= 3 && n <= 100) || (n >= 109 && n <= 199)) {
            long long fibN, sum;
            fibonacci(n, fibN);
            cout << "Bilangan Fibonacci ke-" << n << ": " << fibN << endl;
            fibonacciSum(n, sum);
            cout << "Jumlah deret Fibonacci hingga ke-" << n << ": " << sum << endl;
        } else {
            cout << "Nilai n tidak memenuhi ketentuan." << endl;
        }
        cout << "Apakah Anda ingin mencoba lagi? (y/n): ";
        cin >> z;
    } while (z == 'y' || z == 'Y');
    return 0;
}
