---
title: "grub with two hdds"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by dbaryl on 2007-09-29
Hi, I was dual-boothing with WinXP on one hard drive and Ubuntu on the slave one. I ended up moving some hard drives around, etc and now want to change the slave one (wuth Ubuntu) for a brand new, bigger one.

Here's the problem -- looks like Grub is installed on the 2nd hard drive, and when I change it out for a new one I'm unable to boot the system, at all. In fact, I don't know if I still have Ubuntu installed there, but my guess is that Grub starts from that second drive.

I have the Ubuntu 6.06 live CD.

---

### Post by Pumalite on 2007-09-29
Post:
sudo fdisk -lu
(mount your partition first)
cat /boot/grub/menu.lst

---

### Post by dbaryl on 2007-10-20
Anyway, I tried that and didn't know what to do.


So the current setup has WinXP on the primary drive, the slave one being blank -- the system does, however, require it to be there, or else won't boot. I'm guessing that the grub is still installed on the secondary drive.

---

