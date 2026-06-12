---
title: "GRUB not loading UBuntu"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Sh00nya on 2007-05-09
I was wondering if any of you guys could please offer some advice in resolving an issue with GRUB. It is failing to load Ubuntu Linux while at the same time loads Windows Server without a problem. 

To sum up the problem: my machine has 3 HDDs with Windows on the first and Ubuntu on the second drive...the third drive being used under Ubuntu ....last week I was trying to configure partition on the this drive n somehow messed up the primary Ubuntu drive ie the second one....consequently next time the Grub failed to load...I took it to Bill Reichert where after being unsuccessful in solving this issue he installed Fedora on third drive ....the Grub menu came back n I could boot both into Fedora as well as Windows but still not into Ubuntu...everytime I chose Ubuntu it would stop at file not found error (15)..meaning that the Grub couldn't find the kernel for Ubuntu at the location listed in menu.lst file under boot folder in grub directory in the boot partition of the 3rd drive (where Fedora was installed)...so after considerable efforts with no result I decided to install Ubuntu over Fedora thinking that with Ubuntu again on the system grub might be able to load the original Ubuntu (in 2nd drive)....but still the problem persists...I looked up online n did whatever I think matched my situation like modifying grub...updating menu.lst file...

I in fact used Knoppix as well as UBuntu Live CD for mounting partitions ....since I installed UBuntu over Fedora on the third drive (hd2,0)...thats what shows up when I search the menu.lst file in Grub shell...after I mount that drive....more over I don't have a grub.conf file although all the rest of the files like device.map are present in the grub directory....as I mentioned Windows gets loaded perfectly its the Ubuntu thats the problem...when thats chosen in the Grub menu...it shows the following msg:

----
Booting 'Ubuntu, kernel 2.6.20-15-386

root (hd2,0)
Filesystem type is ext2fs, partition type 0x83
kernel /vmlinuz-2.6.20-15-386 root=/dev/mapper/Ubuntu-root ro quiet splash

Error 15:File not found...
Press any key to continue
----

...n this is what fdisk -l shows:
---
Disk /dev/hda 20.5 GB.... (This is the Windows drive)

Device Boot Start End Blocks Id System
/dev/hda1 * 1 26 208813 6 FAT16
/dev/hda2 .......

Disk /dev/hdb: 6448 MB (This is in fact my original UBuntu)
Device Boot Start End Blocks Id System
/dev/hdb1 * 1 26 208813 6 FAT16

Disk /dev/sda: 9104 MB (This UBuntu I installed over Fedora)
Device Boot Start End Blocks Id System
/dev/sda1 * 1 608 ... 83 Linux
/dev/sda2 609 1106 ... 5 Extended
/dev/sda5 1054 ... ... 82 Linux swap/Solaris
/dev/sda6 1 608 ... 83 Linux
------

Also, as mentioned above...when I mount this last drive -- sda and enter the grub shell...run the find/boot/grub/menu.lst command it gives

(hd2,0)

as the output.

One thing I noticed was there was no gub.conf file any where...am I missing something...? To my understanding...grub is not able to locate the kernel in the location mentioned in menu.lst file..

Here's a partial shot of what 's there in the menu.lst file:

---

title Ubuntu
root (hd2,0) 
kernel /vmlinuz-2.6.20-15-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd /initrd.img-2.6.20-15-386
savedefault
.
.
title Windows NT/2000/XP
root (hd0,)
savedefault
makeactive
chainloader +1
----

BTW, I remember copying the grub file from my original Ubuntu drive (hdb1) over in the new location...is that whats causing the problem...that kernel
location didn't get updated...

If you can please help me in resolving this issue as well as kindly point out as to what am I doing wrong ...I would really appreciate. I am willing to reinstall Ubuntu again in the third drive so as to access the original Ubuntu in the first place...

TKA...

---

### Post by confused57 on 2007-05-09
I don't have much time right now, but from your fdisk -l:
> Disk /dev/sda: 9104 MB (This UBuntu I installed over Fedora)
Device Boot Start End Blocks Id System
/dev/sda1 * 1 608 ... 83 Linux
/dev/sda2 609 1106 ... 5 Extended
/dev/sda5 1054 ... ... 82 Linux swap/Solaris
/dev/sda6 1 608 ... 83 Linux

Your kernel should be root=/dev/sda1:
```
title Ubuntu
root (hd2,0)
kernel /vmlinuz-2.6.20-15-386 root=/dev/sda1 ro quiet splash
initrd /initrd.img-2.6.20-15-386
savedefault
```

I'm not familiar with the mapper/Ubuntu-root entry.

Did you use the Feisty live cd to get your fdisk -l results?  Feisty recognizes all hard drives as sdx, not hdx, regardless of whether they're IDE or SATA...or did you compile the 2.6.20-15-386 kernel in another version of Ubuntu?  I would think "sudo fdisk -l", using the Feisty live cd would have shown all your hard drives as SATA and your SATA drive may or may not be sda.  Like I said, I don't have much time now, but you could try root=/dev/sda1 in your kernel line to see if it works.

---

### Post by Sh00nya on 2007-05-09
Thanx for your reply. You are right Feisty shows all drives as sda...I used Knoppix Live CD to get the above mentioned info. As per your suggestion, I'll try to update the entry for Ubuntu in the menu.lst & see how it goes. Thanx again...:)

---

