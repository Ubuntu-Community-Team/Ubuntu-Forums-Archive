---
title: "installing ndiswrapper - missing kernel header files"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by drifter129 on 2008-07-18
Hi - after installing hardy 8.05 i am having alot of problems getting my wireless card to work. it is a wl-138g v2 (broadcom 4318). 

I have tried to follow instructions to install ndiswrapper manually, which is fine, but when i try to install by using the "make install" command, i get a message saying various files (eg stdlib.h) are missing. It seems that i don't have any of the kernel header files installed. (i am very new to linux - its a miracle i managed to get this far!)

After looking on the net, i am struggling to find instructions on how to MANUALLY install these files (as i don't have network connectivity yet). I have downloaded a .deb file from a site which i think is what i'm looking for, and have copied over to my linux pc by means of a usb stick, but don't know how to install it!! 

Can anyone help?

---

### Post by PmDematagoda on 2008-07-18
What is the name of the file you got? Also, from where did you obtain it?

---

### Post by drifter129 on 2008-07-18
here's the exact file i downloaded:

[http://packages.ubuntu.com/hardy/amd64/linux-headers-lum-2.6.24-18-rt/download](http://packages.ubuntu.com/hardy/amd64/linux-headers-lum-2.6.24-18-rt/download)

---

### Post by PmDematagoda on 2008-07-18
Are you running the Real Time kernel?

---

### Post by drifter129 on 2008-07-18
i'm sorry, but i don't know what you mean by "real time kernel". how would i tell?

---

### Post by jimv on 2008-07-18
Why are you installing manually?  There is a package that you can install for hardy.

sudo apt-get install ndiswrapper-utils-1.9

And to see what kernel version you're running, type

uname -r

---

### Post by drifter129 on 2008-07-20
i can't use the sudo apt-get install as i do not have a working internet connection yet!!!

the version i'm using is 2.6.24-16-generic

---

### Post by PmDematagoda on 2008-07-20
drifter129, the best way to try and find what you need would be using [Ubuntu Packages]("http://packages.ubuntu.com/"), you can just search for what you need, download them and any other required dependencies and then just install it normally(offline):).

---

### Post by Partyboi2 on 2008-07-20
I think you will find the ndiswrapper-utils-1.9 package on the ubuntu hardy live cd

---

### Post by drifter129 on 2008-07-20
ok thanks. need to get this problem sorted out first then i think----> [http://ubuntuforums.org/showthread.php?t=863424](http://ubuntuforums.org/showthread.php?t=863424)

---

