---
title: "Help - Ubuntu Server - ALERT! /dev/mapper/xxxx-vg-root does not exist"
date: 2015-10-27
forum: Installation &amp; Upgrades
---

### Post by laddj on 2015-10-27
Hi 
This is my first post.

I would consider myself a bit of a novice in both computing and Ubuntu although I regularly deal with various IT issues at work (Windows) and have been running Ubuntu on my pc at home for about 6 months or more. So please be gentle and you might have to spell things out quite simply, under the assumption that I know absolutely nothing.

My problem is this:

I have managed to get my hands on an old server and am now looking to install Ubuntu Server 14.04.3 LTS on it. The server consists of the following:

SCSI1 -  262 MB ATA PQO IDE SECURED (which seems to be some internal hardware that I can't seem to locate)
and 
SCSI3 - 4.0 TB 3ware Logical Disk (consisting of 12x 400GB HDDs - not sure why the 3ware only recognizes 4TB and not 4.7TB).


Everything appears to install fine, including grub, and then when it re-boots it gives me the choice of how to boot Ubuntu. But once I try to boot it, it comes up with reams of text which finishes with:

[B]"Gave up waiting for root device.
....
ALERT! /dev/mapper/xxxxxx--vg-root does not exist. Dropping to a shell!"[/B]

I have tried various things over the last 4 days and have managed to solve one error while creating another etc etc. So I've re-installed everything and am hoping to start properly from the beginning with some assistance.
I haven't figured out yet how to get logs or screen prints or anything from the server, so I am having to type everything out.

I've managed to boot into Rescue Mode from the CD (Rescue broken system) and taken a shot of the partition table in case this is of any help:

[https://www.dropbox.com/s/kmplpip4id4bw8l/IMG_20151027_134116719.jpg?dl=0](https://www.dropbox.com/s/kmplpip4id4bw8l/IMG_20151027_134116719.jpg?dl=0)
(not sure why LV-root no longer appears as '/'. It did during the install. The pic is in Rescue Mode)
I'm tearing my hair out. I have read so many posts and topics about all sorts of issues but none of the suggested solutions seem to fix my problem (or more likely, I'm applying the solution in the wrong way).

From what I gather, the problem is that the system is trying to boot from sda, even though the system is on sdb. But I don't know how to point it to the correct partition.

I'll post a few other details which no doubt will get asked (judging by the first things people ask on other posts). Hopefully this will help.

fdisk -l:
[https://www.dropbox.com/s/9dvmox4ffrl0ixx/IMG_20151027_133340468.jpg?dl=0](https://www.dropbox.com/s/9dvmox4ffrl0ixx/IMG_20151027_133340468.jpg?dl=0)

gparted partition info:
[https://www.dropbox.com/s/ayjyxmp6hk51or9/IMG_20151027_133805660.jpg?dl=0](https://www.dropbox.com/s/ayjyxmp6hk51or9/IMG_20151027_133805660.jpg?dl=0)

blkid
[https://www.dropbox.com/s/5rylt01hvsn4k2v/IMG_20151027_133200169_HDR.jpg?dl=0](https://www.dropbox.com/s/5rylt01hvsn4k2v/IMG_20151027_133200169_HDR.jpg?dl=0)

I also get this error when booting Live CD:
[https://www.dropbox.com/s/3p07smgs2rzwnwg/IMG_20151027_132737200.jpg?dl=0](https://www.dropbox.com/s/3p07smgs2rzwnwg/IMG_20151027_132737200.jpg?dl=0)


Any help is HUGELY appreciated.

---

### Post by TheFu on 2015-10-27
Setup ssh-server and use a different PC to ssh into the machine.  Then you can copy/paste the text including both the  command and the output back here.

That only helps if you can get networking up.
For local stuff, use the 'tee' command to redirect output to a log file.
For example:
```
$ lsblk | tee /tmp/lsblk.log
```
```
$ sudo parted  -l | tee /tmp/parted.log
```

Then just copy these log files off to a usb  drive and post the RELEVANT parts here.
Simple?

Or you could use curl to post the text output to a pastbin-clone.
```
$ cat file.txt | curl -F 'sprunge=<-' http://sprunge.us
```

Text is much easier to work with than images.

I wrote a little script that gathers minimal system info:  [http://blog.jdpfu.com/files/quick-sys-info.sh](http://blog.jdpfu.com/files/quick-sys-info.sh) It posts the output automatically to sprunge, assuming there is a network connection.

---

### Post by laddj on 2015-10-27
Thanks for your reply.

Good to know. That's really useful.

Here is the output:

lsblk.log

```
NAME                           MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
fd0                              2:0    1     4K  0 disk 
sda                              8:0    0   250M  0 disk 
&#9492;&#9472;sda1                           8:1    0     1M  0 part 
sdb                              8:16   0   3.7T  0 disk 
&#9500;&#9472;sdb1                           8:17   0     1M  0 part 
&#9500;&#9472;sdb2                           8:18   0   244M  0 part /boot
&#9492;&#9472;sdb3                           8:19   0   3.7T  0 part 
  &#9500;&#9472;mediasrv--vg-root (dm-0)   252:0    0   884M  0 lvm  /
  &#9492;&#9472;mediasrv--vg-swap_1 (dm-1) 252:1    0  1020M  0 lvm  
sdc                              8:32   1   960M  0 disk 
&#9492;&#9472;sdc1                           8:33   1   959M  0 part 
sr0                             11:0    1   574M  0 rom  
sr1                             11:1    1  1024M  0 rom
```

parted.log (I've taken out the USB stick used for copying the file and the Disk I'm running Rescue Mode from to shorten the output.)

```

Model: ATA PQI IDE Secured (scsi)
Disk /dev/sda: 262MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2097kB  1049kB  primary  ext2         boot, raid


Model: 3ware Logical Disk 00 (scsi)
Disk /dev/sdb: 4000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  258MB   256MB   ext2               boot
 3      258MB   4000GB  4000GB                     lvm

...removed USB...


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/mediasrv--vg-swap_1: 1070MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  1070MB  1070MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/mediasrv--vg-root: 927MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  927MB  927MB  ext4


...removed CD-rom....
```

---

### Post by TheFu on 2015-10-27
Lots of guessing below.
The PQI IDE device is probably a CF card. It is meant to be read from, not written.  This is generally used for a hypervisor or dedicated router-type device where all variable data is stored elsewhere. 250MB is too small to load a stock ubuntu server, so this device isn't really useful for the OS.  You can install the /boot onto it, which is what I would do.  ext2 is fine for that area.  Don't let it fill up or you'll be in a world of hurt. Be diligent about cleaning up old kernels - keep only 2-3 of them and it should be fine. Much more than that and you could break the system so it won't boot any more.  There are lots of posts in these forums about that.

To use LVM, and you should, you must have a separate /boot, so far, so good.

The 3ware stuff appears to be recognized. If you didn't specifically install drivers, that is impressive.  3ware is a highly reputable HW-RAID vendor. They were bought by LSI a few years ago - another reputable RAID vendor.  You most likely have solid, fast, HW-RAID. That can be great or terrible (if it breaks).  In a business, having a spare RAID controller or 4-hour vendor replacement contract mitigates the issues with HW-RAID failure.  Of course, you'll need a separate backup location - a 4T USB drive would be fine.

As you see from the lsblk cmd, there are 2 LVs on the disks. The sizes seem a little small.  I'd make the root LV 20-25G in size, have a home LV of whatever is comfortable for your needs - 10-50G and I'd leave the rest unallocated, but part of both the PV and VG to make it easier to extend or create more LVs for other purposes.  For example, if this will be a media server, I'd probably create a "Data" LV.  Think of LVs as partitions, just extremely flexible partitions that can be resized up or down while online (if ext4 is the file system). Then you can mount partitions where ever you like ... 
root ---> /
home --> /home
Data --> /Data

Use lvs, vgs, pvs to see the details of these different LVM entities. These require sudo to work. There's an LVM how-to that can't hurt to read over at HowToForge.com. You'll find it easily.

Ok, so armed with a little more information, we can try to tackle the real issue ... Please post the /etc/fstab and the output from **sudo blkid** ... we should see 4 lines (or more) in the fstab. One mounting /boot from sda and the others referencing the LVs for root, home, and swap.

Make sense?

---

### Post by laddj on 2015-10-27
Interesting insight. Thank you.

I am planning to use the server as a media server. Backups shouldn't be that big of a problem because I mainly plan on putting all my optical data on it. So everything should be backed up in that way. As & when I add more data, I will give closer consideration to backups.

I was intending to ignore the PQI IDE altogether. But as the system only seems to find that whenever I boot at the moment, I thought I might try to use this drive for a biosgrub. Not sure how wise that is or if it is required, but it's something I came across in all the reading I did to try to solve my problem.

I'm afraid I'm not up on all the acronyms yet. I'm assume:
LV - logical volume
PV - physical volume
VG - volume group
I'm guessing this will all make more sense once I read my homework ;)

Right, to the output you asked for:


blkid.log
```

/dev/sda1: UUID="d5821849-fa36-4642-91b1-b611d063a316" TYPE="ext2" 
/dev/sr0: LABEL="Ubuntu-Server 14.04.3 LTS amd64" TYPE="iso9660" 
/dev/sdc2: UUID="578ea5c7-b593-4dc7-8331-ea8744736eca" TYPE="ext2" 
/dev/sdc3: UUID="MvpElL-goDM-283Q-0WNZ-L9aT-HqJY-8R517f" TYPE="LVM2_member" 
/dev/mapper/mediasrv--vg-root: UUID="1a5019ac-fda2-475e-b629-2c28d0cd8594" TYPE="ext4" 
/dev/mapper/mediasrv--vg-swap_1: UUID="f1bc5239-8511-4648-886e-22e3ae0a1cd1" TYPE="swap" 
/dev/sdb1: UUID="4AE0100BE010003D" TYPE="ntfs" 
```

fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/mediasrv--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb2 during installation
UUID=578ea5c7-b593-4dc7-8331-ea8744736eca /boot           ext2    defaults        0       2
/dev/mapper/mediasrv--vg-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```


edit:
I just noticed that the numbering of the /dev/ has changed after using a different USB to copy across the files. So I've run another lsblk to update things:

```
NAME                           MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
fd0                              2:0    1     4K  0 disk 
sda                              8:0    0   250M  0 disk 
&#9492;&#9472;sda1                           8:1    0     1M  0 part 
sdb                              8:16   1   1.8G  0 disk 
&#9492;&#9472;sdb1                           8:17   1   1.8G  0 part /media/usb
sdc                              8:32   0   3.7T  0 disk 
&#9500;&#9472;sdc1                           8:33   0     1M  0 part 
&#9500;&#9472;sdc2                           8:34   0   244M  0 part /boot
&#9492;&#9472;sdc3                           8:35   0   3.7T  0 part 
  &#9500;&#9472;mediasrv--vg-root (dm-0)   252:0    0   884M  0 lvm  /
  &#9492;&#9472;mediasrv--vg-swap_1 (dm-1) 252:1    0  1020M  0 lvm  
sr0                             11:0    1   574M  0 rom
```

end of edit

---

### Post by TheFu on 2015-10-28
When you boot without a flash drive, no LV is being seen?

Is any partition on the sdc or lvm seen?  If not, that would imply that the boot image doesn't have drivers for the 3ware controller. That would be my troubleshooting direction. It isn't uncommon for the installer to have more drivers than what gets installed - at least that has been my experience with network card drivers.  The installer has what my machine needs, but doesn't actually install them. Don't know why.

---

### Post by laddj on 2015-10-28
I'm away from the server at the moment so will not be able to try/check much until I get home this evening.

When you say 'boot', do you mean the initialising that the server does once I press the power button, or the bit after I select Ubuntu to boot?

From videos that I took of the boot sequence, I get the following output (I'm not sure there is a way of capturing this without photos or typing it all out, so here it goes):

First screen
```
Waiting for 3ware Controller to Initialize...
```

Second screen
```
3ware ATA RAID Controller: Escalade 9500S-12
BIOS: BE9X 2.03.01.047 Firmware: FE9X 2.04.00.005
BBU Status: Not Present
Unit 0 -      64K RAID 5         3.63 TB
  Port 0 - ST3400832AS      372.61 GB
  Port 1 - ST3400832AS      372.61 GB
  Port 2 - ST3400832AS      372.61 GB
  Port 3 - ST3400832AS      372.61 GB
  Port 4 - ST3400832AS      372.61 GB
  Port 5 - ST3400832AS      372.61 GB
  Port 6 - ST3400832AS      372.61 GB
  Port 7 - ST3400832AS      372.61 GB
  Port 8 - ST3400832AS      372.61 GB
  Port 9 - ST3400832AS      372.61 GB
  Port 10 - ST3400832AS    372.61 GB

*** Press <Alt-3. to access 3ware BIOS Manager ***
3ware BIOS installed successfully
```

Third screen
```
Phoenix cME FirstBIOS Workstation Pro
Copyright 1985-2003Phoenix Technologies Ltd.
All Rights Reserved
Thunder i7520/s5360. Bios Version: V1.03

CPU = 1 - Intel (R) Xeon (TM) CPU 2.80GHz
1024 System ECC Ram Passed
1024k Cache SRAM Passed
System BIOS shadowed
Video BIOS shadowed
Fixed Disk 0: PQI IDE Secured DiskOnModule
ATAPI CD-ROM: MATSHITACD-RW CW-8123
Mouse initialised

Press <F2> to enter SETUP
<ESC> Boot Menu
```

Fourth Screen
```
Phoenix cME FirstBIOS Pro Setup Utility
CPU Type:  Intel (R) Xeon (TM) CPU 2.80GHz
CPU Speed: 2.80 GHz
Physical CPUs: 1
Logical CPUs: 2
System ROM: E001 - FFF
BIOS Date: 03/18/05
System Memory: 624 kB
Extended Memory: 1022 MB
Shadow RAM: 384 KB
Cache RAM: 1024 KB
COM Ports: 03F8 02F8
LPT Ports: 0378
Display Type: EGA \ VGA
Mouse: Installed
Hard Disk 0: PQI IDE Secured-(PPS/2
Hard Disk 1: None
Hard Disk 2: MATSHITACD-RW
Hard Disk 3: None
Hard Disk 4: None
Hard Disk 5: None
Diskette A: 1.44/1.25 MB 3 1/2"
Diskette B: Disabled

Press any key to continue
```


After that I get the screen asking whether I want to boot into standard Ubuntu or a different Ubuntu mode (can't remember what it is off the top of my head).

Once I select Ubuntu, the screen then fills up with output very quickly (too quick to read) with various messages and error messages. I think these only pertain to 'sda'. At least I can't recall any other /dev/ being mentioned. But then, the speed at which the output appears makes it hard to be certain.

If this isn't what you needed to know, then apologies.


Unfortunately I have no idea how to go about adding drivers to the boot image. Any references that might help me?

---

### Post by laddj on 2015-10-28
I've managed to find various drivers for the network card online and a 3ware installation guide which covers 'Red Hat Linux' and 'SuSE Linux'. 
So I might try to battle my way through those installation steps and see if that changes anything.

I'll report back any progress.

---

### Post by TheFu on 2015-10-28
SuSE and Redhat are NOT the same as Ubuntu.  

I suspect it is just a package that needs to be installed. Worst case, might have to put the module into a file inside /etc/modprobe.d/ with an option or 2. [https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules) might be helpful. BTW, always, always use **sudoedit** whenever editing system files. This is safe, unlike some of the other instructions I've seen. Don't use sudo with any GUI editor, but it is safe to use sudo nano or sudo vim, if you like. sudoedit is just safer overall.

Also, if you could please fix the "code tags" in the last group of post #5 above. The indentation is CRITICAL. Can't tell where /boot is.

I don't think there is any way to capture pre-boot data on a physical machine besides video.  On a virtual machine, you can record everything.  After the Ubuntu kernel selection, the boot data in in /var/log/ ... The trick is this is overwritten every boot, so to access the last boot, you have to boot from alternate media - like a flash drive.  If systemd is part of the OS (it is creeping in a little more with every release), text files may not be there and you'll have to use journalctl to see **any** logs.  That means you'll need the same or later version of Ubuntu on that flash drive to access the logs at all.  Normal "save-your-butt" distros don't have systemd stuff that I've seen (looked 1-2 months ago).

Anyway - hope this helps.

---

### Post by laddj on 2015-10-29
I haven't yet had a chance to try to extract all the masseges I get when I boot; hopefully I'll get a chance tonight. 

In the mean time, I've looked more thoroughly into the driver issue. According to [this ]("http://mycusthelp.info/LSI/_cs/AnswerDetail.aspx?sSessionID=31185251179ESHCXLYOBTLQHIKAXHCPNRPCXPSKK&inc=7567&caller=1&txtCriteria=ubuntu")link (from the people that bought out 3ware), the network card should be supported by Ubuntu. I assume that means that no additional drivers are required. I am not sure whether anything needs to be enabled for this to work though.

From linked website:
> [SIZE=3][COLOR=#333333][FONT=myriad-pro-n4][SIZE=2]3ware 7000/8000/9500S/9550SX(U)/9590SE/9650SE/9690SA Series controllers

[/SIZE]Linux kernels 2.6.23 and newer, and all 2.6 kernels include [native support]("http://192.19.193.26/NewLSIKB/KnowledgebaseArticle15116.aspx") [SIZE=2]for the 3ware 7000/8000[/SIZE][SIZE=2]/[/SIZE]9500S/9550SX(U)/9590SE/9650SE/9690SA [SIZE=2]series controllers.  Use the driver that is built into the kernel, and the latest available 3DM2 and CLI for the management software. [/SIZE] [/FONT][/COLOR][/SIZE] 


I've also updated the "Code" tags as requested a few days ago. The lsblk shows /boot on sdc2 (i.e. on part of the 3ware RAID).

---

### Post by TheFu on 2015-10-29
So ... we are beyond my skills.
The VGs, LVs, and /etc/fstab all look fine to me.
The kernel support for your RAID controller is likely working.

We've been all over by now.  Please clarify a few questions:
* Does the system boot with the current kernel?
* Does the system boot with the current kernel in rescue mode?
* Does the system boot with an older kernel? Is that even a choice?

Is there anything in the 'dmesg' output (this is boot/HW stuff) or in the syslog (/var/log/syslog) that looks  like an error/warning issue related to the disks, controller?

I'm really guessing here.
Would it be possible to add a 25G+ disk to the server and install the OS+Apps to that, then use the external array just for data? Most of my servers are 4G-15G in OS/Applications  ... data goes elsewhere. Just a thought.  I've never installed the OS onto local RAID - if  I need HA, we use a SAN and boot off that storage.  At home, I have 2 disks, and manually mirror one to the other every month or so (using ddrescue) so if anything terrible happens just swapping SATA cables fixes it well enough.  Data and VMs run off an external array if if there is a HW issue, between backups and just plugging in the array to another box here will get the VMs up again within 30-60 min.

---

### Post by laddj on 2015-10-29
[COLOR=#000000]* Does the system boot with the current kernel? ------------------------------NO[/COLOR]
[COLOR=#000000]* Does the system boot with the current kernel in rescue mode?---------NO[/COLOR]
[COLOR=#000000]* Does the system boot with an older kernel? Is that even a choice?----no older kernels or any other OS installed.


After a lot more reading and questioning whether or not the system can actually see the 3ware, I came across various articles describing modules. I managed to print an lsmod table and 3w_9xxx appears, which is good. I'm not sure if the fact that its in this table means that it is actually loaded though.

[/COLOR]```
Module                  Size  Used by
xfs                   917504  0 
libcrc32c              16384  1 xfs
jfs                   188416  0 
btrfs                 937984  0 
raid10                 49152  0 
raid456                94208  0 
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
xor                    24576  2 btrfs,async_xor
raid6_pq               98304  3 async_pq,btrfs,async_raid6_recov
raid1                  40960  0 
raid0                  20480  0 
multipath              16384  0 
linear                 16384  0 
e1000                 135168  0 
parport_pc             32768  0 
parport                45056  1 parport_pc
nls_utf8               16384  1 
isofs                  40960  1 
usb_storage            69632  0 
floppy                 77824  0 
3w_9xxx                45056  2 

```


Your comment about adding a further drive and installing the OS on there is valid. I'll have to see if I can get my hands on the hardware as this approach may be a lot less painful in the long run.


Once again, thanks for all your help so far. I've learnt a lot and really appreciate it.

---

### Post by TheFu on 2015-10-29
All these commands you are running are from a live-boot CDROM or flash drive?
That is completely different than running a booted kernel that was  installed. The list of modules  is different,  the environment is different.

Try using "boot-repair" from the live-CD.  You'll need to install it. Not an issue and hopefully it will see and fix the issues.

---

### Post by laddj on 2015-10-31
Hi again

I've done it. Please allow me to thank you again for all your help. I really appreciate it and have learnt an awful lot over the last week.

I solved the problem in the end by adding another HDD outside the RAID and adding my /, swap and /root partitions onto this drive. I've then added the /home partition and a /data partition onto the RAID. And the install has gone through all the way and Ubuntu is now booting.

I've only just completed it within the last 5min, so haven't been able to play around with it and see how well everything is working. But again, thank you for all your help.  Hopefully this will be the end of my troubles and I can figure out all the rest by myself. Much appreciated.

---

