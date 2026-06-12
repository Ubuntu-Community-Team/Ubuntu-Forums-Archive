---
title: "ive never compiled anything ??? help please"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2010-01-03
i`d like to compile smillaenlarger
this is the text below ,that came with the program
if somebody could make it so i could cut and paste the commands
that i could do
i have smillaenlarger in a folder on my desktop




{To compile SmillaEnlarger, make sure that the Qt library and its developer tools are installed.

Within the SmillaEnlargerSrc directory first create the Makefile with qmake , then build the enlarger with make:

cd SmillaEnlargerSrc

qmake ImageEnlarger.pro

make}

---

### Post by SuperSonic4 on 2010-01-03
```
cd ~/Destop/smillaenlarger
```

```
sudo apt-get install qt-dev-tools
``` (or similar)

```
qmake
```

```
make
```

```
sudo make install
```

---

### Post by jimbean on 2010-01-03
this is what i get now


jim@jim-desktop:~/Desktop/SmillaEnlarger$ sudo apt-get install qt-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qt-dev
jim@jim-desktop:~/Desktop/SmillaEnlarger$

---

### Post by mutex023 on 2010-01-03
I think it is qt4-dev-tools, instead of qt-dev

---

### Post by SuperSonic4 on 2010-01-03
> **mutex023 said:**
> I think it is qt4-dev-tools, instead of qt-dev

Sounds plausible, it's been too long since I used kubuntu

---

### Post by jimbean on 2010-01-03
i am typing this for my own records
i had to retype the code from the last poster
anymore help would be nice

cd ~/Desktop/SmillaEnlarger
typed qmake
and this is what it said
The program 'qmake' can be found in the following packages:
 * qt3-dev-tools
 * qt4-qmake
Try: sudo apt-get install <selected package>
so i did and installed the 2 above
then i typed qmake in terminal and this is what i got
WARNING: Failure to find: EnlargeParam.h

---

### Post by jimbean on 2010-01-03
ok now i am install qt dev tools looks like a long time {132 megs}

---

### Post by SuperSonic4 on 2010-01-03
Yeah it would.

Now follow the instructions given by the program

```
cd ~/Destop/smillaenlarger
```

```
qmake
```

```
make
```

```
sudo make install
```

---

### Post by jimbean on 2010-01-03
qmake in terminal

i`m still getting
WARNING: Failure to find: EnlargeParam.h

---

### Post by jimbean on 2010-01-03
i searched the internet with yahoo
and i found some hits with 
WARNING: Failure to find: EnlargeParam.h
but they were all in foreign languages

---

### Post by mutex023 on 2010-01-03
If you are using ubuntu 9.04 there is a deb - 
[http://linux.softpedia.com/progDownload/SmillaEnlarger-Download-50762.html](http://linux.softpedia.com/progDownload/SmillaEnlarger-Download-50762.html)

Always better to install deb than compile.
Meanwhile I'll look into why its not compiling on 9.10.

---

### Post by jimbean on 2010-01-03
this is hilarious
i spent the whole morning on this
thankyou

---

