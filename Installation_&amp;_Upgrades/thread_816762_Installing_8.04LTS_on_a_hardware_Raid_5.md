---
title: "Installing 8.04LTS on a hardware Raid 5"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by Lutiana on 2008-06-03
Okay, first off if there is another thread that will answer this then please tell me and I will check it out, but I simply cannot find it.

I am trying to install Ubuntu 8.04 LTS Server Edition onto a Highpoint HPT374 hardware Raid 5 (6 disks total of 600gb of space) but when I get to the partition section of the install all I see are the individual drives. I have setup the hardware raid in the HPT374s bios. 

How do I get it to install on the entire raid and not individual disks?

Please help.

Thanks in advance

Lutiana

---

### Post by jpkotta on 2008-06-03
Use the alternate CD.  It can install to RAID arrays.

---

### Post by gmeazell on 2008-06-03
I am having the same problem but I am using RAID 1. I selected the first drive and the install happily copied files to it, but when the computer rebooted, it could not find the OS.

Alternate CD is not an option, since it is only for Desktop not Server as the OP and I are using. I am going to try to reinstall the server to see if I missed a step somewhere. In the mean time, I would like to know if there's a better solution.:confused:

---

### Post by foresto on 2008-06-03
I think the Highpoint 37x chipset is not truly a hardware RAID controller, but actually a so-called "fakeraid" chipset.  That is, little more than a plain drive controller that requires OS drivers to implement RAID.  Since those drivers are not usable by your boot loader (e.g. GRUB), I think you'll find it rather difficult to get your system booting from RAID 5 or 0 using this chipset.

I believe some folks have managed to boot a RAID 1 volume using fakeraid cards, but only because they're actually booting from one of the two mirrored drives.  The two drives don't actually become a single RAID 1 volume until after the kernel is booted and the fakeraid driver is loaded.

The usual cheap solution is to boot from a non-RAID volume to load the kernel and RAID drivers, then mount your RAID volumes afterward.  I don't know of any OS installer that makes this easy, though, and RAID protection excludes the boot volume in this arrangement.  Also, if your fakeraid driver requires entire disks (instead of partitions) for its volumes, you'll need an extra disk to boot from.

