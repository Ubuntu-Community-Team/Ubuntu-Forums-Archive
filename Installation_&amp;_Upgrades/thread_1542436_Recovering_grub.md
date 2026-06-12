---
title: "Recovering grub"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2010-07-30
I'm using ubuntu 10.04 as my main distro. I have partitioned my
hard drive for other distros. Not too long ago I installed mint xfce
and it installed its own grub, then when ubuntu updates installed a 
new kernel, it rewrote the ubuntu grub back to the MBR. I like that.

I'm going to install a new mint distro. It will write a mint grub,
which (if all goes right) include entries for ubuntu.

**Question** how do I manually restore the ubuntu grub. Will dpkg
do it?
thanks
tim

---

### Post by davidmohammed on 2010-07-30
see this [link]("https://wiki.ubuntu.com/Grub2") (its in the section describing how to restore from the live CD).

---

### Post by tim042849 on 2010-07-30
thank you!

---

### Post by oldfred on 2010-07-30
If you can boot into your Ubuntu install from Mint you do not have to use the liveCD:

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

If you do not want Ubuntu to autoreinstall grub2 to the MBR you should be able to select no drive in teh dpkg-reconfigure.

---

### Post by tim042849 on 2010-07-30
oldfred, that is what I was looking for. I guessed that
synaptic was using that anyway. I will mark this thread as
solved. Will test later.
Thanks :cool:

---

