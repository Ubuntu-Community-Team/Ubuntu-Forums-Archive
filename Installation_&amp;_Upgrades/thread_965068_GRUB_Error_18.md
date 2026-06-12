---
title: "GRUB Error 18"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by ddaskey on 2008-10-31
I just created the Ubunti 8.10 Server CD this morning and installed it on my Dell PowerEdge Server 1400SC.  It said installed fine and reboot, but I get the:

GRUB Loading step1.5

GRUB loading, please wait ...
ERROR 18

I've looked in other forums and it seems it is dealing with large hard drives.  I have twp(2) 160GB Western Digital drives.  I've gone into BIOS ( version A09 ) and there isn;t an option for 'Normal' as I've seen in other posts.  It had 'Auto" ( which is what I have it set at ), and then there are some 40 'User' defined parameters ones, none of the pre-filled ones have 160GB.

System:
PowerEdge 1400SC ( I've removed the PERC3/SC ), 1GB RAM
IDE #1 CD-ROM
SCSI #1 DDS Tape Drive
IDE #2 two(2) Master and Slave 160GB HDD
SCSI #2 nothing

---

### Post by Pumalite on 2008-10-31
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
This might involve making a 200 MB /boot partition at the beginning of your installation.

---

### Post by dash86no on 2008-10-31
I have the same problem with Grub, on Kubuntu 8.10.

I just installed on a 20 GB HDD as a clean install using all the defaults for installation. I am not duel booting and elected to use the entire HDD for installation. I am running Kubuntu on a thinkpad T40. 

The installation finished without errors but when I rebooted I was greeted with the Grub error 18 message and unable to go any further.

I will try to fix now using live CD and grub utilities.

---

### Post by dash86no on 2008-10-31
Tried going through the old:

grub> find /boot/grub/stage1
grub> root (hd0,0)
grub> setup (hd0)

but it didn't fix the problem, I'm still getting error 18 from Grub.

I was in the live CD, and man KDE looks beautiful. I was really looking forward to using Kubuntu after having a really positive experience with Mandriva 2009 (If you haven't tried it check it out - an awesome OS) 

I'm too tired to troubleshoot now. I hope I have a better experience upgrading my main box to Ubuntu 8.10 tomorrow. If anyone has any ideas on how to fix this issue with my Kubuntu box please let me know. 

Cheers

---

### Post by caljohnsmith on 2008-10-31
Dash86no, are you getting the Grub error 18 before seeing a Grub menu (or before seeing "press ESC to see menu"), or do you get the error when selecting Ubuntu from the Grub menu? Also, how about posting:
```
sudo fdisk -lu
```

---

### Post by ddaskey on 2008-10-31
I am not getting a menu, prompt or anything.

---

### Post by caljohnsmith on 2008-10-31
Ddaskey, did you see Pumalite's advice? Creating a /boot partition at the beginning of your HDD will probably fix your problem. If that doesn't work, then please post:
```
sudo fdisk -l
```
And we can work from there.

---

### Post by Pumalite on 2008-10-31
> **ddaskey said:**
> I am not getting a menu, prompt or anything.
Try:
Ctrl+Alt+F1 (2,3,4,5,6)

---

### Post by ddaskey on 2008-10-31
I checked and the BIOS, A09, is the latest.  I am now trying to make the boot partitiion as suggested ...

---

### Post by dash86no on 2008-10-31
> **caljohnsmith said:**
> Dash86no, are you getting the Grub error 18 before seeing a Grub menu (or before seeing "press ESC to see menu"), or do you get the error when selecting Ubuntu from the Grub menu? Also, how about posting:
```
sudo fdisk -lu
```

I get the message at the same point as ddaskey:

GRUB Loading step1.5
 
 GRUB loading, please wait ...
 ERROR 18

I post the output of sudo fdisk -lu below:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b18164f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74846834    37423386   83  Linux
/dev/sda2        74846835    78140159     1646662+   5  Extended
/dev/sda5        74846898    78140159     1646631   82  Linux swap / Solaris


Man, I was tired last night, this drive is 40GB, not 20. 

Im thinking of using gparted (or qtparted on KDE, right?) to create a boot partition on the first 1024 cylinders to see if that will fix things. Its a little strange though, as ive had Ubuntu 7.10 and 8.4 on this machine and never experienced this problem before using the defaults.

---

### Post by caljohnsmith on 2008-10-31
Dash86no, how about posting the following from your Live CD before you reinstall or repartition:
```
sudo grub
grub> root (hd0,0)
grub> blocklist /boot/grub/stage2
grub> blocklist /boot/grub/menu.lst
grub> quit
```
That could give some clues as to your problem.

---

### Post by dash86no on 2008-10-31
> **caljohnsmith said:**
> Dash86no, how about posting the following from your Live CD before you reinstall or repartition:
```
sudo grub
grub> root (hd0,0)
grub> blocklist /boot/grub/stage2
grub> blocklist /boot/grub/menu.lst
grub> quit
```
That could give some clues as to your problem.

Ah, too late, already reinstalled. 

The good news is the problem (for me) is solved. I did the following:

1. Elected to reinstall
2. Elected to manually partition the disk
3. Partitioned as follows:

primary partition, 100mb, mount point = /boot
primary partition, 38GB, mount point = / 
extended partition, 2gb, swap

4 completed installation process.

5 rebooted and grub came up and loaded up the kernel no problem. 

Thanks for your help everyone. To anyone who is experiencing the same problem: Kubuntu 8.10 is sweet, it's worth the effort to reinstall!

edit: the values above (100mb/38gb/2gb) are dependent on the size of your HDD. Mine was 40GB so I choose to use 2GB swap, 100mb for the /boot and everything else for root. I choose these values because I believe 100mb should be sufficient for a /boot partition, and because I have 2 GB RAM memory so I elected to have the same amount of swap. Just though i'd add that in case it helps anybody out.

---

### Post by C.S.Cameron on 2008-11-01
I got Boot error 18.
I think it is due to BIOS not seeing partitions larger than 32 GB.
I ran gparted Live CD, reduced the Windows partition to 15 GB.
Then I reduced the Ubuntu partition to 15 GB and moved it to the left.
Then moved swap to left and closed the extended partition.
Ubuntu booted fine as default and Windows booted fine at the grub menu.

---

### Post by ddaskey on 2008-11-03
I am so frustrated.  I tried the partition thingy and got the same message, so I had a 40GB WD drive.  I made that one the master and again, installed fine.  I then went to reboot, and now I get the message:

Boot from(hd0,0 ext3)  <<long hex number>>
Starting up ...
[   0.74000] ..MP-BIOS  bug: 8254 timer not connected to IO-APIC
Loading, please wait...
Gave up waiting for root device  Common problems:

...

ALERT! /dev/disk/by-uuid/<< long hex number, same as above >> does not exist.  Dropping to a shell.

BusyBox...

(initramfs)

---

### Post by Pumalite on 2008-11-03
Post your specs (memory, graphics) and tell me what iso you are using.

---

### Post by ddaskey on 2008-11-03
Sorry, I thought I had done that earlier in the thread..

Dell Poweredge 1400, A09 BIOS
PIII Xeon
1GB RAM
IDE#1  CD-ROM
SCSI#1  DDS Tape Drive
IDE#2  40GB WD Master, 160GB WD Slave
SCSI#2  nothing

8.10 Server  ISO

---

### Post by Pumalite on 2008-11-03
You are right. I mistake your name with that of the other poster. Have you tried a all the advice given?

---

### Post by ddaskey on 2008-11-03
The original error dealt wuth the GRUB error.  In order to fix that, I had to create a partitiion which I did; however, I now get this new error, even when I use just a 40GB master HD, so to answer your question, yes.

Could this be because the hard drives are connected to IDE#2 ( secondary ) instead of IDE#1 ( primary )?

---

### Post by Pumalite on 2008-11-03
Not only that; it could be a matter of 40 or 80 lead cables.

---

### Post by ddaskey on 2008-11-03
Wow, that is above me head.  What exactly does that mean?

---

### Post by Pumalite on 2008-11-03
Check IDE cables with your local supplier. Old computers tend to have 40 lead cables.

---

### Post by ddaskey on 2008-11-03
I guess I am confused -- I went and got what I thought was a standard ribbon IDE cable?  Is there more to it than that?  The server is some six years old.

---

### Post by Pumalite on 2008-11-03
[http://www.pcguide.com/ref/hdd/if/ide/confCable80-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCable80-c.html)

---

