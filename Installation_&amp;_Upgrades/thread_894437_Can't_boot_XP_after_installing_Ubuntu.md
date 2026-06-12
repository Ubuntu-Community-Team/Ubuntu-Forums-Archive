---
title: "Can't boot XP after installing Ubuntu"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by anxiousdog on 2008-08-19
Well I think I've finally dug a hole deep enough that I need to ask for direct help. I've been Googling and reading this forum for days and everything I've tried isn't working.

First, I have a PC that has WinXP on an 80gig hard drive. I wanted to keep XP and dual boot Ubuntu until I could be sure that I didn't need Windows anymore. So I used the Hardy live CD to install and chose to manually partition giving about 20gig to Ubuntu (to start). During the install, the CD failed and asked me to reboot. When I did the reboot, I saw a black screen that said:

> 
Starting Up....
Disk Read Error
Press Ctl+Alt+Del to reboot


Ouch. Nothing I could do would get XP to boot so I just reinstalled Ubuntu via the live CD. That went swell the 2nd time and I was able to use it like normal. The boot screen said that I could boot to Windows, but I got the same error every time I tried.

I have tried all the regularly suggested things which include

- updating the menu.lst
- Running repair from the XP cd
- bootcfg /rebuild
- Fixmbr

After I did the fixmbr last night, I was unable to boot to Ubuntu at all. Every boot results in the same screen I mentioned above. When I run the XP cd, it does recognize that Windows is installed on C:/Windows so I think the data is there but maybe the partition is damaged. Ideally I'd like to save the data on Windows, but I can stand to lose what's on the Ubuntu partition if I have to.

What can I do from here?

---

### Post by Pumalite on 2008-08-19
Post:
sudo fdisk -lu
Also; if your XP is bootable Super grub will do it.

---

### Post by anxiousdog on 2008-08-19
Sorry, I was just about to do that.

> 
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7081    56878101    7  HPFS/NTFS
/dev/sda2            7082        9629    20466810    5  Extended
/dev/sda3            9562        9623      497983+  82  Linux swap / Solaris
/dev/sda5            7082        9561    19920537   83  Linux
/dev/sda6            9624        9629       48163+  83  Linux


---

### Post by Pumalite on 2008-08-19
Try Super Grub and see if you can boot Windows:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by anxiousdog on 2008-08-19
> **Pumalite said:**
> Try Super Grub and see if you can boot Windows:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Ok I downloaded SUD and put it on a floppy. I was able to run it just fine but nothing has worked so far. I tried several options:

