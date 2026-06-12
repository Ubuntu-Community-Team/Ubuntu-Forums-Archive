---
title: "Grub fails after restoring 10.10"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by walt11 on 2011-04-29
After restoring my 10.10 partition (using FSArchiver), Grub fails when I try to boot, with these error messages:
>   error: out of partition
  error: Symbol not found: 'grub_OS_area_addr'
  error: Symbol not found: 'grub_OS_area_addr'
  Failed to boot both default and fallback entriesThis is Grub version 1.98+ 20100804-Subuntu3

This is a dual boot system, with Windows XP-SP3 on the internal hard drive, and Ubuntu 10.10 on an external drive. (I can't reach the Windows entry in the boot menu, since it is not responding to the arrow keys.)

(I restored the 10.10 partition because my upgrade to 11.04 hung - almost near completion.)

I'm booting from a System Rescue CD, and don't know how to fix Grub.

Thanks.

---

### Post by Bobhuber on 2011-04-29
> **walt11 said:**
> After restoring my 10.10 partition (using FSArchiver), Grub fails when I try to boot, with these error messages:
This is Grub version 1.98+ 20100804-Subuntu3

This is a dual boot system, with Windows XP-SP3 on the internal hard drive, and Ubuntu 10.10 on an external drive. (I can't reach the Windows entry in the boot menu, since it is not responding to the arrow keys.)

(I restored the 10.10 partition because my upgrade to 11.04 hung - almost near completion.)

I'm booting from a System Rescue CD, and don't know how to fix Grub.

Thanks.
Boot from the live cd. From a terminal >  sudo mount /dev/sda1 /mnt (replace sda1 with the name of your boot partiition)
sudo grub-install --root-directory=/mnt/ /dev/sda  (replace sda with the name of the boot drive )

---

### Post by walt11 on 2011-04-29
Thank you Bob, for that quick reply. I'm not sure which partitions/drives you mean, so need to ask you.

My Windows C: drive is sda1. My Ubuntu 10.10 is on sdb5. Which of these is my boot partition? (The Grub boot menu defaults to the Ubuntu system.)

The boot device startup menu defaults to the internal hard drive, sda. Is that my boot drive?

Sorry to be so dense about this.

---

### Post by Bobhuber on 2011-04-29
> **walt11 said:**
> Thank you Bob, for that quick reply. I'm not sure which partitions/drives you mean, so need to ask you.

My Windows C: drive is sda1. My Ubuntu 10.10 is on sdb5. Which of these is my boot partition? (The Grub boot menu defaults to the Ubuntu system.)

The boot device startup menu defaults to the internal hard drive, sda. Is that my boot drive?

Sorry to be so dense about this.
Yes follow the directions using sda1 and sda for the boot drive and you should be fine

---

### Post by walt11 on 2011-04-29
> Yes follow the directions using sda1 and sda for the boot drive and you should be fine

Bob, it installed with no errors, but when I boot,  I just get the Grub prompt:

grub>

How do I get the boot menu?

---

### Post by walt11 on 2011-04-29
I just tried booting from the external drive, get the boot menu, but the same errors as in my original post.

---

### Post by oldfred on 2011-04-29
if your Ubuntu install is in sda5 you should be using that  to reinstall grub2's boot loader to the MBR.

Can you manually boot?

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd0,5) or sda5
sh:grub>ls (hd0,5)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,5)/vmlinuz root=/dev/sda5
sh:grub>initrd (hd0,5)/initrd.img
sh:grub>boot

If you can boot then reinstall grub from there.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

If you cannot boot, reinstall grub.
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by walt11 on 2011-04-30
Hello oldfred! Thanks for responding.

My Ubuntu install is on sdb5.
I cannot boot, so will try the links you suggested. I'll probably have additional questions.

Thanks!

---

### Post by oldfred on 2011-04-30
Bobhuber's instruction were correct except you need to use sda5. He posted the two commands in red which is all you need if you know it is sda5 & sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
[COLOR=Red]sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by walt11 on 2011-04-30
It worked perfectly! (My linux partition is sdb5.) THANKS so much!! It's this kind of support that confirms me in my choice of Ubuntu. (I think I've said that before - and this just re-emphasizes it.)

---

