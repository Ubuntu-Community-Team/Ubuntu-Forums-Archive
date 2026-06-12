---
title: "Grub2 configuration problem?"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by scrappyddz on 2010-09-24
ok, here is my current cycle
boot up in to chameleon, lists only Mac OS X as a boot option. Reboot, load Ubuntu 10.4 install cd, 
get to a terminal, 
mount /dev/sda3 /mnt 
grub-install --force --root-directory=/mnt/ /dev/sda3
 
reboot, let chameleon come up, it sees both Mac OS X & Ubuntu partitions
and I can boot to either or happily,
 
now here is the problem... If I select linux and boot in to linux from
chameleon, i am brought to the grub menu, where i can select the first
choice which is normal ubuntu 10.4 and every thing is great... until I
reboot and my linux partition no longer shows up in chameleon, as if
tthe act of booting in to grub is changing something / deleting itself
from the partition? and I have to do the whole thing over again. SO, not
having to even go in to OS X, I'm not sure thats really the concerns
more as I'm doing something wrong with grub.
 
Thanks in advance!

---

### Post by zvacet on 2010-09-24
If you want grub to be your bootloader you can read [this.]("http://ubuntuforums.org/showthread.php?t=1405867")

---

### Post by scrappyddz on 2010-09-24
Interesting, but I was kinda hoping to get this setup going, if I can't, so be it... but Chameleon is kinda sexy =)

---

### Post by scrappyddz on 2010-09-27
fyi doing a sudo update-grub , twice (yes, twice) seemed to make it work

---

