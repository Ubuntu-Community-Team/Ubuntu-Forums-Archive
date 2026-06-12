---
title: "how to upgrade from 10.4 DESKTOP to 10.4 NETBOOK edition ?"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by Court-circuit on 2010-06-04
Hi all,

couldn't find the answer anywhere, and here is the thing :
I got a Sony Vaio VGN-TX3 XP, from 2006.
I have installed 10.4 desktop edition, as usual, but it is really slow.

I was wondering :
1. woudl i gain to install the 10.4 Netbook edition ?
2. how to updgrade from one to the other without doing a fresh install ?

could someone help on this ?

thanks

C.

---

### Post by dino99 on 2010-06-04
goto: system admin synaptic

search "ubuntu-desktop" and right click it to remove/purge it

search "ubuntu-netbook" and install it

clean the system, into a console:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by Court-circuit on 2010-06-04
Cool. thanks.

Do u think i will gain ? what would be hte major difference ?

my proc is not an atom, but a intel Centrino Core solo U1400 on a 945GMS chipset.

bests
C.

---

