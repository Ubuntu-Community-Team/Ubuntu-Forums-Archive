---
title: "ubuntu 8.04 on external harddisk"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by hansikke on 2008-07-24
hello,

i've installed ubuntu 8.04 on my external harddisk but it will not boot

i've done the installation from the live cd with success.
the external disk was previously a ntfs disk. I've used the free space of the disk what was about 25GB to make a ext3 partition of 20GB and a swap partition of 5GB.
the idea is nothing to change on my internal harddisk.
so i also installed grub on my external disk.
when i bootup and sellect to boot from my usb drive.
grub displays an error 17.

is there a sollution to get it working whitout changing the MBR from my internal disk and without the loss of the data on ntfs partition of my external disk.

the internal drive is sda
the external drive is sdb
ntfs partition on external drive is sdb1
ext3 partition on external drive is sdb2
swap partition on external drive is sdb3

thanx in advance 

greetings Hans

---

### Post by cdtech on 2008-07-24
Booting from your BIOS to your external drive, GRUB will see the device as the primary drive. So set up your external drives menu.lst to read the kernel from (hd0,1).

Hope this helps......

**P.S.**
Or from the partition you have the GRUB BOOTLOADER installed to. (hd0,0) (hd0,1) ect.....

---

### Post by Euphorion on 2008-07-24
Hallo

According to the Grub Manual error 17 is:
"This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB"

Which as far as I can interpret things is that when booting, Grub is loaded and then wants to continue loading but is directed to a partition whose filesystem type is not recognized. The cause is most likely to be that in menu.lst the Partition data is pointing to the wrong partition. If upon boot, i assume from Bios, the external disk will most likely be the primary disk in Grub notation (hd0,0) (Grub always stats from zero for both disk and partitioning numbering. Therefore determine in which partition of the external disk you have installed Ubuntu and adjust the value in menu.lst accordingly. If for example Ubuntu is in the 2nd partition of your external disk and Grub is also loacated there then the value to use will be (hd0,1). The workings of Grub and its manual can be found here [http://www.gnu.org/software/grub/grub.de.html](http://www.gnu.org/software/grub/grub.de.html) see link documentation on left side of the page.

I am very interested in your method and will follow this thread closely as I too want to install an additional Ubuntu 64 Bit on an external drive in order to test to see if all works well before overwriting my 32 bit Ubuntu.

---

### Post by timcredible on 2008-07-24
do a search, there's a site that explains this - think it's at ubuntukids.com or something like that.  there's 2 things you need to do:

1 - when installing ubuntu to the external disk, you need to change where grub gets installed.
2 - you need to go to /boot/grub/menu.lst and change that back after it's installed.

i ran off an external usb-connected drive for a while, it works fine.

---

### Post by hansikke on 2008-07-25
still no luck
every time i want to bootup i get 
grub 1.5.

loading grub
eror 17

and i can do nothing

i've included a txt file with some information i've gatherd using the livecd

i've tried changing the numbers in the map file
i've also tried changing the numbers in the menu file from 
hd(1,1) to hd(0,1) and to hd(1,4)

is there something else i need to do
i'm a real noob at this

thnx in advance

greets hans

---

### Post by Pumalite on 2008-07-25
Try (hd0,0)

---

### Post by hansikke on 2008-07-25
no doesn't work either

it still gives me the same error
grub loading stage 1.5.
grub loading
error 17

any other ideas?

---

### Post by Pumalite on 2008-07-25
Reinstall Grub to /dev/???
???= your USB
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by hansikke on 2008-07-25
i've reinstalled grub but nothing changed
could there be a problem with the disk type ext3?

---

### Post by Pumalite on 2008-07-25
On the subject; this is a thread worth reading:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=herman)

---

### Post by hansikke on 2008-07-25
I installed ubuntu the way they discribed it.
only instead of the guided partitioning i choose manual partitioning because the guided one erased my ntfs partition.

---

### Post by codingfreak on 2009-08-25
Do you have any lucky in solving the problem which you are facing ??

---

