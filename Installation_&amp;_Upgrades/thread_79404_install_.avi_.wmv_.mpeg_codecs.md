---
title: "install .avi .wmv .mpeg codecs"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by myst on 2005-10-20
hi.
i've installed the latest release of kubuntu on my laptop (acer aspire 1694).
mp3 playback works fine already, and mpeg too, but i can't play .avi and .wmv files. kaffeine is always saying, that i have to install the right plugin. If i play .mpeg or mpg files the video output works fine, but i have no sound. :(
does anyone know which packages i have to install to fix these problems?
or is there any other solvation for this probelm?
geetings
myst

---

### Post by renzokuken on 2005-10-20
u need to get a hold of the "win32" codecs......

they used to be on mplayerhq.hu but that disapperared some days ago......

there is prolly a deb in the ubuntu repos for this, its usually called libavcodec so just do a 

sudo apt-get install libavcodec

---

### Post by tictoc on 2005-10-20
To get w32codecs you can add:
```
deb ftp://ftp.nerim.net/debian-marillat/ sid main
```
to /etc/apt/sources.list
```
sudo apt-get install w32codecs
``` 
Immediately go back and comment out (#) that line from sources.list as it can break your system to leave it active.

---

### Post by myst on 2005-10-20
Hi,
i installed the codecs. but my player still says there is no plugin to play avi files. :(
is there any other way to get it worked, or have i to configure the installed codec anywhere?
greetz
myst

---

### Post by renzokuken on 2005-10-20
check the configuration settings of your media player and see if u can find out where it is looking for the win32 codecs

most players look for them in /usr/lib/win32 so make sure ur player is pointed to there, or wherever the apt-get installed them to

---

### Post by myst on 2005-10-20
hey!
thank you very much. now it's working correctly!!
in kaffeine the path was configured right to /usr/lib/win32 but i had to hit the apply button with the same options again to "really" apply settings. i don't know why this, but is works at all!!! :)))))))
greetz myst

---

### Post by renzokuken on 2005-10-20
no trubs at all......

you are officially the first person ive ever helped on a linux problem.....i only know cos im a n00b so went through this myself recently

---

