---
title: "Error &quot;Too many partitions&quot; trying to use free space on a bootable-Ubuntu usb stick"
date: 2020-06-15
forum: Installation &amp; Upgrades
---

### Post by lucienm2 on 2020-06-15
Hi,
I created a bootable Ubuntu 18.04 on a usb stick of size 32 Gb.
It created me (Please see the screen capture in attach) :
   - a partition 1 of 1.9 Gb ISO9660 with Ubuntu on it,
   - a partition 2 of 2.4 ,Mo Fat
   - free unused space of 29 Gb
Of course, I wanted now to use the free 29 Gb to store any data there :
I called thus 'Disks' utility, choose the free space, and clicked on the "+" sign.
   - the first screen asks me to choose the size, and 'extended' or not :
      + if I check 'extended' I cannot go further (he then says "mac disk labels do not support extended partitions" -> ?? I am under Ubuntu 18.04 ??)
      + I thus did not check 'extended', and on the next screen, whatever I choose as ext4,ntfs, or fat, I get the same message "Too many partitions"
However I have only 3 partitions on this usb disk, as you can see from my screenshot.

So I don't understand what's happening ; does anyone see ?
I tried with other tools, gparted, Paragon HDM, but none is able to give me access to this free space.

As a subsidiary question, would it be linked to the fact that partition 1 has been created as ISO9660, and that the whole disk then would act like a finalized CD ?

[ATTACH=CONFIG]286230[/ATTACH]
Thanks in advance for your time.

---

### Post by TheFu on 2020-06-15
**sudo fdisk -l** please.  images don't provide sufficient details.
Doubt i can help since i only use flash storage for emergency needs or to install the OS on real storage.

---

### Post by yancek on 2020-06-15
Are you using an install of Ubuntu do try to make these changes on the 'live' usb?  You won't be able to change anything on the usb if you are booted from it.  If you wanted to use the free space, the best option would have been to create a 'live' persistent usb.  Is the disk label type gpt or msdos?

---

### Post by ActionParsnip on 2020-06-16
You can only have 4 primary partitions if memory serves. Make one primary partition then the rest as an extended partition. You can then cut the extended partition into logical partitions as you need.

---

### Post by lucienm2 on 2020-06-16
>  sudo fdisk -l /dev/sdc
[sudo] Mot de passe de lucien : 
Disque /dev/sdc : 28,9 GiB, 31037849600 octets, 60620800 secteurs
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Type d'étiquette de disque : dos
Identifiant de disque : 0x2b192737

Périphérique Amorçage   Début     Fin Secteurs Taille Id Type
/dev/sdc1    *              0 3753599  3753600   1,8G  0 Vide
/dev/sdc2             3672780 3677451     4672   2,3M ef EFI (FAT-12/16/32)
lucien@LM:~$ 


As you can see, I have only 2 partitions, the rest is 29 Gb of free space ...
Thanks

---

### Post by lucienm2 on 2020-06-16
I did not boot on the usb.  I booted on  SSD hard disk with installed Ubuntu.
From the previous reply you can see that it is msdos.
To create the stick, I used the "Boot disk creator" available under "System tools > Administration" of the gnome-menus ; the only thing I had to specify is the location of the Ubuntu .iso image.  This program erases the stick before writing to it.  How do you see that I could proceed to preserve the free space ?
Thanks

---

### Post by Skaperen on 2020-06-16
how did you make the bootable USB memory stick?  if you made it in another OS then make another one so you have [FONT=courier new]***TWO***[/FONT] of them.  boot from one of them and then insert the 2nd one and add the new partitions to the 2nd one.  then boot from the 2nd one to be sure you did it correctly and didn't ruin it.  if the 2nd one boots up OK then do the partition add to the 1st one.

---

### Post by TheFu on 2020-06-16
Please always use "code tags" when posting shell output so columns line up and we don't each have to reformat it locally.  Please.

i see only 2 partitions but they seem "funny."
[LIST=1]
[*]/dev/sdc1 - the iso iso9660 format, read-only
[*]/dev/sdc2 - the uefi boot partition
[/LIST]

To modify this partition table the partitions cannot be in-use; either mounted or the OS cannot be running from any partition on it.  A different boot system is necessary.

The "too many partitions" error is new to me. Could that be for some other storage connected to the system?

So i was able to reproduce the problem here.
```
$ sudo fdisk -l /dev/sdb
Disk /dev/sdb: 57.7 GiB, 61958258688 bytes, 121012224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
**Disk identifier: 0x193f762d**

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *        0 3478783 3478784  1.7G  **0** Empty
/dev/sdb2       10528   15519    4992  2.4M ef EFI (FAT-12/16/32)
```
inside gparted, it claims the flash drive is 248GB when it is definitely only 64gb.  I'd guess this is due to the way the ISO was laid out originally.

```
sudo parted -l /dev/sdb

Model: Corsair Voyager VEGA (scsi)
Disk /dev/sdb: **248GB**
Sector size (logical/physical): 2048B/512B
**Partition Table: mac**
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                **Apple**
 2      5390kB  7946kB  2556kB               EFI

```

Parted sees the layout differently and makes the problem clear - Apple.  

There hasn't been any Apple products anywhere near any of my equipment in about a decade.  it only lasted 3 weeks when i had a Mac before it was shipped away.

