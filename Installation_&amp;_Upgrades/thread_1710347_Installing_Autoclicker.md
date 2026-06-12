---
title: "Installing Autoclicker"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by hyudryu on 2011-03-19
I found a tool made for Ubuntu called Xautoclick. I downloaded it and it is called "xautoclick-0.30.tar.gz" The installation notes say "tallatBe sure you have the proper development packages for your distribution
installed (i.e. something like xserver-xorg-dev, gtk2-dev, et cetera).

After that, run:

./configure
make
sudo make install"
I have no clue what to do... I typed in "./configure" in the terminal and it says "bash: ./configure: No such file or directory?

Could someone perhaps teamviewer me and help me? Thanks.

---

### Post by kestrel1 on 2011-03-19
You need to make sure that you are in the directory of the programs download.
If you have un-tared to the Desktop folder & the folder the files are in is called xautoclick, do the following in the terminal:
```
cd Desktop/xautoclick
```
Then run:
```
./configure
```

---

### Post by hyudryu on 2011-03-19
Wow thank you so much.

---

### Post by kestrel1 on 2011-03-19
I assume that worked then?

---

### Post by Nanur on 2012-07-08
Hey, I tried doing the ./configure, but it said
```
None of the xautoclick applications can be build. 
You need to install the development packages of X11, 
GTK+ and/or QT. Check the documentation of your distribution 
for detail.
```

I'm not sure what to do.. any help would be appreciated!

---

### Post by wildmanne39 on 2012-07-08
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title.
Thanks

---