- Windows (Activate Partition)
- Boot Windows
- Fix Windows (uninstall grub)
- Restore Backup (restore windows partition (NTFS) Boot backup same partition

I can now get to the grub menu, but when I select the Windows XP boot, I get 

> 
Error 12: Invalid device requested
Press any key to continue


And when I try to boot any of the ubuntu options, I get

> Error 15: File not found 

So where do I go from here?

---

### Post by caljohnsmith on 2008-08-19
Anxiousdog, based on what you've said so far, I think fixing your problem might be really easy. Please boot up your Ubuntu Live CD, open a terminal, and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][This should return your Ubuntu partition with Grub as (hd0,4), if it does proceed with:][/COLOR]
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
What the above will do is reinstall Grub to your MBR, and it will point to (hd0,4) or /dev/sda5 for its configuration files. Let me know if you encounter any problems or errors.

EDIT: Wait, I think I may have misread your previous post. Do you get the Grub menu on startup now? If so, skip the above steps. Instead, boot a Live CD, and in the terminal do:
```
sudo mount /dev/sda5 /mnt
cat /mnt/boot/grub/menu.lst
```
And post the output please.

---

### Post by Pumalite on 2008-08-19
You might be trying to boot Windows from a logical partition: post a screenshot of Gparted.

---

### Post by anxiousdog on 2008-08-19
Caljohnsmith: Thanks for the help... maybe I'm still a bit of a ways off from the 'easy' fixes!

I tried your first suggestion and here is what I got:
> 
grub> find /boot/grub/stage1

Error 15: File not found


I followed your second suggestion and here is the output:

> 
ubuntu@ubuntu:/$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:/$ cat /mnt/boot/grub/menu.lst
cat: /mnt/boot/grub/menu.lst: No such file or directory


---

### Post by anxiousdog on 2008-08-19
> **Pumalite said:**
> You might be trying to boot Windows from a logical partition: post a screenshot of Gparted.

Looks like you're on to something... attaching a screen shot of the terminal + gparted.

---

### Post by Pumalite on 2008-08-19
sda is enterily unallocated. No OS in that drive according to Gparted. Your fdisk tells a different story. Are you able to boot Ubuntu with Super Grub?

---

### Post by anxiousdog on 2008-08-19
> **Pumalite said:**
> sda is enterily unallocated. No OS in that drive according to Gparted. Your fdisk tells a different story. Are you able to boot Ubuntu with Super Grub?

Nope. I can see the list of OS but no matter which one I try to boot I get an error. The Linux errors are "Error 15: File not found" and when I boot XP it says "Error 12: Invalid device requested".

---

### Post by Pumalite on 2008-08-19
Boot a Knoppix Live CD and try to save data. Otherwise start from scratch.

---

### Post by caljohnsmith on 2008-08-19
Something has got to be wrong with that gparted screen shot you provided, otherwise fdisk wouldn't show partitions and Grub would not get as far as showing you a menu on startup. 

Please boot the Live CD again, and before you do anything, mount both sda5 and sda6:
```
sudo mkdir /mnt/sda5
sudo mkdir /mnt/sda6
sudo mount /dev/sda5 /mnt/sda5
sudo mount /dev/sda6 /mnt/sda6
ls -l /mnt/sda5
ls -l /mnt/sda6

```
Please post the output from the above commands.

Next see if Grub can find its stage2 file, because if you get a menu on startup, you should have a stage2 file somewhere:
```
sudo grub
grub> find /boot/grub/stage2
grub> find /boot/stage2
grub> find /grub/stage2
grub> quit
```
And please post the output.

---

### Post by anxiousdog on 2008-08-19
Here is the first output:

> 
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda5
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda6
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/sda6
ubuntu@ubuntu:~$ ls -l /mnt/sda5
total 96
drwxr-xr-x   2 root root    4096 2008-08-15 13:58 bin
drwxr-xr-x   2 root ubuntu  4096 2008-08-15 08:37 boot
lrwxrwxrwx   1 root ubuntu    11 2008-08-15 08:37 cdrom -> media/cdrom
drwxr-xr-x   4 root root    4096 2008-07-02 10:26 dev
drwxr-xr-x 125 root root   12288 2008-08-19 03:02 etc
drwxr-xr-x   3 root root    4096 2008-08-15 08:44 home
drwxr-xr-x   2 root root    4096 2008-07-02 10:16 initrd
lrwxrwxrwx   1 root ubuntu    33 2008-08-15 03:47 initrd.img -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  17 root root    4096 2008-08-18 13:34 lib
drwx------   2 root root   16384 2008-08-15 08:37 lost+found
drwxr-xr-x   5 root root    4096 2008-08-19 03:01 media
drwxr-xr-x   2 root root    4096 2008-04-15 05:53 mnt
drwxr-xr-x   2 root root    4096 2008-07-02 10:16 opt
drwxr-xr-x   2 root root    4096 2008-04-15 05:53 proc
drwxr-xr-x  10 root root    4096 2008-08-19 03:00 root
drwxr-xr-x   2 root root    4096 2008-08-18 13:34 sbin
drwxr-xr-x   2 root root    4096 2008-07-02 10:16 srv
drwxr-xr-x   2 root root    4096 2008-04-19 05:05 sys
drwxrwxrwt   5 root root    4096 2008-08-19 03:02 tmp
drwxr-xr-x  12 root root    4096 2008-08-15 13:53 usr
drwxr-xr-x  15 root root    4096 2008-07-02 10:34 var
lrwxrwxrwx   1 root ubuntu    30 2008-08-15 03:47 vmlinuz -> boot/vmlinuz-2.6.24-19-generic
ubuntu@ubuntu:~$ ls -l /mnt/sda6
total 18497
-rw-r--r-- 1 root root    422667 2008-07-12 05:30 abi-2.6.24-19-generic
-rw-r--r-- 1 root root     80049 2008-07-12 05:30 config-2.6.24-19-generic
drwxr-xr-x 3 root ubuntu    1024 2008-08-19 03:00 grub
-rw-r--r-- 1 root root   7911819 2008-08-18 13:35 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root   7497036 2008-08-15 14:05 initrd.img-2.6.24-19-generic.bak
drwx------ 2 root root     12288 2008-08-15 08:37 lost+found
-rw-r--r-- 1 root root    103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root    905170 2008-07-12 05:30 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root   1921432 2008-07-12 05:30 vmlinuz-2.6.24-19-generic


Here is what I got with grub:

> 
grub> find /boot/grub/stage2

Error 15: File not found

grub> find /boot/stage2

Error 15: File not found

grub> find /grub/stage2
 (hd0,6)


---

### Post by caljohnsmith on 2008-08-19
> **anxiousdog said:**
> 
grub> find /grub/stage2
(hd0,6)

Are you sure that was what Grub responded? :-k (hd0,6) is the same as /dev/sda7, but according to your fdisk output in post #3, you don't even have a /dev/sda7 partition. Unfortunately it looks like there might be something wrong with your HDD's partition table. Either that or Grub has lost its sanity. 

Please post the output of the following from a Live CD:
```
sudo grub
grub> geometry (hd0)
grub> quit

```
And while you're at it, check again that "sudo fdisk -l" matches your post #3.

But before we go any further, I would recommend backing up any important files you have in Windows. To do this, I would first try booting your Windows Install CD and running *both*:
```
fixmbr
fixboot
```
"Fixmbr" will put the Win XP boot loader back in the master boot record (MBR), and "fixboot" will fix the boot sector of your Windows partition. If that doesn't allow you to boot directly into Windows on startup (and then save your important files), your other option is:
[LIST]
[*]Boot a Live CD
[*]Open a terminal and do:
```
sudo mount /dev/sda1 /mnt
```
[/list]That should mount windows to the /mnt directory. Then you can use a file browser to go to /mnt and copy files from there to a USB stick or something. Let me know how it goes.

---

### Post by anxiousdog on 2008-08-19
I'm pretty sure that fixmbr/fixboot won't let XP boot up since I've tried it a few times including using Super Grub. :\

> 
grub> geometry (hd0)
drive 0x80: C/H/S = 9729/255/63, The number of sectors = 156301488, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 2,  Filesystem type unknown, partition type 0x82
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 6,  Filesystem type is ext2fs, partition type 0x83


> 
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7081    56878101    7  HPFS/NTFS
/dev/sda2            7082        9629    20466810    5  Extended
/dev/sda3            9562        9623      497983+  82  Linux swap / Solaris
/dev/sda5            7082        9561    19920537   83  Linux
/dev/sda6            9624        9629       48163+  83  Linux


Looks the same... is there a way to reinstall grub so that it will work correctly?

---

### Post by caljohnsmith on 2008-08-19
We may be able to get your Grub temporarily working, but in the end I think you're going to need to run some integrity tests on your HDD and check for errors. There definitely seems to be something wrong with your partitioning.

But to see if we can get Grub going again, from the Live CD try:
```
sudo grub
grub> root (hd0,6)
grub> setup (hd0)
grub> quit
```
Also do:
```
sudo umount /dev/sda6
sudo mount /dev/sda6 /mnt
ls -l /mnt/grub
cat /mnt/grub/menu.lst
```
Please post the output.

---

### Post by anxiousdog on 2008-08-19
Okay, before I do that let me tell you that I *finally* got Ubuntu to boot and everything is intact nice and safe - just how I left it.

I rebooted and when I got to the grub menu, I hit "e" to edit before I booted. I saw an entry that said "root (hd0,5)" I edited that and changed it to "root (hd0,6)" and then hit "b" for boot. Came up just fine!

1. So now how do I make that permanant? Is it the menu.lst file? 

2. What about the XP boot issue?

3. Do I still need to do the commands above?

---

### Post by caljohnsmith on 2008-08-19
> **anxiousdog said:**
> Okay, before I do that let me tell you that I *finally* got Ubuntu to boot and everything is intact nice and safe - just how I left it.

I rebooted and when I got to the grub menu, I hit "e" to edit before I booted. I saw an entry that said "root (hd0,5)" I edited that and changed it to "root (hd0,6)" and then hit "b" for boot. Came up just fine!

I guess I don't understand, because previously you said you had reinstalled the Windows XP MBR, so that you weren't able to boot anything. How did you reinstall Grub and get your Grub menu back? 
> **anxiousdog said:**
> 
1. So now how do I make that permanant? Is it the menu.lst file? 

Yes, to make the change permanent, just edit your menu.lst file which should be on sda6 in the /grub directory. 
> **anxiousdog said:**
> 
2. What about the XP boot issue?

You'll first need to post your menu.lst so we can check that:
```
sudo umount /dev/sda6   [COLOR="Blue"][it's OK if it returns an error, I'm just making sure it is unmounted so we can mount it to /mnt][/COLOR]
sudo mount /dev/sda6 /mnt
ls -l /mnt/grub
cat /mnt/grub/menu.lst
```
Anxiousdog, I really think you should run some disk checking programs on your HDD to see if it is OK. Whether things seem to be working, something is not OK with your HDD or you wouldn't have conflicting info from fdisk, grub, and gparted. But it's your computer, I'm just warning you that you may be in for alot of problems if you don't get to the root of the partitioning enigma.

---

### Post by anxiousdog on 2008-08-19
I was able to run the Super Grub disk and run "Fix boot of Linux" early on. I just didn't realize that it was trying to boot to hd,05 rather than hd,06. Once I changed that I'm back to the issue with XP. Here is my menu.lst:

> 
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=fb481ecc-e004-4484-ac96-f41f684274b3 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=fb481ecc-e004-4484-ac96-f41f684274b3 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP
rootnoverify (hd0,1)
makeactive
chainloader +1
boot


When I rebooted and tried to boot XP, I got "Error 13: Invalid or unsupported executable format".

What tools do you suggest I try to verify the HD?

Sidenote: it seems like nothing is ever easy with me...

---

### Post by caljohnsmith on 2008-08-19
To fix your Windows entry in the menu.lst, use the following:
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```
Note there should be no "boot" line at the end. And of course to fix Ubuntu just change all those "root (hd6,0)" lines to "root (hd5,0)". 

Do you have a CD with disk checking tools that came with your HDD? If not you could download and use [The Ultimate Boot CD]("http://www,ultimatebootcd.com"). 

Also. boot up your Live CD and run the following:
```
sudo apt-get install testdisk [I don't remember if it is on the live CD]
sudo testdisk

```
Go through the prompts and choose the "analyze" option, and see if it returns any errors. Please post the output.

---

### Post by anxiousdog on 2008-08-19
Well let me preface this again with the fact that nothing is easy with me. :)

I ran testdisk and didn't seen any obvious errors, and gparted is looking rather nice again (see attached screenshot).

However, now when I try to boot I see the Ubuntu splash which runs forever and finally ends up at the initramfs terminal. Oy.

XP still won't boot, so I'm back to the live CD.

Here is the latest fdisk:

```

ubuntu@ubuntu:~/testdisk-6.10/linux$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        7081    56878101    7  HPFS/NTFS

/dev/sda2            7082        9629    20466810    f  W95 Ext'd (LBA)

/dev/sda5            7082        9561    19920568+  83  Linux

/dev/sda6            9562        9623      497983+  82  Linux swap / Solaris

/dev/sda7            9624        9629       48163+  83  Linux

```

Here is the testdisk output after I did the quick search:
```

Disk /dev/sda - 80 GB / 74 GiB - CHS 9730 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  7080 254 63  113756202 [SysPart]
L Linux                 7081   1  1  9560 254 63   39841137
L Linux Swap            9561   1  1  9622 254 63     995967
L Linux                 9623   1  1  9628 254 63      96327
P Linux                 9629   0  1  9728 254 63    1606500

```

---

### Post by caljohnsmith on 2008-08-19
There has got to be something going on with your HDD, because nothing has been consistent. How about running the following from your Live CD:
```
badblocks /dev/sda | tee ~/Desktop/bad_sectors.txt
```
Also:
```
sudo smartctl -a /dev/sda
```
Check the output from the above command to see if your HDD is "SMART" enabled, and if so run:
```
sudo smartctl -t long /dev/sda
```
Note the above command will immediately terminate, but your HDD will continue running its self-diagnostics. To check its progress and results, use again:
```
sudo smartctl -a /dev/sda
```

---

### Post by Pumalite on 2008-08-19
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by anxiousdog on 2008-08-20
Hey again Caljohnsmith... I'm very thankful for your diligence in helping me with this. I'm sure that you're right with the HDD issue. When I tried Pumalite's suggestion to reinstall grub, I got a 'badblocks' error message.

I've run the command you gave me for smartctl but I guess I don't have it:

```

ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
sudo: smartctl: command not found
ubuntu@ubuntu:~$ 

```

I also did the bad_sectors.txt with the following:

```
ubuntu@ubuntu:/$ sudo badblocks /dev/sda | tee ~/Desktop/bad_sectors.txt

```

The terminal window is just hanging, but it did create the bad_sectors.txt file - though nothing is in it. ARGH. Wait, maybe it's just taking a while?

I'd blow the whole thing away and start over, but I have about 30gig of data in Windows that I'd like to keep and I don't have a very good way to offload it. I don't think our server has enough room (I'll check with my husband) and not sure if we have any other hard drives readily available.

Thoughts this morning?

---

### Post by caljohnsmith on 2008-08-20
My mistake, I forgot that neither "badblocks" or "smartctl" are programs installed by default. You can install them with:
```
sudo apt-get install e2fsprogs smartmontools
```
I would definitely try to make a backup of all your important files at this point, as I think the only possible realistic, long-term, and reliable solution would be to wipe your HDD clean and start over; but only if we can prove that your HDD is still in good health. Let me know the results you get when running "badblocks" and "smartctl". 

Also, do you have a diagnostic tools CD that came with your HDD? Please run that if you do. If not, you could download the [Ultimate Boot CD]("http://www.ultimatebootcd.com") as that has a plethora of HDD diagnostic tests you can run.

About backing up your files, do you have a USB stick or maybe some DVD-RW disks you could use to back up with? If you're really desperate for a place to back up to, you could always upload to some place like [www.drop.io](www.drop.io) (no need to create an account). Let me know how it goes. :)

---

### Post by anxiousdog on 2008-08-20
Ah thanks! Ok to start here is the output from smartctl:

```

ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST380011A
Serial Number:    5JV91D5M
Firmware Version: 3.08
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Wed Aug 20 14:31:41 2008 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  58) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   061   057   006    Pre-fail  Always       -       2858034
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       7
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   089   060   030    Pre-fail  Always       -       830248440
  9 Power_On_Hours          0x0032   062   062   000    Old_age   Always       -       33467
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       211
194 Temperature_Celsius     0x0022   045   048   000    Old_age   Always       -       45
195 Hardware_ECC_Recovered  0x001a   061   057   000    Old_age   Always       -       2858034
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by anxiousdog on 2008-08-20
Wellllll, I finally gave up with all the errors I was getting and blew away the Ubuntu partition. I tried to rebuild XP but it gave me an error so I decided to rebuild Ubuntu instead.

I have it installed and working and I even mounted to my windows files so that I can see my data (and back it up). I'll back it up and then blow away the windows partition. I ran several diagnostic tools on my hard drive but it didn't throw any obvious errors. I think the issue was with the partitions. Not to mention that my XP install is ancient and probably just waiting to die on me.

I won't mark this solved just yet since I worry that after the re-install of XP I still may not be able to dual boot, but we'll see.

---

### Post by Pumalite on 2008-08-20
Glad you decided to do it and finally got it working.

---

### Post by anxiousdog on 2008-08-20
> **Pumalite said:**
> Glad you decided to do it and finally got it working.

Thanks for your help. I'm very happy to be using Hardy full-time. Now as soon as I can be sure I don't need no stinkin' windose at all, I'll ditch it.

---

