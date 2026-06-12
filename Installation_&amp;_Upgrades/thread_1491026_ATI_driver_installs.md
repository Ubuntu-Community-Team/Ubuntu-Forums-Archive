---
title: "ATI driver installs"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by TheRacerX on 2010-05-23
Hello im new to Ubuntu...well Linux in general Ive always used windows but my friend suggested i try it out anyways im trying to install the most recent catalyst control center and driver for my ATI video card.

It's a .run file but my computer keeps giving me this weird coding error in gedit,
how to do fix it so i can install the driver so i can use all the graphical features of Ubuntu

my computer is a laptop an Acer Extensa 4420
AMD Athlon X2 Dual Core TK-57 at 1.9GHz
3GB DDR2 single channel RAM at 315MHz
and an ATI Radeon Xpress 1250 embedded video card

---

### Post by dino99 on 2010-05-23
dont use the ".run" file from nvidia, ubuntu already have the fine tuned drivers available with "synaptic"

install xserver-xorg-video-radeon, then after reboot, check hardware driver (system admin) to see if the driver is well activated.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Mark Phelps on 2010-05-23
> **TheRacerX said:**
> Hello im new to Ubuntu...well Linux in general Ive always used windows but my friend suggested i try it out anyways im trying to install the most recent catalyst control center and driver for my ATI video card.

Don't -- it won't work with current Ubuntu versions and your video card.  Only the open source drivers will work -- and those are installed by default.

---

### Post by TheRacerX on 2010-05-23
except for the fact those drivers arent working either my video card is not compatible or something is wrong with it.

---

### Post by TheRacerX on 2010-05-23
also for some reason no matter what resolution or refresh frequency i wet my display too its still distorted in some way, either the screen wobbles up and down or it gets there weird fuzzy lines on the screen.  Ive tried every resolution and frequency combination known to man. nothing fixes it

---

### Post by quadproc on 2010-05-23
> **TheRacerX said:**
> Hello im new to Ubuntu...well Linux in general Ive always used windows but my friend suggested i try it out anyways im trying to install the most recent catalyst control center and driver for my ATI video card.

It's a .run file but my computer keeps giving me this weird coding error in gedit,
how to do fix it so i can install the driver so i can use all the graphical features of Ubuntu

Just a note of explanation about the gedit error that you see on the .run file: that file contains an initial unpacking script to decompress the remainder of the file.  For that reason, most of the file is binary and gedit cannot make sense of it so gedit complains.  If you would like to see the script then you can
```
head  -n 310 <the_.run_file_name>
```You might need to adjust the 310 a bit.
> 
my computer is a laptop an Acer Extensa 4420
AMD Athlon X2 Dual Core TK-57 at 1.9GHz
3GB DDR2 single channel RAM at 315MHz
and an ATI Radeon Xpress 1250 embedded video cardI did not look up the age of your video hardware and you did not say which Ubuntu release that you are using so I will say that there might be a compatibility problem between the .run file and your Ubuntu version.  Ask your system
```
sh <the_.run_file_name> --listpkg
```and see if the two are compatible.

quadproc

---

### Post by TheRacerX on 2010-05-23
im running Ubuntu 9.10 32bit in a dual boot setup with Windows 7 Professional

---

### Post by TheRacerX on 2010-05-24
> **quadproc said:**
> Just a note of explanation about the gedit error that you see on the .run file: that file contains an initial unpacking script to decompress the remainder of the file.  For that reason, most of the file is binary and gedit cannot make sense of it so gedit complains.  If you would like to see the script then you can
```
head  -n 310 <the_.run_file_name>
```You might need to adjust the 310 a bit.
I did not look up the age of your video hardware and you did not say which Ubuntu release that you are using so I will say that there might be a compatibility problem between the .run file and your Ubuntu version.  Ask your system
```
sh <the_.run_file_name> --listpkg
```and see if the two are compatible.

quadproc

i tried that it keeps giving me cannot find directory everytime i type that into Terminal

---

### Post by quadproc on 2010-05-24
> **TheRacerX said:**
> i tried that it keeps giving me cannot find directory everytime i type that into Terminal
It sounds like you need to cd to the directory where the .run file is located.  For example, if the .run file is located on your desktop, you could input
```
cd Desktop
sh <the_ati_.run_file_name> --listpkg
```Of course, substitute the actual directory instead of Desktop, and substitute the actual run file name where I used <the_ati_.run_file_name>.

quadproc

---

### Post by TheRacerX on 2010-05-24
do i put the brackets before and after then file name as well?  Sorry i was never good at computer programming and coding lol im a computer hardware geek, my software knowledge is pretty basic

---

### Post by TheRacerX on 2010-05-28
also i found out my video card has a linux proprietary catalyst control center suite on the ATI website and that my video card came out in feb of 2007

---