A more convenient solution is to spend the money on a true RAID controller.  I bought a 3ware card for just over $100 that handles two drives.  It works very nicely in linux, with no special drivers to mess with (they're built-in to current kernels).

Here are some relevant links:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)
[http://www.wensley.org.uk/raid](http://www.wensley.org.uk/raid)

---

### Post by Lutiana on 2008-06-03
I have done some more research on the card, and I am not entirly convinced that it is a software raid. And this is based on my experience with the card. 

But in any event I have decided to install the system on a drive outside the RAID 5, connected to the IDE header on the motherboard and then I will install the driver for the RocketRaid 454 (HPT374 Chip) and set the RAID 5 volume as my data/samba store.

One thing I did find out is that the default driver loaded by Ubuntu (the hpt366.ko) is not want I want to use for the raid 5 array, instead I want to download and compile the "open source" driver from highpoint's website.

I found this howto on the process: [http://stefan.freyr.org/?page_id=6](http://stefan.freyr.org/?page_id=6)

I'll post my results as soon as I can.

---

### Post by dstew on 2008-06-03
The Alternate Install CD has menu items to create and install to a software RAID. To install to a FakeRaid, one needs to use the Live CD, install dmraid, and hand-install the operating system, because the installer will not cooperate with dmraid. At least it was this way with Feisty and Gutsy. Does anyone know if the Hardy installer on the Live CD will install to a FakeRaid?

One way to know if you have true hardware RAID is to boot a live CD and do **fdisk -l**. If you have true hardware RAID, it will see only one disk. If it sees multiple disks, it is FakeRaid, which is software-assisted hardware RAID. I am not aware of any desktop PC with true hardware RAID. A FakeRaid controller can set up an array, but it will need the main board CPU to do the calculations for parity, and to maintain the array, especially in the case of RAID-5.

---

### Post by Lutiana on 2008-06-08
Okay, so some more feedback.

The "open source" driver from highpoint will not compile on the new kernel. Apparently there are some code changes with the new kernel so we are stuck waiting for highpoint to make new drivers (ie change their code).

On another note, the HPT374 chip is a "fake raid" hence the low cost of the card. 

I did try the redhat driver to no avail. So I am at a dead end for now.

I will post more if I learn anything new.

---

### Post by Lutiana on 2008-06-10
Okay, so I emailed Highpoint and got this response:

> 
from	Support <support@highpoint-tech.com>
to	******************
date	Tue, Jun 10, 2008 at 10:16 AM
subject	Re: RocketRAID 454 (HPT374) Driver support
	
Hello,

Updates are still planned, but a release date has not been set.

Regards,

HighPoint Technologies, Inc.
Customer Support Department

[http://www.highpoint-tech.com](http://www.highpoint-tech.com)
[http://www.hptmac.com](http://www.hptmac.com)



So I have switched to a software Raid 5. I had to disable the raid in the RR454 bios for it to work properly and then I followed this tutorial:

```

http://mywheel.net/blog/index.php/software-raid-in-ubuntu/

```

Only thing to note is his english is not very good and can be a little confusing, and when he tells you to use the cylinder size I recommend using the actually Byte size, since different manafacturers will have different cylinder counts to achieve the total size (should be typed in as +xxxxxxxK in fdisk).
 
He also uses reiserfs, but from what I gather this is not a good choice for ubuntu, but I have not played with this part too much yet.

He also does not tell you how to add the new raid to etc/fstab, but this site was very good to work out how to add it:

```

http://www.tuxfiles.org/linuxhelp/fstab.html

```

And lastly, once you have it all setup you check the partition and file system to make sure it is the right amount of space using the fs command (i have not tried it yet):

```

http://www.computerhope.com/unix/udf.htm

```

And lastly here is a page for more information on msadm
```

http://www.linuxmanpages.com/man8/mdadm.8.php

```

Hope this helps!

---

### Post by CheShA on 2008-06-10
There are 3 different types of RAID array:
- Sofware raid requires no additional hardware at all. It is set up, configured and managed at OS install time or possibly later.
- Hardware raid requires a hardware raid card. Calculations for parity, etc are done by the raid card. It is set up in the hardware raid controller and is transparent to the operating system - the OS never sees separate disks; the array is presented to the OS as a single disk. 
- So called "fake raid" uses a hardware card with a bios on it. There is usually a bios based setup utility, but the actual raiding is managed by an operating system driver.  Without the driver your operating system will see multiple drives. Calculations for parity and such are done by the CPU. This is what you have.

Fake raid on linux needs to be set up by using dmraid and requires a slightly fiddly installation of booting into a live CD then installing packages manually. 

Running dmraid -l show that your chipset is supported for RAID 0,1, 0+1 or 10. NOT raid 5, unfortunately. However, you do not need any other packages/drivers to implement dmraid array.
```

cheshacat@chesha:~$ dmraid -l 
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs

```

If you wish to set up a RAID array on your existing hardware, use this howto, it may look  intimidating but it's actaully quite easy. It's pretty much copy and paste after a while but I do recommend you read whats going on and take your time to understand it, it will be worth it in the long run:

[http://www.howtoforge.com/ubuntu_dapper_raid_system](http://www.howtoforge.com/ubuntu_dapper_raid_system)

It's for dapper and there are one or two bits that have changed for more recent versions, but if you read the comments carefully at the end, everything you need to know is there:
--------
1) "I used the package ubuntu-standard rather than ubuntu-base since this and ubuntu-minimal (which is already installed by this point) obsoletes it."

2) "During grub install the line

cp /lib/grub/$SETUP_CPU_GRUB/* /boot/grub/

fails because now the stage files are put in /usr/lib/grub/$SETUP_CPU_GRUB
"

3) "I used the package linux-generic rather than linux-$SETUP_CPU_UBUNTU since this obsoletes most of the linux kernel installs."
-------------

One other caveat is that you need to manually edit /etc/group and add your user to the "admin" group or you won't be able to admin things in gnome.

Good luck!

Edit: for what it's worth, RAID 5 pretty much sucks. Since you have 6 disks, I would consider giving the space over to a RAID 10 setup, it's well worth the difference.

---

### Post by Lutiana on 2008-06-10
Good to know. I was merely adding a large data store to an existing install. So I don't need to boot from the Raid 5. I used a stand alone 80gb to get the system up and running.

As for RAID 10 v Raid 5, I prefer 5 since it gives you the parity and the space. The RAID 10 would only be 360Gb and Raid 5 gives me 600Gb (65% more capacity, but a little less reliability). 

The data is not that important to me. I will burn DVDs of the things I really want to keep. My Window 2003 server has a 480Gb RAID 5 array and it has worked flawlessly for more than 3 years now, on a Highpoint RocketRaid 454. I had one drive go bad on me because of overheating but replaced it and carried on.

I might investigate RAID 6 though.

Thanks for the tutorial though, I may try it on one of my test machines at some point.

---

### Post by Lutiana on 2008-06-10
Actually I did some more research on DMRaid and it appears as though it will activate the BIOS setup RAID by using:

```

dmraid -ay

```

Right now I am using the RocketRaid 454 basically as an IDE controller and not a "Raid" controller (ie no RAID setup in the BIOS). Is using its BIOS and dmraid better than my setup? More reliable or better perdormance? Or is it simply in the end 2 ways of achieving the same thing?

---

