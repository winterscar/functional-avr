# nonstd-functional

std::function for AVR. Implements a few of the std lib functions as helpers.


You can use it to pass callbacks to functions
``` cpp
#include "nonstd.h"

void foo(nonstd::function<void (int i)> bar){
    bar(3); // call bar (a function passed to foo) with a value of 3
}

void main(){
    int j = 3;
    foo([=] (int i) {Serial.println(i + j);}); // pass foo a lambda
}
```

`std::bind` is not implemented but you can replace it with a lambda. 
``` cpp
//This:
// ...
    using namespace std::placeholders;
    auto foo = std::bind(&SomeObject::some_func, this, _1, 3);
// ...

//Becomes this:
// ...
    auto foo = [=](int _1) {some_func(_1, 3);};
// ...
```