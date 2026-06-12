---
title: "BIOS cannot read the USB stick for fresh install"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by mistakos on 2011-01-26
Hi:)

I am pretty new to linux so i need your help. I installed Ubuntu at my desktop pc instead of Windows XP. Because my cdrom is damaged I tried the USB stick approach, which worked perfectly at my netbook. When i restarted my PC and changed the boot sequence, so that it can boot from the USB stick, everything went perfect. BIOS read the USB stick and it booted without any problem. 

I installed Ubuntu and started working with it, until i had to restart my PC again. Then it showed me a msg and the it gave me the initramfs, from BusyBox. I searched a lot in google and someone suggested to do an upgrade, which i did. i upgraded to 11... something (can't recall the version) but from then on i lost any graphical environment i used to have. sometimes it doesn't even boot to root properly.. 

Without finding a solution to this either, i decided to reinstall Ubuntu and start over. But the problem is that BIOS cannot read my USB stick, so i cannot boot from the USB so i cannot enter the live cd.

Any ideas why my USB cannot be red by BIOS so that i can boot from it? 

Thanks in advance

---

### Post by lt_y3k on 2011-01-26
Maybe your image is not installed correctly to usb stick? Try to reinstall image to usb stick with unetbootin.

---

### Post by BACbOK on 2011-01-26
If you have Windows, you can do bootable usb-stick with [Lili usb creator]("http://www.pendrivelinux.com/linux-live-usb-creator/") from Ubuntu iso-file.

---

### Post by mistakos on 2011-01-26
the USB stik is the same i installed linux at my netbook and my desktop. no i don't have windows, but i will try to remake the boot USB stick. Is this going to solve the problem that when i enter to change the boot sequence on BIOS it cannot see the USB???

i thought it was more like a drivers problem...

---

### Post by BACbOK on 2011-01-26
What BIOS you have?

---

### Post by mistakos on 2011-01-26
```
Bios Version: V1.6 062305 20:14:57
```

---

### Post by BACbOK on 2011-01-26
> **mistakos said:**
> ```
Bios Version: V1.6 062305 20:14:57
```
What producer (vendor) of BIOS?
AWARD, AMI, Phoenix, Compaq etc...

---

### Post by mistakos on 2011-01-26
Phoenix v6.0

---

### Post by wilee-nilee on 2011-01-26
Look on google with a per session key prompt for your computer. This will get you to a out of the bios boot from menu. Mine is f12 eeepc is esc HP is f9.

---

### Post by mistakos on 2011-01-26
Thanks ppl. I got my USB to boot and i installed a fresh copy of Ubuntu. Unfortunately i still have the same problem, as they state here..
[http://ubuntuforums.org/showthread.php?t=1027432](http://ubuntuforums.org/showthread.php?t=1027432)

so i posted my results over that thread. Although, if anyone over here can help, see my results here
[http://ubuntuforums.org/showthread.php?p=10400471#post10400471](http://ubuntuforums.org/showthread.php?p=10400471#post10400471)

thanks again..

---

### Post by mistakos on 2011-01-26
wilee thanks for doing this :) i might be a pain in the ***.. but i won't do any more crazy stuff :)

EDIT
now that i have the new problem.. do you want me to install a fresh copy of ubuntu?

---

### Post by wilee-nilee on 2011-01-26
So look closely at this link. Since your booting with a thumb the HD's can get interchanged, so that sda reads as sdb when your in the live session, reloading grub.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Notice the command
sudo fdisk -l
this will identify if the Ubuntu partition is shown as sdb rather then sda adjust the two following commands I had you run accordingly.

---

### Post by wilee-nilee on 2011-01-26
> **mistakos said:**
> wilee thanks for doing this :) i might be a pain in the ***.. but i won't do any more crazy stuff :)

EDIT
now that i have the new problem.. do you want me to install a fresh copy of ubuntu?

I don't think you need to reinstall, it is just verifying how the HD is being read when using the thumb in a live session, does this make sense?

I think on the thumb the sda is reading as sdb.

---

### Post by mistakos on 2011-01-26
ok.. the fdisk says that the boot is on the sda1. i tried the two commandes. haven't rebooted yet. just wanted to write a msg that pops when i run the grub-install --root-directory... command.

```
/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
```

is this normal?

---

### Post by mistakos on 2011-01-26
still the same.. no improvement.. :(

---

### Post by wilee-nilee on 2011-01-26
Ah flexnet is a problem look at post 18 and 22 here.
[http://ubuntuforums.org/showthread.php?t=1605076](http://ubuntuforums.org/showthread.php?t=1605076)

Post 22 has a link to Amazon look for this section.

> The part of FlexNet that survives in the MBR apparently interprets the clean install process as an attempt to circumvent DRM. So, reinstallation is blocked. The solution is to completely zero out ALL sectors of the primary hard disk, including the MBR, before doing the clean install of Win7. I'll eventually post a detailed explanation of the process in a comment to this review.

---

### Post by wilee-nilee on 2011-01-26
I believe you can wipe or 0 out the MBR here is a link kind of old but the command is correct in the first post.

If you run the first dd command at bs=446 it should leave the partition table there and you would just reload grub as we have been trying.
[http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query-606489/](http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query-606489/)

---

### Post by wilee-nilee on 2011-01-26
Here is another forum link that may be more informative. Notice the third command and where your error for flexnet is. Also notice oldfred's comment and links as well, they are a knowledgeable forum member.
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)

---

