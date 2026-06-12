---
title: "installing progs in wine"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by cnc95fan on 2007-03-11
this question has probably been asked many times, but how do you install programs in wine? i have created the c drive and the d drive and all the files needed are there , ive tried using winecfg and clicking add application, but nothing happenes, is there anything else i have to do, and im installing from a cd rom

---

### Post by aidanr on 2007-03-11
by opening a terminal, cd (change directory) to the cdrom, and typing wine program_name.exe

eg.

cd /media/cdrom
wine setup.exe

---

### Post by cnc95fan on 2007-03-11
kk thnx

---

### Post by cnc95fan on 2007-03-11
it comes up with errors saying warning: 3d driver not suporting somthing,...:confused:

---

### Post by aidanr on 2007-03-11
not all programs are going to work or work well, do a search for the app you want to run [here]("http://appdb.winehq.org/") to see if anyone has gotten it working

---

### Post by zvacet on 2007-03-11
Type 
```
winefile
```
and in C drive look for your app and double click on it.

---

### Post by cnc95fan on 2007-03-16
no, when i try to install the rpogram (/media/cdrom0) the termanal says graphics card claims to not supports 3d a8 or somthing like that anyway, is there somthing im doing wrong? i go to the wine cfg and click add application and set it for win95 because command and conquer requires windows 95, and then i go into the terminal and type cd /media/cdrom0 and then type wine setup.exe

---

### Post by zvacet on 2007-03-17
When you click add apps you must see window which ask you where from(it is dropdown menu).Select .wine>dosdevices>z(in my case is z,maybe something else is for you) and you will see folders(cdrom and media).pick one of them(one must be right one) and install.Other way is to copy exe from Cd to your home directory and after that put it in .wine C drive program files folder(hidden in home directory).
```
winefile
```
C drive>program files>your_exe>double click

---

