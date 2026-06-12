---
title: "Installing windows a-f-t-e-r Ubuntu?"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by jakew1991 on 2005-06-17
Is such a thing possible??  If so, any pointers or suggestions would be helpful.  I'm installing Windows XP under Qemu right now, so hopefully actually running Windows will be faster than installing it.

 - Jake

P.S. (don't read if u dont want to): I used my mom's computer one time (Win XP)...now I know why I switched to Linux!!  (*slow!!*)

---

### Post by bored2k on 2005-06-17
[QUOTE=jakew1991]Is such a thing possible??  If so, any pointers or suggestions would be helpful.  I'm installing Windows XP under Qemu right now, so hopefully actually running Windows will be faster than installing it.

 - Jake

P.S. (don't read if u dont want to): I used my mom's computer one time (Win XP)...now I know why I switched to Linux!!  (*slow!!*)[/QUOTE]
 Running Windows inside Linux cant be faster than installing the real thing, ever. You can install windows then restore Grub. If thats not what you want, I misunderstood..

---

### Post by clb137 on 2005-06-17
[QUOTE=jakew1991]Is such a thing possible??  If so, any pointers or suggestions would be helpful.  I'm installing Windows XP under Qemu right now, so hopefully actually running Windows will be faster than installing it.

 - Jake

P.S. (don't read if u dont want to): I used my mom's computer one time (Win XP)...now I know why I switched to Linux!!  (*slow!!*)[/QUOTE]re 


In order for windows to boot it likes to be on the first partition  or at least below 1024 in the partition, therfore the wise  move is to install windows first then linux  


clinton

---

### Post by intangible on 2005-06-17
I assume you want to install Windows along-side your Linux installation.  

First, backup anything important.  Windows does not play nice a lot of times with other OSes

What you'll need to do is resize your linux partition to give windows somewhere to install... I've resized partitons from a Ubuntu Live CD with gparted, but it was tricky since it wasn't included on the CD.  I would look around for another live CD that already has QTparted or Gparted on it to make it easy on yourself.  You cannot resize it from within Ubuntu, because you cannot resize a currently mounted partition (or at least you shouldn't :D).

Then you can install windows into the free space on the hard drive, hopefully it won't muck around with your Ubuntu partition (that's why you made a backup, right?).

After the install, GRUB will be gone from the MBR, so you'll have to boot off a live CD again, mount the linux partition: 
**mount /dev/hda1 /mnt**
then
**chroot /mnt** This will make / to be your hard drive partition
and to reinstall grub
**grub-install --recheck**
then update /boot/grub/menu.lst to boot Windows, add this:
[b]title Windows XP
rootnoverify (hd0,1)
chainloader +1[/b]
and comment out the line that says **hiddenmenu**

And if all goes well, you should have a choice of what to boot after the next reboot.

**THIS COULD MESS STUFF UP, MAKE BACKUPS!** 

Good Luck

---

### Post by clb137 on 2005-06-17
As the previous one states it could mess up, therefore if you DO NOT have anything important in ur linux install it is far better to have 'Windows installed first then your linux,  

the howto described above does work but be warned not for everyone the recommened way is win first then linux, 

goggle search and as the same question



clinton

---

### Post by jakew1991 on 2005-06-17
[QUOTE=bored2k]Running Windows inside Linux cant be faster than installing the real thing, ever. You can install windows then restore Grub. If thats not what you want, I misunderstood..[/QUOTE]
 Really??

The Windows XP install usually takes an hour to an hour and a half on my machine (before I switched to Linux I had to re-install *many* times).  Under Qemu, install had to run overnight.  Maybe because I was trying to use a .img file?  (I imagine it would be faster to run Win XP under emulation if it's actually installed on a partition)
 
 - Jake

---

### Post by jerrykenny on 2005-06-17
Couldnt you cadge an old 5Gb or so hard drive from someone ?    remove your original hard drive to the secondary in the first IDE,   plug the new-un into the pole position and do a normal install ?

You just then have to post another thread for dual-booting  :smile:

---

### Post by jakew1991 on 2005-06-17
[QUOTE=jerrykenny]Couldnt you cadge an old 5Gb or so hard drive from someone ?    remove your original hard drive to the secondary in the first IDE,   plug the new-un into the pole position and do a normal install ?

You just then have to post another thread for dual-booting  :smile:[/QUOTE]

I'm on a laptop.   :smile: 

 - jake

---

