---
title: "Sata2 detected after upgrade, ubuntu now on sdb?"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by ting on 2006-06-16
The problem:
I have an asrock dual sata2 motherboard. The sata 2 interface has finally been detected after the latest kernel upgrade. This detection means that ubuntu which previosly resided on sda has been moved to sdb. Wich leaves me with an unbootable installation.

The boot splash stops on waiting for root filesystem.

If I edit the grub menu before booting and instruct it to boot from sdb5 instead of sda5, I get all the way to Checking All Filesystems. Then I go to the command line, where it says No susch file or directory for sda6, sda7 etc. I can now type exit and continue on booting into ubuntu. Though i can't log in since I have a seperate /Home partition.

To make a long story short: Newly detected drive is placed as sda. The drive Ubuntu lies on is now called sdb. Ubuntu no like:? 


Questions:
- How do I get ubuntu to understand the new situation?
- If i reinstall ubuntu, will the sata2 driver be downloaded from the net before the partitioner starts so I can avoid these problems?


Notes:
The problem is caused by inclusion of a driver from the 2.6.16 kernel. Which is good news.
I have tried to install the 2.6.16 kernel before with the exact same problem. In trying to fix the problem I edited the grub menu.lst and /etc/fstab. However I was left unable to mount the other drives, and the exit to prompt from bootsplash mentioned above.

My set up is as follows
sataII: 250 gb ntfs
sata nr. 1: 74gb with several partiotions
		winxp
		winxp64
		ubuntu
		ubuntu home partition
		some more partitions
sata nr. 2: 250 gb ntfs


fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda7       /media/sda7     ext3    defaults        0       2
/dev/sda8       /media/sda8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda9       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



device.map
> (hd0)	/dev/sda
(hd1)	/dev/sdb


part of grubs menu.lst
> title		Ubuntu, kernel 2.6.15-25-k7
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-25-k7 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-k7 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-25-k7 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.15-25-k7
boot

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

---

### Post by Paulus on 2006-06-19
Hey thanks for making this thread!

After reading that the driver for the SATA2 controller has been included in the latest update, I decided to give it a try,  and low and behold it worked!

All I did was swap the cable over to the sata2 plug and enabled it in my bios.  I additionally disabled the old SATA1 controller, since my other drive is standard ATA.  The drive is still detected as 
/dev/sda

and everything is working as per normal.  The only niggle is I had to modify my xorg.conf file again to include my monitors resolution, since it was reset automatically.

So just reporting sucess, sorry I can't help.  perhaps you should try disabling the existing SATA1 interface like I did and give it a go.

p.s there is no noticable performance increase as expected, so this is not totally essential i guess. 8)

---

### Post by ting on 2006-06-21
Good to hear you got it working.O:) 

Iwe contemplated doing something like this, but I was hoping for a quick fix like sudo update something. But guess not. Well at least the driver is in there. Due to the world cup, my tinkering has been severly reduced lately:-\"  If I do find a fix i'll be shure to post it here.

---

### Post by sdyson on 2006-07-13
I had a problem that seems pretty similar to this. I initially had a single SATA drive with Ubuntu installed on it and just bought a new SATA drive to replace an old IDE drive with my music on it. 

Before the new drive was formatted I could get to the GRUB menu but couldn't boot because the new drive was being assigned sda instead of sdb. I managed to modify the grub menu.lst to boot from sdb (and modify my fstab to mount my home partition from sdb) which got me running again but once the new drive was formatted I couldn't even get GRUB to load (Error 22). 

Some fiddling later I've discovered that switching the sata connectors on the motherbaord solved the problem. It makes no sense because I had my boot drive connected to SATA1 and my new drive to SATA4. They showed up as 1 and 4 in the BIOS as well. But once I put my boot drive on SATA4 and my new drive on SATA1 my boot drive was correctly assigned sda and everything worked well. 

Hopefully this solution will help others suffering the same problem.

---

