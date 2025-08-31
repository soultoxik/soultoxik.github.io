---
title: Tuple 
tags: cpp, crazy
---

Когда хочется проехаться по содержимому тюпла с индексом
```cpp
    template<std::size_t I = 0, typename ...Ts>
    inline typename std::enable_if<I == sizeof...(Ts), void>::type
    something(std::tuple<Ts...>) { }

    template<std::size_t I = 0, typename ...Ts>
    inline typename std::enable_if<I < sizeof...(Ts), void>::type
    something(std::tuple<Ts...> ts) {
        doSomething(std::get<I>(ts));
        something<I + 1>(ts);
    }
```
[https://ideone.com/LVdMnx](https://ideone.com/LVdMnx)

---

When you need to iterate over the contents of a tuple with an index:

```cpp
    template<std::size_t I = 0, typename ...Ts>
    inline typename std::enable_if<I == sizeof...(Ts), void>::type
    something(std::tuple<Ts...>) { }

    template<std::size_t I = 0, typename ...Ts>
    inline typename std::enable_if<I < sizeof...(Ts), void>::type
    something(std::tuple<Ts...> ts) {
        doSomething(std::get<I>(ts));
        something<I + 1>(ts);
    }
```
[https://ideone.com/LVdMnx](https://ideone.com/LVdMnx)