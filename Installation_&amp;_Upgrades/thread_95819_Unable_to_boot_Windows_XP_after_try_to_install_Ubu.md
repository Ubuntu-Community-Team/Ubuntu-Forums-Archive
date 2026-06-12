---
title: "Unable to boot Windows XP after try to install Ubuntu to USB HDD"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by Dropknee on 2005-11-27
I have a raid0 WD Raptor 10,000rpm x2 and I guess I made a big mistake trying to install Ubuntu to my external usb hdd. I follow the step by step to do this, but the problem was I trying to install Ubuntu normally instead expert mode and when this try to install the grub loader this intall in HD0, becacuse Im in normal mode and not in expert mode this dont ask me where to install the grub loader, this cause to a big malfuncional raid, now when I try to boot the raid, this show a horrible error and not boot.:( 

Anyone know how to fix this??? I really need this because the raid have all my personal data.

Pls help. my personal work depend of this

thx

---

### Post by bwog on 2005-11-28
It is most likely that your windows data are still there. 

You can repair you windows mbr by using the windows install CD in rescue mode, and use options like fixmbr (and fixboot, or edit boot.ini). It is not hard, but it is important that you know what you are doing, so search for a windows tutorial that explains how to use fixmbr (you may have to load raid drivers).

You will feel better when XP works again. 

After that, your ubuntu install will still be there and to get it going you need to put grub on a place where it can be booted. You may have to edit grub to put windows into it. Read a bit about this and take your time, keeping in mind that errors can be repaired.

---

### Post by Dropknee on 2005-11-29
sorry need to bump this, because I really need someone help.

---

### Post by Ulokye on 2005-11-29
Wasn't Bwog's post helpfull to you? what more specifically do you need help with....

p.s don't keep things you can't loose on a raid0

N

---

### Post by yaztromo on 2005-11-29
I used to fix this by getting a Windows 98 boot floppy (there's loads of images of it on the web). Boot from that and type fdisk /mbr.

I only used it for ide disk's though. Your mileage might vary with raid.

---

### Post by Dropknee on 2005-11-30
Well the fixmbr is in windows XP CD, but this opcion dont work with raid and I cant use fixboot because this corrupt the partitions. :(

---

### Post by rune on 2005-11-30
Why in the world did you pick the normal install with such a special setup? 

Is it a hardware or software raid? Do the raid come with any rescuesoftware?

If it's hardware, do the raid show in ubuntu or on a livecd?  

I don't think this forum is the place to look for help. Go with the vendor of the raid and see if they either have a support forum or search google groups.

---

### Post by Dropknee on 2005-11-30
The problem is not the raid, the array is healty is the mbr in 1 of the HDD, the grub install in HDA, and dont know why this grub damage the partition because SATA show like SDA, SDB, etc. I need to rebuild the mbr. Ubuntu dont have native support to raid install, so your raid show like this:
SDA 74gb WD xxxxxxxxx
SDB 74GB WD xxxxxxxxx
SDC 2.0 USB 84 GB xxxxxxx

 My error was try to install ubuntu in USB HDD in normal mode and not in expert

 :(

---

