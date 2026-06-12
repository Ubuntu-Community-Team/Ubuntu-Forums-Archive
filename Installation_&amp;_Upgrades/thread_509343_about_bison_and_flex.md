---
title: "about bison and flex"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by adnk on 2007-07-25
Hello all there,

i have attempt  to install a software using flex and bison programs during the installation, but I always encounter an problem, and take an error message as given the following: 

/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_list.h:169: note: candidates are: bool std::_List_iterator<_Tp>::operator==(const std::_List_iterator<_Tp>&) const [with _Tp = Element]
parser.y: In function ‘int yyparse()’:
parser.y:342: error: no match for ‘operator==’ in ‘it == 0’
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_list.h:169: note: candidates are: bool std::_List_iterator<_Tp>::operator==(const std::_List_iterator<_Tp>&) const [with _Tp = Element]
parser.y:922: error: conversion from ‘int’ to non-scalar type ‘std::_List_iterator<double>’ requested
make[1]: *** [parser.tab.o] Error 1
make: *** [gmad] Error 2

 What can be the reason of the problem? 

if you can help me to solve this problem, i wil be happy very much.

yours sincerely,
adnan.

(Note: I use Ubuntu 7.04 version on my computer and my compiler is gcc 4.1.)

---

