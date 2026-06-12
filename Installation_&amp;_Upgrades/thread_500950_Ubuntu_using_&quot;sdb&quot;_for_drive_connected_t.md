---
title: "Ubuntu using &quot;sdb&quot; for drive connected to EIDE3 ?   Grub can't boot."
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by Raptor Ramjet on 2007-07-14
Hello,

I've just swapped out the motherboard on my computer so I could add a large sata drive for storage (the old board didn't have SATA controllers, the new one does)   However after changing the motherboard and adding the new sata drive I was unable to get the system to boot. 

So... after much experimentation with grub etc. I decided to simply reinstall from the Feisty live CD and formatted every partition except my old "/home" partition.  However I am now still unable to boot as Grub fails with "Error 17: Cannot mount selected partition".  If I go into Grub and do the following:

find /boot/grub/stage1

It returns "(hd0,0)"

I then try

root (hd0,0)
setup (hd0)

And Grub runs without an error but I still can't boot as I get the same "Error 17: Cannot mount selected partition". 

At this point I should point out that I have a slightly unusual setup as my new motherboard is a Gigabyte G7VAXP ultra which has 4 EIDE controllers (2 standard, 2 "RAIDable") and two sata controllers (also "RAIDable") on which I have the following devices attached:

EIDE1 - DVD-Rom
EIDE2 - DVD Writer
EIDE3 - Hard drive (3 partitions for "/", "/home" and "swap")
EIDE4 - Removable caddy (currently has with no disk in it)
SATA1 - 500Gb drive (to be mounted as "/data")
SATA2 - Nothing.

Something is bugging me though as when I boot using the Ubuntu live CD it picks up the sata drive as "/dev/sda" (which is what I'd expect) but it then picks up the drive on EIDE3 as being "/dev/sdb" which seems wrong to me ?  However I can mount and view the files on the disk using 

mkdir /media/test
sudo mount -t reiserfs /dev/sdb1 /media/test
nautilus /media/test

Previously the motherboard I used (ABit KT7A) also had 4 EIDE controllers and I was using exactly the same disk setup with the only difference being that I had no sata drives and there was an EIDE drive in the removable caddy.  

In this case the partitions on the drive connected to EIDE3 were correctly identified as being "/dev/hde1" (/), "/dev/hde2 (/home) and "/dev/hde3" (swap)

So I'm suspicious that my drives are not being picked up correctly and would just like some advice as to whether things sounds right ? 

Failing that any thoughts as to how to get grub installed would be most welcome too.

Finally any instructions on how to install and use lilo instead of grub would also be appreciated as I never used to have a problem with lilo (which I used to originally build the machine with "Dapper" as grub wouldn't work then either...)

Cheers.

---

### Post by Raymond Day on 2007-07-14
I came here because I trying to install Ubuntu 7.04 server on a SATA 160GB hard drive. It see it as:

SCSI3 (0,0,0) (sdb) 160.0 GB

1st it would not boot just keep on going and hearing the floppy clicking eatch time it auto rebooted. Just the BIOS start screen would come up.

So I just installed it all over again the same way. This time is hung at:

GRUB _

I am now installing it a 3rd time. I hope it will boot this time.

I even run the GRUB instaler but it never changed any thing.

-Raymond Day

---

### Post by Raymond Day on 2007-07-14
I had a 320GB IDE drive on it. So I unpluged the power to it.

I have did the install about 10 times now but it never boots. I even did a md4sum on the iso it comes back with this:

cf462501e2dc1b82b96dfc497a0404a2  ubuntu-7.04-server-i386.iso

Burned it and verifed that it was burned right.

Run check DC for defects

It says:

Intergrity test failed
The ./pool/main/p/python2.5/python2.5_2.5.1~rc1-Oubuntu3_i386.deb file failed the MD5 checksum verification. Your CD-ROM or this file may have been corruped.

<Contunue>

Can't Contue.

What could be wrong?

Is there a Internet way to install this to make sure all the data is good?

I don't think the data is bad. I guess because it's a SATA hard drive.

-Raymond Day

---

### Post by Raymond Day on 2007-07-14
Look's like it was my CD-rom drive just could not read the CD good.

I put another CD-rom drive on and it installs with no errors. But on boot the SATA drive just hangs at:

GRUB _

So I am installing it on the IDE drive. But I like to install it on the SATA drive as the boot drive. But it just will not boot from that.

-Raymond Day

---

### Post by Raymond Day on 2007-07-15
I got it working. But I had to install it on the IDE drive. It just will not boot from the SATA drive what it labled as SCSI3 (0,0,0) (sdb) 160.0 GB

The one I got it to boot from it lable

SCSI1 (0,0,0) (sda) 320.1 GB

When it boots now it shows lots of same kernels to pick to boot from. I guess because I reinstalled this about 15 times!

I had Fedora on this because back then I started with FC1 and it would boot from a SATA drive with FC1

What's wrong with ubuntu 7.04 server that it just will not boot from a SATA drive? Just come back GRUB _ and hangs.

-Raymond Day

---

