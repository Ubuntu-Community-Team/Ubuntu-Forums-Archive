---
title: "Installing tar.bz2 files?"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by michael91 on 2008-11-12
I've read through a few of the topics regarding the installation of these type of files, but I am still yet to understand fully how to install them. I've downloaded Firefox 3.0.3, and am unable to install it. Any help would be greatly appreciated.

---

### Post by Partyboi2 on 2008-11-12
If you are using Intrepid 8.10 or hardy you should already have it installed by default.

---

### Post by michael91 on 2008-11-12
I'm using Gutsy Gibbon 7.10.

---

### Post by Partyboi2 on 2008-11-12
Ok try this, open a terminal (Applications>Accessories>Terminal) change directory to where the download file is, so if its on your Desktop
```
cd ~/Desktop
```then extract
```
tar xjf firefox-*.tar.bz2
```then change into the new directory
```
cd firefox
```then run by typing
```
firefox
```
Then if its working create a launcher to run it. You may want to move the firefox folder to a better location before making the launcher for it.

---

### Post by michael91 on 2008-11-12
Unfortunately, I typed it character for character and it still didn't work.

michael@Computer:~$ cd ~/Desktop
michael@Computer:~/Desktop$ tar xjf firefox-3.0.3.tar.bz2
michael@Computer:~/Desktop$ cd firefox
michael@Computer:~/Desktop/firefox$ firefox


That's the exact code that I typed. The tar.bz2 file is on the Desktop, and it's called firefox-3.0.3.tar.bz2. After it all, it still came up with Version 2.0.0.17.

---

### Post by Partyboi2 on 2008-11-12
instead of typing firefox to start try typing
```
 ./firefox
```

---

### Post by michael91 on 2008-11-12
Nope, still same version.

---

### Post by bruceleelinux on 2008-11-12
> **michael91 said:**
> I've read through a few of the topics regarding the installation of these type of files, but I am still yet to understand fully how to install them. I've downloaded Firefox 3.0.3, and am unable to install it. Any help would be greatly appreciated.
hi.
copy file to a folder in home for example temp
open a terminal.
write this codes
```
cd /home/username/temp
tar zxvf filename.tar.bz2
cd filename
./configure
make install
make
```
this are simple and usefull.try it.good luck

---

### Post by michael91 on 2008-11-12
It might be of some help, but with the .tar.bz2 file came a folder with what appears to be the properties (i.e. folders, .ini files, .so files, etc.) inside. Would this have any effect in the installation?

---

### Post by Partyboi2 on 2008-11-12
Actually, looks like firefox 3 is avaliable from gusty backports. You can enable the backports repo by going into Software Sources (System>Admin>Software Sources) and I think its under the update tab. (not at linux box at the moment) then install it through synaptic.

---

### Post by michael91 on 2008-11-12
It's there and all (thanks for the help), but there's a break in xulrunner-19 which you need to run Firefox 3.0.

---

