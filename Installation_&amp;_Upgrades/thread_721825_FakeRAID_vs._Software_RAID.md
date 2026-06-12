---
title: "FakeRAID vs. Software RAID"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by tuxx on 2008-03-11
Hello,

I might seem to be missing the big picture.

I'll very soon be asembling my new server using RAID-1 on my nForce 430 chipset.

I'm almost convinced I'll be using Software RAID and hopefully it'll be done during installation.

However.. and this might the three I can't see because the wood shades... :

When using Software RAID.. how do I setup my BIOS? With RAID or just as a normal singledrive system?

PS: Linux will be the only OS so no need for dualboot etc.. only fully functonal RAID-1 from start to crash.

TIA

Best regards,
Martin

---

### Post by mrsteveman1 on 2008-03-11
With Linux softraid the bios just thinks there are multiple drives, and until Linux assembles the array at boot time, it doesn't know there is anything but multiple separate drives either. In fact, even after you setup mdraid you will still see multiple drives in the device tree and in the kernels partition table ( cat /proc/partitions ), but you will also then see a device like /dev/md0 etc, which is the assembled raid array.

Basically the bios isn't involved at all with RAID-1 using linux softraid. What you do have to keep track of is to make sure grub is installed to both disks in case one fails, otherwise the system won't boot.

---

### Post by tuxx on 2008-03-13
Hello and thank you for your reply.

Finished my installation last night and setup grub using fallback in case of a disk breaks - all works like a breeze.

My question has been answered and this thread is hereby solved.

Thanks again - such a big question for me - such a simple answer :-)

---

### Post by motin on 2008-07-16
The best guides to install by the means of software raid or fakeraid I have managed to find are:

**FakeRAID:**
Follow the following guide for RAID 0:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
...but adapt to RAID using additional comments here:
[http://samokk.is-a-geek.com/wordpress/2006/01/15/running-ubuntu-gnulinux-on-a-fakeraid1-mirroring-array/](http://samokk.is-a-geek.com/wordpress/2006/01/15/running-ubuntu-gnulinux-on-a-fakeraid1-mirroring-array/)

Interesting RAID 0 guide which I haven't tried: [http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation](http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation)

**SoftwareRAID:**
Wonderful guide:
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)
A very similar version with some updated information:
[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

The largest notable difference is that FakeRAID installation is yet not possible using any installer currently (neither gui or alternate one), and thus the FakeRAID approach demands quite a bit of expertise from the one performing the installation.

Personally, I attempted FakeRAID using the guide above but eventually ran into so many uncertanties that I had to give up before even altering the bootloader. 

SoftwareRAID however was

My main question now however is what the performance difference is between these two options? I mean, if disk I/O and error handling are say 30% better with FakeRAID, of course I'll make another attempt on installing by such means... Does anyone know the exact differences here?

Also, I believe that some FakeRAID controllers are shipped with linux drivers. OpenSUSE and Fedora installations have an option to load drivers during installation (like Windows does by means of the F6 prompt). Is there any corresponding possibility for Debian/Ubuntu and does a successfully loaded third party driver  mean that dmraid is unnecessary and the installation can be carried on as usual? That would definitely be a lot easier than manually installing everything...

A heads up on:
 - Performance differences
 - Error handling capabilities
 - Ease of installation 
between softwareraid and fakeraid would be highly appreciated!

Cheers all!

---

