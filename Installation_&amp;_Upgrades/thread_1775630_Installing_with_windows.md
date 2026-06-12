---
title: "Installing with windows"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by Maxzeroedge on 2011-06-05
I have downloaded ubuntu 11.04. I used version 9 on sis' lappy and personally like it more than windows... The major reason, it being free :D
Anyway, I have windows 7 installed. I want to install Ubuntu on a separate drive. Can I do this without Wubi? Because it makes me download the files and I can't stay online for that long to let it download.
Thanks in Advance.

---

### Post by jaacko on 2011-06-05
Yes, you can install Ubuntu without Wubi. And I also recommend doing so if you really plan to use Ubuntu. Just download the ISO disk image from the Ubuntu website and burn it to a disk. Then boot the computer from the disk. 

I'm not sure what you mean by 'separate drive'. If you mean a separate partition on the same hard drive where Windows currently is, I recommend resizing the Windows partition (to make room for ubuntu) within Windows before installing Ubuntu. The Ubuntu installer has a partitioning tool built-in and that can handle the rest of the partitioning. Also remember to make a backup. Many things can go wrong while fingering partitions.

This is also a quite common topic here on forums, so you'll propably find answers to many of your questiong conserning installation by using the Search-box. :)

---

### Post by kansasnoob on 2011-06-05
This is a great dual-boot guide:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

I prefer this method:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

If you need detailed info we should first see what your partitioning arrangement looks like so, once you've got a Live CD/USB, please boot selecting Try Ubuntu and from the live desktop post the output from terminal of this command:

```
sudo parted -l
```

BTW that's a lower case L.

More info on downloading and burning a Live CD here, just click on the "show me how" links:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by Maxzeroedge on 2011-06-05
@jaacko , yes I mean partitions on the same hard disk.
So if I install Ubuntu in say D:, I will have to format it and when I start my PC, it will ask me Windows 7 or Ubuntu?

---

### Post by nzjethro on 2011-06-05
I followed this guide to get my dual boot up and running.

lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony

You don't need wubi (I didn't even know what wubi was when I did it). And yes, make sure you back up. I lost all my Windows data (through personal carelessness rather than the install process) when I tried. Not fun.

Good luck!

---

### Post by ILoveYorkies on 2011-06-05
Always backup just in case even if only shrinking or expanding partitions. I agree with Jaacko's advice to partition meaning shrink your Win partition with 7's disk manager. Possible data lose is why I dual boot by installing Ubuntu to flash drives. You can install to your prepartitioned  partition with just the Grub2 installed to a thumbdrive or if you can afford a 16gb or larger thumbdrive you can partition it and install all of Ubuntu to it. I've done it both ways. Here's my method, 
you could try to install to an external hard  drive ( or a flash drive  like I have done ). You partition the flash drive  with Gparted  from a  livecd or liveusb. First  while in Windows change the thumbdrive from  removeable (to write cache so you have to always use shutdown safely  like  when using an external hard drive). Then use a livecd choose try Ubuntu  not install. If it boots okay then go to apps and pick Gparted and  partition the drive giving 300mbs or less to Grub2 then you need a root  (/) partition then  a a swapfile and a /home partition. Then use disk  utility to double check which is the the dev names so you install to the  correct drive so you don't overwrite your Win partitions nor it's mbr.  Or you could install grub to a 4gb or less thumbdrive after partitioning  your main Win partition most likely c drive, shrinking it so you can  make another partition for Linux. If you do that, MAKE SURE YOU BACKUP  OR COPY ALL THE DATA YOU NEED TO KEEP! Shrinking your partition with  software for Win or using Gparted usually doesn't BUT IT CAN CORRUPT OR  ERASE DATA!  If you IMPROPERLY INSTALL GRUB YOU COULD MESS UP Windows  MBR BOOTLOADER! That's why I use flash drives and use the "other" check  box during install instead of allowing Ubuntu to choose everything. I  can then choose  the devices to partition myself.  I just use the key to pause post so I  can choose which drive to boot from, In my case I press Esc then F9 and  it lists my Grub drive named Sandisk. I have to do that every time  I  want to boot Natty but That's just the way I wanted it. If you don't then  just go into your bios uttility and move the Ubuntu drive to 1st place  then Windows drive to 2nd place then every time you power on or reboot it looks for your Grub2 drive  to boot from. In my case my Sandisk Cruzer Of course you must have the flash drive installed whenever you want to boot Ubuntu.If it doesn't find it it boots directly into Win again.But the Grub2 menu should offer Ubuntu, and  other oses ( in your case Win 7 ) plus recovery mode and memtest. So  far this method has worked for  me.. I hope this  helps.

---

### Post by Maxzeroedge on 2011-06-05
So it means, I need to have Windows installed on whole HD first, then shrink it and finally install ubuntu?

---

### Post by Mark Phelps on 2011-06-06
Not clear what your really want to do ...

If, in fact, you want Ubuntu installed to the same physical hard drive as Win7, and you do NOT want to use Wubi (right so far?), then do the following:

FIRST, use the Backup feature in Win7 to create and burn a Win7 Repair CD.  You are likely to need this later if the Win7 boot loader has problems.

THEN, open the Disk Management utility in Win7. Confirm that you have no more than three partitions.  IF you do, STOP.  If you continue with more than three partitions you run the risk of having Win7 force the conversion of your Win7 partitions -- which will cause you major grief.

Presuming you have three partitions or less, use the Disk Management utility to shrink the Win7 OS partition (the large partition, not the small one) to make room for Ubuntu.

Do NOT format the new unallocated space. Leave it as is.

Finally, boot from the Ubuntu CD and install it into the unallocated space.  Be very careful when doing this, as selecting the wrong location will erase your Win7 installation!

If this all works, when you reboot, you will boot directly into Ubuntu.  To then get access to Win7 back, open a terminal in Ubuntu and enter "sudo update-grub".  That will rewrite the default GRUB menu to add an entry for Win7.

---

