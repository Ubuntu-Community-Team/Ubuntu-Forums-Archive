---
title: "help to install tk8.5.10-src.tar.gz"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by RGNOME on 2011-07-13
Hello, i am new in LINUX (and loving it) i would like to upgrade my tk8.4 to 8.5 to run a program. i have upgraded TCL (to 8.5) but ketp tk as 8.4.
now after downloading tk8.5targz and untaring it, waht do i do to install?
cheers
R.

---

### Post by realzippy on 2011-07-13
Compiling is not for beginners....suggest you install tk8.5 from the software center or,faster,open terminal and paste in:

```
sudo apt-get install tk8.5
```


...and welcome to UF!

---

### Post by raja.genupula on 2011-07-13
untar your software
cd to that folder
run this 

```
./configure
```
```
make
```
```
sudo make install
```

---

### Post by realzippy on 2011-07-13
Op had to navigate to the "Unix" folder inside the untared tk8.5 folder
to compile it for Unix/Linux ...there  is also a README which shows how to compile.

---

### Post by RGNOME on 2011-07-13
Thank you guys for the prompt response!

The sudo apt-get worked.

i tried previously to my original posting ./configure (inside the tk folder) with negative results

Cheers

R.

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

