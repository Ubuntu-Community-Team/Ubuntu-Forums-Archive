---
title: "Preparing USB Memory Stick for Booting 12.04"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by walt11 on 2012-05-16
I've been following the instructions "Preparing Files for USB Memory Stick Booting" in the Ubuntu Official Documentation for 12.04, and I'm using the "Copying the files — the flexible way" method.

I've prepared the memory stick as per instructions, booted from it OK, and the installation begins. When it gets to the step of looking for an installer ISO image, it finds my downloaded file ubuntu-12.04-desktop-i386.iso, accepts it, and attempts to read it. I get the error message:

There was a problem reading data from the CD-ROM ...

Retrys do not help. I know this is a good file because I've used it to burn a CD, and booted with that CD. I tried saving error logs, but that step failed also.

Any suggestions on how to proceed?  Thanks.

---

### Post by mörgæs on 2012-05-17
Have you tried creating the USB stick with Unetbootin?

---

### Post by walt11 on 2012-05-17
Thank you! Unetbootin looks like just what I need.

---

### Post by mörgæs on 2012-05-17
Good. If it worked please mark the thread 'solved'.

---

### Post by walt11 on 2012-05-17
Unetbootin created the USB stick with no apparent problems, but when I tried to boot from it, all I got was "Boot error". I tried using install-mbr on it, but still got the boot error. Then I tried using Boot Repair, which reported that it had successfully repaired the MBR, but still get the boot error. Not sure how to proceed from here.

---

### Post by mörgæs on 2012-05-17
Please give a complete hardware description.

---

### Post by efflandt on 2012-05-17
If you can boot the install CD to a live system, does **Startup Disk Creator** from that make a bootable USB stick?  If you use the option in Startup Disk Creator to format it, make sure you format the partition and not the device (for example, format /dev/sdb1 not /dev/sdb).

If you formatted the entire device (instead of partition) or wrote an iso directly to the device, you can use gparted to create an msdos partition table and FAT32 partition.

---

### Post by walt11 on 2012-05-17
Thank you both for your replies. Here is the information mörgæs requested. And I'll also try the Startup Disk Creator approach.

