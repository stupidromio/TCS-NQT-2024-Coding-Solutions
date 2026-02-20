# 📘 TCS NQT / DCS -- C++ Input Handling Guide

This guide explains all common input formats asked in **TCS NQT /
Digital Coding Section (DCS)** and how to safely handle them in C++.

Understanding input format is more important than logic in TCS exams.

------------------------------------------------------------------------

# ✅ 1️⃣ Space-Separated Input (Size Not Given)

### 🎯 Example Input:

    1 2 3 4 5

### 💻 Code:

``` cpp
vector<int> input_space_separated() {
    vector<int> arr;
    string input;
    getline(cin, input);
    stringstream ss(input);
    int num;
    while (ss >> num) {
        arr.push_back(num);
    }
    return arr;
}
```

### ✔ Why It Works:

-   `>>` automatically skips spaces
-   Reads until no numbers remain

------------------------------------------------------------------------

# ✅ 2️⃣ Comma-Separated Input

### 🎯 Example Input:

    1,2,3,4,5

### 💻 Safe Code:

``` cpp
vector<int> input_comma_separated() {
    vector<int> arr;
    string input;
    getline(cin, input);
    stringstream ss(input);
    string token;

    while (getline(ss, token, ',')) {
        arr.push_back(stoi(token));
    }

    return arr;
}
```

### ✔ Why It Works:

-   Splits input using comma delimiter
-   Avoids stream errors

------------------------------------------------------------------------

# ✅ 3️⃣ Bracket + Comma Format (LeetCode Style)

### 🎯 Example Input:

    [1,2,3,4,5]

### 💻 TCS Safe Method:

``` cpp
vector<int> tcs_safe_array_input() {
    vector<int> arr;
    string input;
    getline(cin, input);

    for (int i = 0; i < input.length(); i++) {
        if (input[i] == '[' || input[i] == ']' || input[i] == ',') {
            input[i] = ' ';
        }
    }

    stringstream ss(input);
    int num;
    while (ss >> num) {
        arr.push_back(num);
    }

    return arr;
}
```

### ✔ Why This Is Best:

-   Converts special characters into spaces
-   Reuses standard space-separated logic

------------------------------------------------------------------------

# ✅ 4️⃣ When Size is Given

### 🎯 Example Input:

    5
    1 2 3 4 5

### 💻 Code:

``` cpp
int n;
cin >> n;

vector<int> arr(n);

for (int i = 0; i < n; i++) {
    cin >> arr[i];
}
```

⚠ If mixing `cin` and `getline`, always use:

``` cpp
cin.ignore();
```

------------------------------------------------------------------------

# 🚀 TCS Pro Tips

## 🔹 Use One-Line Include

``` cpp
#include <bits/stdc++.h>
using namespace std;
```

## 🔹 Match Output Exactly

-   No extra spaces
-   No extra text
-   Follow sample output format strictly

## 🔹 Identify Format Before Coding

-   Is size given?
-   Are commas present?
-   Are brackets present?
-   Is text required in output?

Spend 1 minute analyzing before coding.

------------------------------------------------------------------------

# 🏁 Final Advice

In TCS NQT/DCS: - Logic is Easy to Medium - Input format handling is the
real challenge - Output formatting must match exactly

Master input handling → Clear coding round confidently.
