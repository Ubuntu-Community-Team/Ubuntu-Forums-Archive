---
title: "Removing Hard Drive"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by Deadheded on 2006-11-28
Here is my setup:

Primary Master IDE NTFS win2000
Primary Slave IDE NTFS 
Secondary master IDE FAT
Secondary Slave IDE DVD RW
SCSI ext3 Ubuntu

I installed Ubuntu on my SCSI drive but needed to pass things back to my Win2000 OS so I added the Secondary Master IDE drive and formated it with Ubuntu FAT.  Everything works great.

Now I need to remove the Secondary master drive but when I attempt to boot my computer I get and error when my boot loader comes up...  Something like "error 27"

How can I remove this storage drive and still boot either to Ubuntu or Win2000?

BTW I am new to linux but have been a hardware tech for many years using Windoze so I know I have got my hardware setting correct..

---

### Post by bulldog on 2006-11-28
Well GRUB counts your hard disks and if you remove one the counting isn't correct anymore.

You boot ubuntu and it's on (hd3)now if you remove a drive it is on (hd2)
So you have to correct your GRUB and your fstab because the drives listed there points to the wrong device.

Hope this makes it a little clearer for you.

---

### Post by Deadheded on 2006-11-28
Yes it does thanks... Now I have to learn GRUB..  Funny GRUB did not have any problem when I added the drive and the boot drive changed from 3 to 4

---

### Post by Deadheded on 2006-11-29
I edited the boot/grub/menu.lst and changed my linux drive from hd3,0 to hd2,0 and shut down. I removed my 3 IDE drive and restarted and got the "error 21" again.  I put the drive back in and could not load the kernel but I was able to boot with the CD and restore a backup of the menu.lst file and I'm working again.  Do I also need to edit the device.map file?  I did not worry about the fstab as my 3rd IDE drive is not listed and I manually mount that when I need it...  

TIA ... Hed...

---

### Post by gn2 on 2006-11-29
This may be useful: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

