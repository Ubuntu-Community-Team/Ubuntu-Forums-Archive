---
title: "Grub ?"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by ThePainter on 2005-03-04
Hi,
I have Ubuntu on my 2nd HD, and XP on my 1st HD.
I need to reinstall XP (what a suprise, I know, Why bother ?).
Anyway I thought Id run throught the process to reinstall the boot loader for when XP eats it, so I followed the way it says in the "Ubuntuguide" webpage just to see how it worked.
Well I hit problems straight away.
I booted onto the Ubnutu disc and got as far as the [!!] Partitions disks  bit and hit "Ctrl-Alt-F2" to get into the console.
Then "Enter"
then - 
mkdir /ubuntu
fdisk -l /dev/discs/disc1/discs
(here I hit problems)
mount hdb2 /ubuntu/  = failed
mount /dev/discs/disc1/disc/part2  /ubuntu/ (which is where my root was in the list given) = failed
mount part2 /ubuntu/ = cant find /etc/fstab

so I cant get any further ? any ideas where I have gone wrong ?
If I cant do this then Im going to have to reinstall both OS's

Unless I can put the bootloader on a floppy, but I cant find a way to do that either and that means I will have to boot off the floppy all the time which Im not keen on.

Thanks for any help  :confused:

---

### Post by ThePainter on 2005-03-06
Hi,
Well thanks for the help (not).

I have got it working by backing up my Ubuntu root partition with Norton Ghost 9 from within XP and then I reinstalled Ubuntu just into the root and left the Home partition with the choice to use the partition and the present data.
This installed the grub into "hd0" and then I booted into XP again and ran Ghost to restore the original root partition.
Im up and running again with my dual boot but no thanks to ubuntu and thanks to XP.

I couldnt find any help with reinstalling the grub to "hd0" apart from a couple used with redhat and I tried them but they didnt work and the one in "ubuntuguide" didnt work as I stated in my first post.

So if anyone else has this problem heres a way that you can use if you have the tools.

What we need is a bootable floppy or cd that gives you the chance to install a grub into Hd0 rather than having to go into the console.
Mandrake have one but it only works if you have mandrake installed on your HD cos I tried it but it needed a mandrake partition to direct the grub to.

Anyway Im back and Im wiser from my journey   :mrgreen:

---

