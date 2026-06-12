---
title: "Upgrade Trouble - Need Help!"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by nomadik on 2005-10-15
hi there,

i upgraded from Hoary to Breezer yesterday via apt-get and
followed all the instructions -
some packages were not installing correctly due to dependency problems:
gnome-terminal-data
postfix
lsb-core
mailx
mutt
mysqlserver

tried to redo the apt-get upgrade - no luck 
tried removing by hand + reinstalling - again didn't work...

most importantly i can't get my xserver to work at all -
tried everything i could find in the forums - no luck 

i am on a Sony Laptop with ATI Radeon Mobility 9200 
worked perfectly under hoary - 
i tried to reconfigure the xorg.conf with AtI drivers, fglrx, vesa...
i also tried the fglrxconfig program  (although my card should be supported) - 
also if i try startx or gdm - it can't find the command

please give me a hint !! - i really like ubuntu and find it very weird that 
a graphics card that was detected without problems in hoary doesn't work anymore ...

---

### Post by az on 2005-10-15
From a terminal you can try

sudo apt-get -f install

---

### Post by nomadik on 2005-10-15
thanks for the fast reply - but i tried that ...
my biggest problem is the broken X -
i just can't get to the gui 

it is so weird because i can't find any faults -

---

### Post by nomadik on 2005-10-15
fglrxinfo just tellsme:
Error: unable to open display :0

---

### Post by nomadik on 2005-10-15
just went through the x.org logs -

i get this very often:
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: Open failed

later:
Desc: ATI FireGL DRM module
it says that the Kernel module version does not match the driver -
(incompatible kernel module detected)
DRI initialisation failed 
(maybe driver kernel module missing or bad)

---

### Post by az on 2005-10-15
First, if you have any package problems, correct them with 
apt-get -f install

then fix X by running
dpkg-reconfigure xserver-xorg (do that in recovery mode)

It should default to using non-accelerated video.  You should then be able to install the correct ATI driver for hardwar4e adcceleraqtion, using the howto on the wiki.

---

### Post by nomadik on 2005-10-15
i did everything you suggested -
but i still can't get gdm to start -
also if i invoke fglrxinfo it tells me:
Error: unable to open display:0

i am getting very desparate :( -
maybe the ATI drivers are buggy 
i don't even care about OpenGL and hardware support -
i just want my gui back ...

---

### Post by nomadik on 2005-10-15
thanks for the help -

just to close this thread -
i found out what the problem was via irc
it seems that i had upgraded from hoary with apt-get upgrade
instead of apt-get dist-upgrade - so i was missing bits and pieces -
i reinstalled the ubuntu-desktop with:
'sudo apt-get install ubuntu-desktop'

all back to normal now - yeah

---

