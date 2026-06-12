---
title: "C++ Compiler in Ubuntu 10.04 LTS"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by rshinde70 on 2011-01-27
Hi Friends..
I'm using Ubuntu 10.03LTS. Now days I've started learning C++.
But unfortunately, Only c codes can be compiled on This version of ubuntu while I'm not able to compile/run C++ codes.
is here anybody knows the right solution???

---

### Post by cgroza on 2011-01-27
You need the G++ compiler. You can get it by:

```
sudo apt-get install build-essential
```

---

### Post by rshinde70 on 2011-01-27
> **cgroza said:**
> You need the G++ compiler. You can get it by:

```
sudo apt-get install build-essential
```

It's already installed, :(

---

### Post by cgroza on 2011-01-27
How about:

```
sudo apt-get install g++
```

You run it by:

```
g++ filename
```

---

### Post by rshinde70 on 2011-01-27
> **cgroza said:**
> How about:

```
sudo apt-get install g++
```You run it by:

```
g++ filename
```

The same problem continues...
What gcc shows if i tries to comile like..
r```
ohit@rohit-desktop:~$ sudo apt-get install g++
[sudo] password for rohit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
g++ set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 234 not upgraded.
rohit@rohit-desktop:~$ vi trial.cpp
rohit@rohit-desktop:~$ g++ trial.cpp
trial.cpp:1:21: error: iostream.h: No such file or directory
trial.cpp: In function ‘int main()’:
trial.cpp:4: error: ‘cout’ was not declared in this scope
rohit@rohit-desktop:~$ 
```

---

### Post by cgroza on 2011-01-27
Ok, from now it is just compile errors.

The include line should be:
```

#include <iostream>
``` // standard library header files do not have .h extension.

And with the cout error, you could put a:

```
using namespace std;
```

or std:: right before the cout statement.

---

### Post by rshinde70 on 2011-01-27
> **cgroza said:**
> Ok, from now it is just compile errors.

The include line should be:
```

#include <iostream>
``` // standard library header files do not have .h extension.

And with the cout error, you could put a:

```
using namespace std;
```or std:: right before the cout statement.

Thanks Brother. I understood about that header file But i didn't understand about 'cout'
I really didn't understand. Could you explain it please?

---

### Post by cgroza on 2011-01-27
It is because the cout function is present in the std namespace. The "cout::" or using namespace std introduces this new name in the current name space so you can use it.

Read a little bit about namespaces in C++ and you will understand. It basically groups things that have something in common.

EDIT: std:: does not introduce new names in the current namespace, but only accesses it from there.

---