I had Boot Repair create a Bootinfo Summary, which is at [http://paste.ubuntu.com/993376/](http://paste.ubuntu.com/993376/)

The computer is an eMacines 6520T with an AMD Athlon 64 Processor 3400+, 1.8 GiB of memory, hard drive (sda in the bootinfo summary) is 200 GB, partitioned into sda1 which contains Windows XP SP3, and sda2, a small restore partition. Graphics card is Gallium 0.4 on ATI RS480.

My Ubuntu 12.04 is on an iomega portable drive (sdh). Ubuntu is in sdh5, and sdh6 is the swap partition. This is the system which was running when the bootable memory stick was created. The ISO image I used was a downloaded ubuntu-12.04-desktop-i386.iso

The memory stick itself (sdc) is an 8 GB SanDisk Cruzer (not U3). sdc1 contains the bootable sytem (I allowed 2 GB for persistent files). I cleared everything off before running Unetbootin. GParted currently reports this information about it:

    Size: 7.45 GiB
    Partition table: msdos
    Heads: 255
    Sectors/track: 63
    Cylinders: 973
    Total sectors: 15633408
    Sector size: 512

For partition sdc1 it reports:
    File System: fat32
    Size: 7.45 GiB
    Used: 2.71 GiB
    Unused: 4.75 GiB
    Flags: boot

I appreciate your looking at it at this level of detail. Thanks!

---

### Post by walt11 on 2012-05-17
Am I correct in understanding that the bootable USB stick which is created will function like the live CD; i.e., it will ask whether I want to try the system or install it? Because my ultimate goal would be to install it, on a 16 GB USB stick I have. Is that a realistic expectation?

---

### Post by oldfred on 2012-05-18
I have a full install of 12.04 in my 16GB flash drive in a 8GB / (root) with the rest just as data. It is functional but not speedy as USB ports are slower than hard drives and flash is slow (particularly writes). But you can change some settings (Similar to SSD) to reduce writes.

Full install is just like any install to another drive. Best to partition in advance and use manual install. Only with manual install (Something Else) do you get the choice to install the grub2 boot loader to the MBR of the flash drive. It normally just defaults to sda with any of the auto installs.

Install instructions have not changed hardly at all between versions. New Unity is a lot different once installed.

The lighter weight versions may work better as they do not have as large of programs to load.

Installs to 4GB flash, newer of Ubuntu versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

My first install from one USB to another USB did have an issue which may not be one now. Grub searches by UUID if drive is not correct and when I unplugged one USB the other one changed drive. But grub stopped searching on UUID since there was a gap in device number. I had to use e change hdX to correct X and delete the search to get it to boot first time.

---

### Post by walt11 on 2012-05-18
Thanks for all the good advice, and links. (And special thanks for the warning about using the manual install. You remember how much trouble I had taking Grub *off* sda!)

It will take me a while to digest all the information, but I'll be back with questions. (I always seem to have them.)

---

### Post by walt11 on 2012-05-19
Yet once more you have helped me to a solution! Thanks again. All went well, and I now have a bootable flash drive with 12.04 installed.

The only issue is that I'm experiencing *very* slow downloads. (I installed updates - many, and it took several hours.) I was connected via Ethernet cable, and it is normally quite fast. I tried booting the flash drive from my faster laptop, which is connected by wireless, and the downloads were still slow. The system on the flash drive is surprisingly fast. It's only the downloads which are so slow.

The light on my router flashes for a few seconds, then stops, and that behavior is repeated constantly, so the throughput is quite low. Could it be some kind of buffering issue? The laptop downloads very fast when I boot it into Windows 7. And the Ethernet connection, where I normally use Ubuntu on the external drive has always been fast (but, not sure about today).

In any case, I now have a working system on flash drive, which was my goal. Nevertheless, I'm still going to try to get a bootable flash drive to use as an installer. I intend to try the Startup Disk Creator method which was suggested, and I''m still perplexed about why the drive I created using Unetbootin won't boot.

---

### Post by mörgæs on 2012-05-20
Have you tried to change download mirror?

---

### Post by oldfred on 2012-05-20
Anything that has to do a lot of writes to the flash drive will be slow.

All Ubuntu/ Canonical have been slow recently. Seems better today. I always change to a more local download mirror as mörgæs suggests and change for all updates once installed.

I install a different way. A bit more advanced as you have to directly edit grub.cfg, but really just have to copy some entries. I loopmount the ISO using grub2, so then it is just a copy of the ISO.

On my flash drive, I have a data partition and use that to store ISO. But then you have to edit path to find ISO.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by walt11 on 2012-05-20
I didn't know that you could choose a mirror when downloading software. Thanks to both of you for mentioning it. (Found the place in the Software Center where you can choose "Select Best Server", and I suppose one should do that each time before downloading.)

Thanks for the information and links to MultiBoot USB with Grub2. I'll look at them, but I confess to nervousness about anything that involves working with Grub. With your help, have finally got Grub doing what I want it to, and I'm inclined to leave well enough alone.

---

### Post by mörgæs on 2012-05-20
> **walt11 said:**
> ... choose "Select Best Server", and I suppose one should do that each time before downloading.



No, just do it once. The ranking among mirrors seldom change (except for the last couple of days, where there has been some delay).

---

### Post by walt11 on 2012-05-20
Thanks. That saves a lot of unnecessary effort.

---

### Post by walt11 on 2012-05-28
The 12.04 system on my flash drive is running so well that I replaced my older, multiple-times, upgraded system on my external drive with it, freeing up substantial space for data as well. Thanks again for all the help.

I appreciate the information on booting LiveCD ISOs from flash drive or hard drive, but that seems rather complex for me, and right now I'm happy with what I have. I'm going to mark this thread as solved.

---

