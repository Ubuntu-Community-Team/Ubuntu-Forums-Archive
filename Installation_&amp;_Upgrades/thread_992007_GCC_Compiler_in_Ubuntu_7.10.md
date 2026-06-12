---
title: "GCC Compiler in Ubuntu 7.10"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by theemperor on 2008-11-24
Hi,

I am using Ubuntu 7.10.

How do i find out whether gcc is installed or not in my machine. Because when ever i try to compile some source code it says Checking for GCC and couldn't find GCC compiler.

I am not a techie.  Pls help me 

Thanks in advance

Bijoy

---

### Post by pennacook on 2008-11-24
Have a look at the output of 
```
dpkg -s gcc
```
If it reports back
```
Status: install ok installed
``` then it is installed.

---

### Post by linux_tech on 2008-11-24
To check the version you can use (in terminal) 
```
gcc -v 
```
If its not installed, you may install it by
```
 sudo apt-get install gcc
```

---

### Post by taurus on 2008-11-24
```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by theemperor on 2008-11-24
Hi,
Thanks a lot.
I found it installed in my machine. This thread posting was really helpful


Bijoy

---

