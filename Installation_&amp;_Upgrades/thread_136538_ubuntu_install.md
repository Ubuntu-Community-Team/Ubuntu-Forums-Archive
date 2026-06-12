---
title: "ubuntu install"
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by exo-skeletal on 2006-02-26
ok i have ubuntu 5.10 installed and now i want to install windows xp aswell and dual boot them. how would i go about dual booting them and i want to keep the data i have on my ubuntu install. thx in advance

---

### Post by shams2 on 2006-02-26
first make a grub boot floppy, in a termal type:
grub 
then type:
root (hd0,x) 
x is your /boot partition minus one, then do:
setup (fd0,0)
this will create the grub boot floppy test before using if it is working, then install the xp, boot with boot floppy to ubuntu and install the gurb to mbr with:
root (hd0,x)
setup (hd0,0)

---

