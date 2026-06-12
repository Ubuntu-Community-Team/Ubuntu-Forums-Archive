---
title: "Triple Boot System - Grub 2 not in the MBR - how to do?"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by LinuxFan9 on 2010-01-22
Hi there,

System:
- XP Prof 1 /dev/sda1
- XP Prof 2 /dev/sda2
- Ubuntu    /dev/sda5

Grub 2 installed in the MBR ->
booting all three operating systems with no problems.

BUT:

Grub 2 installed in the MBR destroys the driver of alcohol, which is installed on XP 1st.
Alcohol starts, but then there is an error message that the driver of alcohol could not be loaded and there is no virtual drive of Alcohol.
But that's what I need using XP Prof 1.

How can I use Grub 2, booting all three Operating Systems, without destroying the driver of alcohol? 

Sincerely.

---

### Post by bryanl on 2010-01-22
first is to read [grub2 docs](https://help.ubuntu.com/community/Grub2)

If you had grub2 installed and overwrote the MBR. then it's a simple matter of mounting the ubuntu root partition (and /boot if segregated) then running (see 'Reinstalling from LiveCD") 
```
sudo grub-install --root-directory=/mnt/ /dev/sdX
```
substituting the mount point and drive device as appropriate. That will reset the MBR and the grub menu you had setup in the ubuntu install.

If you want to add entries or otherwise change the grub boot, see the docs as that is much more convoluted (and capable) than it used to be with the old grub.

The alcohol problem is a whole 'nother can of worms and I am not familiar with that app or why it needs to mess with the MBR

---

