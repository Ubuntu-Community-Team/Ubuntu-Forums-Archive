---
title: "[SOLVED] Do I need to upgrade my hardware?"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Spaceman9 on 2008-05-21
After installing Ubuntu 8.04 when I reboot I get an Error 15 message and it won't boot the OS. 8.04 sees my hard drives out of order and as sd instead of hd. I only have PATA drives. Does anyone know how to fix this? Is there something I can type into Grub to fix it?

Ubuntu 7.04 and Kubuntu 7.10 install without problems. Did Ubuntu change the installer so it only sees drives as sd? Did Ubuntu remove the code that sees drives as hd or PATA drives? Do I need to upgrade my hardware to use 8.04? Thankx for any help.

---

### Post by Patb on 2008-05-21
Spaceman, Ubuntu has been using sd notation for a while now.  It seems that maybe your grub menu is not consistent with the device notation but it's not clear why.  

You could reinstall grub using the instructions here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If that seems confusing or just doesn't work, post the output of each of these commands run from a terminal:
```
sudo fdisk -l
sudo blkid
cat /boot/grub/menu.lst
```

> Do I need to upgrade my hardware to use 8.04?
Probably not, but you haven't indicated what that hardware might be ;).

Cheers, Pat.

---

### Post by Spaceman9 on 2008-05-21
Thank you Patb I'll read it, but I bet I'm going to end up having to use freespire. Freespire uses Ubuntu 7.10 and I've never had any problems with Ubuntu untill 8.04. So I don't know what's going on.

I built my computer in 2001 so it's really old hardware now. My bios is from 1999.

---

### Post by dstew on 2008-05-21
If you had another Ubuntu system on your computer before, and you installed 8.04 without installing grub, you can get this error. I assume you get the error 15 at the start of the grub boot, before you get a menu. Am I correct? The fix is to re-install grub. It is easy to do. The link in Patb's post has the intructions.

---

### Post by Spaceman9 on 2008-05-21
Thank you dstew, I'll try to fix grub. I didn't have anything on my drive. I reformatted it first so I'd have a clean install.

---

### Post by Spaceman9 on 2008-06-27
This is an update on the Error 15 problem. I solved this problem by taking all the partitions off my first 2 drives with the partition thing in Ubuntu. Then I made a root and a home and a swap partition on the first drive. Then I installed PCLOS and it's GRUB on the MBR of the second drive and then installed Ubuntu 8.04 and it's GRUB on the MBR of the first drive.

I still got the Error 15 message so I had to edit the Ubuntu GRUB so it could find it's GRUB on hd0,0. I haven't had any problems with booting since.

---

