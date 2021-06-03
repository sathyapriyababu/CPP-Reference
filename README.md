# CPP CHEAT SHEET
 


- ✨CPP ✨
- Collections
-----------
![collection decision tree](https://i.stack.imgur.com/kQnCS.png)
![collection decision tree](https://i.stack.imgur.com/G70oT.png)
[more details](http://stackoverflow.com/questions/471432/in-which-scenario-do-i-use-a-particular-stl-container)

## cXX
* http://en.cppreference.com/w/cpp/language/converting_constructor
* http://en.cppreference.com/w/cpp/language/explicit
* http://en.cppreference.com/w/cpp/language/list_initialization
* http://en.cppreference.com/w/cpp/language/operator_member_access#Built-in_subscript_operator
* http://en.cppreference.com/w/cpp/language/override
* http://en.cppreference.com/w/cpp/language/eval_order
* http://en.cppreference.com/w/cpp/memory/shared_ptr
* http://en.cppreference.com/w/cpp/language/constexpr
* http://doc.qt.io/qt-5/qobject.html#Q_DISABLE_COPY

## Boost
* http://www.boost.org/doc/libs/1_59_0/libs/optional/doc/html/index.html

Vector Insert/Iterate Example
--------------
```
    std::vector<int> vect(10);

    int cnt = 0;
    for (std::vector<int>::iterator iter = vect.begin(); iter != vect.end(); iter++) {
        (*iter) = cnt++;
    }


    for (std::vector<int>::reverse_iterator iter =  vect.rbegin(); iter != vect.rend(); iter++) {
        cout << "iter: " << (*iter) << endl;
    }
```


Vector Sort Example
--------------
```
    std::vector<int> unsorted({32,71,12,45,26,80,53,33});
    std::sort(unsorted.begin(), unsorted.end());

    for ( int & value : unsorted) {
        cout << value << " ";
    }
    cout << endl;
```


Map Example
-----------
```
    std::map<int, char, std::greater<int>> mymap;

    for (int idx = 'a'; idx <= 'z'; idx++ ) {
        mymap[idx] = idx;
    }

    for (std::pair<int, char> keyvalue : mymap) {
        cout << "key: " << keyvalue.first << " value: " << keyvalue.second << endl;
    }
```

Move Example
-------------

```
class MyMove {

private:
    int x;
public:
    MyMove() : x(42) { }

    MyMove(MyMove &&o) : x(std::move(o.x)) {
        cout << "moved " << endl;
    }

    MyMove(MyMove &o) : x(std::move(o.x)) {
        cout << "copied" << endl;
    }

private:
    MyMove &operator=(const MyMove &) {
        cout << "assigned" << endl;
    }
};

// ------------

    MyMove a;
    MyMove b = std::move(a);
```

Template Example
---------------
```
template<class MyType>
MyType &myTemplateFunction(MyType e) {
    cout << "template func: type " << typeid(MyType).name() << " value " << e << endl;
}


template<class MyType>
class TClass {

public:
    void print(MyType e) {
        cout << "template class: type " << typeid(MyType).name() << " value " << e << endl;
    }
};
```

Stream Operator Overloading (global)
------------------------------------
```
std::ostream &operator<<(std::ostream &out, const FooBase &o) {
    out << "op overloading: <<" << o.getId() << ">>" << endl;
    return out;
}
```


File Read Example
-----------------
```
    std::fstream inFile("~/ClionProjects/recap-cpp/main.cpp");
    std::string line;
    while (std::getline(inFile, line)) {
        cout << "-------->" << line << "<---------" << endl;
    }
```

File Write Example 
-------------------
```
    std::ofstream outFile("~/ClionProjects/recap-cpp/tmp.txt", std::fstream::out | std::fstream::trunc);
    std::ostream& out = outFile;
    out << "foo test bla" << endl << std::flush;
    outFile.close();
```


