---
title: "trouble in compiling cpp programs using g++"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by hellofriendz on 2009-12-20
hey guys plz do help me... i'm in real trouble..... 
always getting the error : **No such file or directory**
 when i compile a simple prgm....

_PROGRAM _gedit abc.cpp#include<iostream.h>
main()
{
 cout<<"Hello\n";
}
[U]
COMPILATION STEP[/U]

g++ abc.cpp

_ERRORS_

abc.cpp:1:21: error: iostream.h: No such file or directory
abc.cpp: In function ‘int main()’:
abc.cpp:4: error: ‘cout’ was not declared in this scope
:(:confused:

---

### Post by cpplinux on 2009-12-20
1. include <iostream> instead of <iostream.h>
2. add _using namespace std;_ before the line of 'int main()'.

---

### Post by hellofriendz on 2009-12-20
OH MY... it worked...!:P:KS
thanks a lot buddy....
but why is it like that....???
i mean in college i didnt need to include namespace std....
is there a way to avoid that and proceed in the normal way???:-k

anyways thanks a lot my friend....=D>

---