So my google-fu found this: [https://askubuntu.com/questions/814745/in-ubuntu-iso-mbr-why-does-a-gpt-partition-overlap-the-boot-partition-and-make](https://askubuntu.com/questions/814745/in-ubuntu-iso-mbr-why-does-a-gpt-partition-overlap-the-boot-partition-and-make) with a workaround solution.
Looks like Sudodus' tool [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) can include a persistent partition for us as it creates a bootable flash drive from an iso file.

---

### Post by TheFu on 2020-06-16
Did a **mkusb**  from an iso and asked for persistence w/ GPT partitioning and both bios and uefi booting. i didn't understand all the questions do the NTFS sdb1 surprised me.  There wasn't any mention of NTFS that i recall.

```
Disk /dev/sdb: 57.7 GiB, 61958258688 bytes, 121012224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D9235A67-3F4F-47D6-92EA-928D3B9E2F88

Device        Start       End  Sectors   Size Type
/dev/sdb1  62515200 121010175 58494976  27.9G Microsoft basic data
/dev/sdb2      1953      3906     1954   977K BIOS boot
/dev/sdb3      3907    503906   500000 244.1M EFI System
/dev/sdb4    503907   4021484  3517578   1.7G Linux filesystem
/dev/sdb5   4022272  62515199 58492928  27.9G Linux filesystem
```
sdb5 is ext4 which isn't nice for flash storage. Would prefer both the NTFS and ext4 be f2fs myself, but that would probably break things.
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint,label
NAME             SIZE TYPE  FSTYPE      MOUNTPOINT LABEL
sdb             57.7G disk                         
&#9500;&#9472;sdb4           1.7G part  iso9660                Ubuntu-MATE 16.04.6 LTS amd64
&#9500;&#9472;sdb2           977K part                         
&#9500;&#9472;sdb5          27.9G part  ext4                   casper-rw
&#9500;&#9472;sdb3         244.1M part  vfat                   usbboot
&#9492;&#9472;sdb1          27.9G part  ntfs                   usbdata
```

i have not tested the boot as is and probably won't today.  My systems are all busy for the evening.   mkusb is pretty impressive for what it claims to do.  Did read that the casper-rw label was mandatory, at least for 16.04 persistent partitions.

---

### Post by lucienm2 on 2020-06-17
Many thanks, TheFu, for your interest, and even more thanks for the link you gave to  [https://askubuntu.com/questions/8147...ition-and-make]("https://askubuntu.com/questions/814745/in-ubuntu-iso-mbr-why-does-a-gpt-partition-overlap-the-boot-partition-and-make") ,  as this describes the situation really good.

I make a summary of it here for the people who will read this post later in the future : 

Cause :[INDENT] The program available in the Ubuntu distribution, "Créateur de disque de démarrage" in french (that I would translate to something like  'Live Ubuntu boot stick creator"), which uses the deb file "usb-creator-gtk" does a pretty good job in copying the iso of Ubuntu on a usb stick and make it bootable for +/- any kind of operating system that this stick will be plugged in.
However, to achieve this kind of universality, the master boot record generated on the usb stick is tweaked and not standard at all.  For example, one of the partitions overlaps with the others ; and consequently the mbr cannot be edited/modified with standard partitioning tools.[/INDENT]
Solution : 


[LIST]
[*]Either you are happy with how easy it was to use this program, and you forget about the 28 Gb free space that you will never manage to have access to (it's not my case - not for how much money, but just I can't afford :-) 
[*]Either you find back an old 4 Gb usb stick, for which you are happy to use this program and you won't have this feeling wasting space (I don't have any, and don't want to buy one - I'm hardminded :-) 
[*]Either you do it 'the old school' (= where you need to put your brain at work if you want to achieve something) and you do more or less like explained [here]("https://askubuntu.com/questions/817931/how-to-create-a-live-ubuntu-usb-drive-with-persistence-for-bios-using-only-termi"), which I will translate for me into :
[LIST]
[*]first completely erase the stick, in order to be able to recreate a master boot record of your own 
[*]use a partitioning tool and create the number of partitions needed, in my case 1 bootable partition FAT of 4Gb, the rest as a partition of the type you like. 
[*]use one of those available programs to copy an iso file to the usb stick ; personally I used LinuxLive USB Creator thus to copy the .iso to the stick (this is what I ran a few years ago, to get my first Ubuntu installed ...)
[*]I did this, and I confirm that it works : I have now an Ubuntu live stick on which I can boot to install Ubuntu on other computers, and an extra disk space to store programs that I will install afterwards. 
[/LIST]
  
[/LIST]

I end up saying to TheFu, that I tried to put code tags around my terminal output, but did not find anything to do it   ->   I was in "Submit a quick reply" ...
For your info, I opened the first sectors of the stick and there somewhere I could see the words "Apple" and "EFI".
I doubt you are still interested in seeing the MBR of my stick, but just for the pleasure of quoting it, here it is !
```

Offset     Title                      Value
------     -----                      -----
0          MB loader code             45 52 08 00 ...
1B8        Windows disk signature     3727192B
1N8        Same reversed              2B192737

Partition table Entry #1

1BE        all 0's

Partition table Entry #2

1CE        80=active partition        00
1CF        Start head                 158
1D0        Start sector               7
1D0        Start cylinder             228
1D2        Partition type (hex)       EF
1D3        End head                   232
1D4        End sector                 16
1D4        End cylinder               228
1D6        Sectors preceding part2    3672780
1DA        Sectors in partition #2    4672

Partition table Entry #3

1DE        all 0's

Partition table Entry #4

1EE        all 0's


1FE        Signature (55 AA)          55 AA
```

---

### Post by TheFu on 2020-06-17
> **TheFu said:**
>  
Looks like Sudodus' tool [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) can include a persistent partition for us as it creates a bootable flash drive from an iso file.

i will point you once again at this.  it does what you seek.

---

