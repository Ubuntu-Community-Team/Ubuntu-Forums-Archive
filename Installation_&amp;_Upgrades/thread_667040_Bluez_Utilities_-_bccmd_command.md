---
title: "Bluez Utilities - bccmd command"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by breakaway8 on 2008-01-13
Hi, I read a tutorial online to change the product and vedor id of your bluetooth dongle. However, this requires the use of Bluez utilities. 

I downloaded the latest version of Bluez from [www.bluez.org](www.bluez.org) and extracted it. I then ran ./configure and then make and make install.

The problem is, all tools were installed except for dfutool and bccmd which are the most impt. Can anyone help?

I am on Ubuntu 7.10.

---

### Post by Partyboi2 on 2008-01-14
Couldn't you use the [I]bluez-utils packge from the repo's?
[/I]```
sudo apt-get install bluez-utils
```

---

### Post by breakaway8 on 2008-01-14
I did at first but bccmd wasn't included somehow in that package. Everytime I type bccmd at the terminal screen, i get a command not found msg.

---

### Post by breakaway8 on 2008-01-15
anyone have any ideas? pretty pls...

---

### Post by nx9 on 2008-02-03
run:
./configure --enable-all

should install everything you need
had me stumped for a bit too, had to read the configure script to figure it out
hope it helps =)

---

