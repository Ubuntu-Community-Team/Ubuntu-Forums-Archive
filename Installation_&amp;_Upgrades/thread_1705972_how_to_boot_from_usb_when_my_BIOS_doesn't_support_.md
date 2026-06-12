---
title: "how to boot from usb when my BIOS doesn't support it ?"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by meTroubled on 2011-03-13
i just downloaded Ubuntu10.10,i used to burn the .iso file to a cd and then boot using the CD. recently my cd/dvd writer crashed and i was wondering could i boot from my pen drive in such cases,i also prepared a bootable pen drive but in my BIOS settings there is no option visble for such booting. please help.

---

### Post by Dutch70 on 2011-03-13
Welcome to UF

Have you tried hitting the "esc" button when your pc is loading?

---

### Post by Mark Phelps on 2011-03-14
> **brain.tp@gmail.com said:**
> i just downloaded Ubuntu10.10,i used to burn the .iso file to a cd and then boot using the CD. recently my cd/dvd writer crashed and i was wondering could i boot from my pen drive in such cases,i also prepared a bootable pen drive but in my BIOS settings there is no option visble for such booting. please help.

Sorry, but if your BIOS does not provide an option for booting from USB, there's no way to add that -- short of a BIOS update.

---

### Post by lkraemer on 2011-03-15
You didn't mention if you had a Floppy drive or not, but if you do
it is possible to start the boot process and then transfer the booting
to a USB Flash Drive with Boot-it.  I've used it to boot from Floppy,
then start DSL (Damn Small Linux) on my older Compaq 1672 Laptop that
didn't have USB as a Boot Option.  It worked Great.  I don't remember
which Version I was using, and that old Laptop isn't with me at the
moment, as I'm out of state.  This was a version of Boot-It prior to
the BootIt-NG (BING) that they have out now.  I've got specific
setup information and a Flash Drive with that old Laptop.

Here is a bit of detail from Fri 02/29/08 06:31 PM:
Dear Sir:
I purchased BootitNG a year ago or so, and now I am getting ready to make use of it.
I need your help in solving the steps to make my computer fully functional when I am
done.  (Previously I used a floppy BootitNG disk to boot my Damn Small Linux (DSL)
to Flash drive installed DSL.  That worked fine since I didn't have the option to boot
from a USB Flash Drive.)
 
I have searched the FAQ and the Knowledge Base and I really haven't found much on
how to do this.
 
I have copied my drive to a 320G Maxtor STM32206020A IDE drive to allow me to test
the results.
 
My Drive has the following:
 
1.  First Partition - 14.3Gig FAT32 Win98 (Dual Boot with WinXP in an EXTENDED Partition))
2.  Second Partition - EXTENDED 63.8Gig NTFS (WinXP Partition)
3.  Lots of unallocated space.  (See enclosed jpg.)
 
I would like to do the following:  (without having to totally rebuild my XP machine)
 
1.  COMPLETELY REMOVE the Win98SE Partition, and stay with the Four Partition Limit.
2.  MOVE/SLIDE the WinXP Partition to the beginning of the Drive, then EXPAND it to 80Gig,
     and still have it BOOT UP on XP (and also Ubuntu ver 7.10  -- Linux)!
     Note: I would really like to have this partition not be EXTENDED, and would rather
              it be just a normal Partition.........if possible.
3.  Create 3 more Partitions (/ROOT /HOME /Linux-Swap) to install Ubuntu.
     (Ubuntu will install GRUB when it is installed.  Will this be a problem?)
 
That would give me Four Total Partitions.
1.  WinXP - Bootable 80Gig NTFS Partition
2.  Ubuntu 7.10 using /ROOT /HOME /Linux-Swap - Bootable  ( I can handle the Linux part
     as long as GRUB doesn't impact BootitNG.)
 
I have tried several times without using BootitNG and I haven't had any luck in getting
Win XP to boot.
 
Can you email me some detailed directions of what is needed to get this done with BootitNG.......
if it is possible!!!!!!
 
Thanks.

[http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm)


**Here is another method I used:**
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=17;t=20721](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=17;t=20721)


lk

---

### Post by Hakunka-Matata on 2011-03-15
[https://help.ubuntu.com/community/MountIso#Mounting%20ISO%20Files]("https://help.ubuntu.com/community/MountIso#Mounting%20ISO%20Files")

You can install from an .iso (.iso file stored in a folder on HD - and subsequently mounted from that folder into a /mnt/, /media/ or other /custom/ folder)  mounted on your hard drive.  see above url to figure that part out.

Installing your Ubuntu10.10.iso to the same hard drive can then be done, albeit with instructions I cannot give you at the moment, because I don't have the procedure completely clear in my own mind yet.  But I've done it a number of times.  Maybe someone else can explain that part clearly.  

You do have the potential problem of not being able to boot to a live CD, and not being able to use your Hard drive mounted .iso file as a Live CD if you get the drive into an unbootable state.

---

### Post by lkraemer on 2011-03-15
If you just wish to Mount an ISO and access it, that is as simple as:
Assume I want to mount my Quicken.ISO, I just make a mount point,
mount the ISO, do what I need, then umount the ISO.......

```

cd /
cd /mnt
mkdir cddisk
cd ~
cd Downloads/Windows_Software/ISO\'s/Quicken-2004-ISO/
mount -o loop qw04dlxr3b.iso /mnt/cddisk

```

```

umount /mnt/cddisk
cd /
cd /mnt
rmdir ccdisk
exit

```

lk

---

### Post by fyfe54 on 2011-03-15
> **brain.tp@gmail.com said:**
> i just downloaded Ubuntu10.10,i used to burn the .iso file to a cd and then boot using the CD. recently my cd/dvd writer crashed and i was wondering could i boot from my pen drive in such cases,i also prepared a bootable pen drive but in my BIOS settings there is no option visble for such booting. please help.

You could look at this:

[http://www.linuxplanet.com/linuxplanet/reviews/7319/1/](http://www.linuxplanet.com/linuxplanet/reviews/7319/1/)  

Dave

---

### Post by Hakunka-Matata on 2011-03-15
@ lkraemer:  Agreed, mounting an iso is super simple with that method.  My problem is/was, once a let's say Ubuntu10.10 Desktop 32 bit, OS iso is mounted that way, what is the method to start the installation?  

I'm guessing post #7 may be the answer.  That would be the best of both worlds, thanks

---

### Post by drs305 on 2011-03-15
> **Hakunka-Matata said:**
> @ lkraemer:  Agreed, mounting an iso is super simple with that method.  My problem is/was, once a let's say Ubuntu10.10 Desktop 32 bit, OS iso is mounted that way, what is the method to start the installation?  

I'm guessing post #7 may be the answer.  That would be the best of both worlds, thanks

This may help - it's a guide on how to install Ubuntu after booting an ISO on a hard drive:
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

---

