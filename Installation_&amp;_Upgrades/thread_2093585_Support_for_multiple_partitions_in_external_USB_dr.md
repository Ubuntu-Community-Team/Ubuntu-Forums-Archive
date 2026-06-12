---
title: "Support for multiple partitions in external USB drive"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by pakki on 2012-12-11
@ [http://askubuntu.com/questions/227614/attempt-to-mount-a-filesystem-with-type-ext4-at-failed#comment280844_227614](http://askubuntu.com/questions/227614/attempt-to-mount-a-filesystem-with-type-ext4-at-failed#comment280844_227614)

So I can't install Ubuntu in my external drive I therefore removed my internal laptop hardisk (contain windows) & placed the external hardisk (previously in a Samsung USB 2.5' External Closure) of 160gb there...I ran installation using this profile

all as ext4.. swap 2000mb logical / 17000mb logical /home 9000mb logical /opt 14000mb logical rest free space...

Installation ran perfectly without the error mentioned in previous question. Now I tried luck by pulling out this internal hard (containing perfectly running copy of Ubuntu 12.10) & inserting it in Samsung enclosure to be used as USB...

I booted from this USB & walla Ubuntu did boot but wait it threw two nasty errors for being unable to mount /home & then /opt press S to skip & M manual recovery I chose to skip & I can login as a guest & can use Ubuntu?

From this experiment I concluded that Ubuntu doesnt support multiple partitions (/home & /opt) in a USB Hardisk, am I correct?

I reinstalled Ubuntu again making this hardisk as internal but this time with this profile (note only one / partition)

all as ext4.. swap 2000mb logical / 50000mb logical rest free space

I again made this act as external USB hardisk & Ubuntu finally ran successfully but flexibility of separate /home & /opt partitions was out of equation :(

I played a little bit with Ubuntu... then it was time to finally insert my Win7 (original) internal hardisk. After I booted to Windows, attached the external hard (containing Ubuntu) I formatted the free space left in Ubuntu installation as NTFS (because NTFS option wasn't available in gpart, another disappointment of having FAT32 but not NTFS). Now again I booted via this USB hardisk but it throwed me an error:

unknown filesystem grub rescue

& I was utterly dismayed & retired ungracefully :(

---

### Post by C.S.Cameron on 2012-12-11
Following is step by step for installing 12.04 on a 64GB flash drive on an Intel machine. 12.10 is almost the same.
This is just like doing a normal install to internal drive except for the option of making the first partition FAT32 (or leaving it NTFS) so Windows can see it. Procedure is identical for all USB drives.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue.

At "Installation type" select "Something else".
Continue
Confirm Device is correct.

Select "New Partition Table".
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Make "Size:" about 66000 MB.
Select "Primary".
Location for the new partition = "Beginning of this space".
"Use as:" = "FAT32 file system".
And Mount point = "/windows".
Select "OK"

Click "free space" and then "Add".
Select "Size:" = 4000 to 6000 megabytes, "Primary", Beginning of this space, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Size ..." = 1000 to 4000 MB, "Primary", Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can update grub later, if you wish.

---

### Post by pakki on 2012-12-12
I have done similar steps but weirdness is the final result! 

I am installing on a 160gb hard I a Samsung enclosure... After installing Ubuntu I boot from my external hard the first time & it runs perfectly. Then I issue the command to shut Ubuntu down, I keep waiting but computer doesn't shut down (Ubuntu keeps scrolling) & thus I manually unplug my CPU. After that first shutdown my external hard never boots with Ubuntu (no matter what partition configurations) issuing error of unknown filesystem grub rescue

---

### Post by sudodus on 2012-12-12
> **pakki said:**
> I have done similar steps but weirdness is the final result! 

I am installing on a 160gb hard I a Samsung enclosure... After installing Ubuntu I boot from my external hard the first time & it runs perfectly. Then I issue the command to shut Ubuntu down, I keep waiting but computer doesn't shut down (Ubuntu keeps scrolling) & thus I manually unplug my CPU. After that first shutdown my external hard never boots with Ubuntu (no matter what partition configurations) issuing error of unknown filesystem grub rescue
USB is very slow writing many small files, so I think the computer was still busy writing while you interrupted it by unplugging. I suggest that you try again, this time letting it finish writing.

If you have an eSATA (for example a USB + eSATA combo) port, you can get much faster data transfer and better performance if you boot from there instead of USB 2.0. I think there are problems to boot from USB 3.0, but maybe it works with the newest version of Ubuntu.

---

### Post by pakki on 2012-12-12
> USB is very slow writing many small files, so I think the computer was still busy writing while you interrupted it by unplugging.

But Ubuntu had already installed itself onto the hardrive. I played with it (even installing some apps) for half an hour. It just that if I shut it down (while this is plugged in USB) it won't... & on the next boot it creates the Grub error?

---

### Post by sudodus on 2012-12-12
> **pakki said:**
> 
From this experiment I concluded that Ubuntu doesnt support multiple partitions (/home & /opt) in a USB Hardisk, am I correct?

No, it is possible to use many partitions. I have several such USB (HDD and flash) drives, and they work for me.
> 
But Ubuntu had already installed itself onto the hardrive. I played with it (even installing some apps) for half an hour. It just that if I shut it down (while this is plugged in USB) it won't... & on the next boot it creates the Grub error?
So the same drive works when internal, but not when mounted via USB? I have also done this operation, and it works even in different computers provided that I have not installed any proprietary drivers that might be incompatible with some of the computers. I have also cloned between USB pendrives, internal SATA drives and an eSATA drive. It works for me.

So what is different for you? Will your computer boot properly from a live USB drive (for example an Ubuntu install drive)? What about the settings of your BIOS?

---

### Post by pakki on 2012-12-12
Sir thanks for bearing wth me & I hope you continue that while I give comprehensive details...

The external hardrive (WD Scorpio blue 160gb) is encased in a Samsung 2.5' External closure which don't uses any software... I can connect it with my Sony Bravia, Win system or even Android Tab it just works as a normal USB.

**Let us focus on booting external drive having Ubuntu installed on it & forget about supporting different partitions...**

I pull out my laptop's internal 360Gb (fearing of messing its MBR) & replaced it with 160Gb which afterwards be used as external. So I installed Ubuntu using live CD using:

```
swap 2000mb logical
/ 58000mb primary ext4
/windows rest as FAT32
install boot configuration as /dev/sda
```

Ubuntu ran (& I restarted several times) flawlessly while I used 160gb as internal...Then I in-placed the original 320gb & inserted 160gb in Samsung's casing to be used as external. 
Switched on the laptop & don't boot from my internal (360gb having windows) rather booted fom my 160gb now acting as external USB. 

Like always Ubuntu ran flawless for the **first time**, I can install/unistall & every stuff also it recognised all the partitions my 360gb internal. But here is the tragedy when I issue a restart or shutdown it never does rather it stucks with Ubuntu scroller going on & on...perhaps this is the cause that corrupts the GRUB after it fails to shutdown laptop & black screen with erros pops up...stucked

I can't give a screenshoot but I do realise that GRUB fails to understand from which hardisk it is being loaded or something in **presence** of windows carying 360gb internal hard...**abstracts** from the error screen

> 
ata_id[240]:HDIO_GET_IDENTITY failed for /dev/sdb Invalid argument
.
.
.
Deactivating Swap
.
.
unmount: /run/lock not mounted
unmount: /run/shm not mounted
.
.
unable to connect system bus
Failed to connect to socket
.
.
/var/run/dbus/system -bus scoket: No such file or dircetory



Now I force shutdown & always next time error is the same

> unknown filesystem
grub rescue> 

I think Grub don't understands hardware changes & this is the bane when I want an independent booting system form my external drive

> So what is different for you? Will your computer boot properly from a live USB drive (for example an Ubuntu install drive)? What about the settings of your BIOS?

I use PowerISO to make my Kingston USB 4gb bootable with any distros image file & it boots normally rather I did installed Ubuntu from my kingston USB onto 160gb as internal but history repeats itself :(

---

### Post by C.S.Cameron on 2012-12-12
As an experiment, boot your normal internal drive,
Plug in your external drive.
In terminal run:

```
sudo update-grub
```

Now boot your external drive, (with internal still installed).
and in termal run:

```
sudo update-grub
```

You should then have the grub option to boot either no mate which boots first.

---

### Post by sudodus on 2012-12-13
What about your internal drive: Is there exactly the same content as in your external drive? I mean the same UUID, label etc of the partitions? Otherwise they should not be mixed up.

I still think that you have too little patience, you must wait very long until the cached files are written from your RAM to the USB drive. This is much slower than when the system is on an internal SATA drive. It is different with a live USB drive, because it need not write anything. And a persistent live USB drive only writes a little (only some modifications, most of the system files come from a compressed file).

If you are not sure when the writing process has finished, you can run sync from a terminal window
```
sync
``` When this command finishes, and you get a new prompt, writing has finished, and it should be faster to shutdown or reboot the computer.

Another problem might be that there is now some file system error. Check for that and try to repair it like this:

- Boot from another linux drive, for example the Ubuntu install USB pendrive.

- Open a terminal window and run

```
sudo e2fsck -f /dev/sdXY
```

where X is the drive letter (maybe b) and Y is the partition number (maybe 1 or 5) so for example

```
... /dev/sdb1
```

---

### Post by C.S.Cameron on 2012-12-13
I agree that first run things can take a long time, especially shut down. A lot of stuff gets written to disk.
I would allow at least a half hour

---

### Post by pakki on 2012-12-13
Respected sir, 
> What about your internal drive: Is there exactly the same content as in your external drive? I mean the same UUID, label etc of the partitions? Otherwise they should not be mixed up.

Although they have the same brand (WD Scorpio Blue) but one is Malaysian other of Thailand so same UUID is not possible also my internal drive structure is completely different (rather independent) because it don't host any Ubuntu file system only Win7

> 
I still think that you have too little patience, you must wait very long until the cached files are written from your RAM to the USB drive. This is much slower than when the system is on an internal SATA drive. It is different with a live USB drive, because it need not write anything. And a persistent live USB drive only writes a little (only some modifications, most of the system files come from a compressed file).

Sir via HDtune I had tested I/O speed of my external HD which is +25mb/sec I think you are misjudging this with some external *flash drive* which normally operates at 6mb/sec. Further I have given it enough time after prolonged stuck it gives me error mentioned before.

> I agree that first run things can take a long time, especially shut down. A lot of stuff gets written to disk.
I would allow at least a half hour
Like I said its external HD not any cheap flash, furthermore its not the first shutdown experienced by Ubuntu. Like I said previously it was the first shutdown while this Hd is in external mode, I did successful shutdowns/restarts while it opertaes internally.

I don't have any Ubuntu on my original internal drive s I can't access terminal.
[CENTER][IMG]http://i.imgur.com/BmRiZ.jpg[/IMG][/CENTER]
(under win7 this application can easily identify ext4,ext3 & anything)

Why in the God's name my / formatted as EXT4 (56.81gb) is corrupted as shown? That is why I am welcomed with 
unknown filesystem 
grub rescue

---

### Post by oldfred on 2012-12-13
Windows does not know about LInux partitions. I am surprised it even shows swap correctly.

We have seen some systems where grub gets lost when booting from a partition beyond 100GB on drive or very large partitions. Your / (root) does go beyond 100GB. I have always thought it was a BIOS setting, but it may be something in USB ports as well?

I might try a slightly smaller 75GB NTFS sdb1, a 20GB / (root) and use rest of USB drive as /home (and curent swap).

---

### Post by pakki on 2012-12-13
> Windows does not know about LInux partitions. I am surprised it even shows swap correctly.
Windows cant but this app can & also can create ext4 partitions, the only explanation... /root partition got corrupted
[CENTER][IMG]http://i.imgur.com/82VTv.jpg[/IMG][/CENTER]
 
Can u vote for a separate /boot partition. Also i have tried 
```

ls
set root=(hd0,msdos5)
set prefix=(hd0,msdos5)/boot/grub
insmod normal
normal
```

but unknown fileesystem prevails at grub rescue terminal at boot

---

### Post by oldfred on 2012-12-13
From a liveCD/DVD/Flash what does gparted show? You can use gparted from your Ubuntu installer or download gparted or parted magic with gparted as a tools ISO.

Best to use Windows tools for Windows & Linux tools for Linux.

---

### Post by sudodus on 2012-12-13
I see, you are convinced that you were not too impatient, but waited long enough for the drive to write. Good enough.

What about your ext4 partition? How did you create it: with MiniTool Partition Wizard or with Gparted or automatically during the installation of Ubuntu? Or with some other method? Could that be a problem?

But on the other hand, it booted several times internally and once from USB. So it was corrupted during that first USB Ubuntu session. I assumed that it was at shutdown (poweroff or reboot), but it might happen also during the session. How could that happen? Did you do anything special or did you notice anything weird (except at shutdown)?

---

### Post by pakki on 2012-12-13
> But on the other hand, it booted several times internally and once from USB. So it was corrupted during that first USB Ubuntu session. I assumed that it was at shutdown (poweroff or reboot), but it might happen also during the session. How could that happen? Did you do anything special or did you notice anything weird (except at shutdown)?
:D am happy that this statement from your side guarantees that I have passed on my basic question assuredly.
 All partitions were created during install procedure, even I used the option to use full hardisk...
Yes, it never properly shutdowns when I am booting externally & then grub error...I have done several HD tests & everything is fine no bad sectors, nothing! Plus while I played in Ubuntu (when hardisk was used internally) it was superb no error, no lag...
> So it was corrupted during that first USB Ubuntu session. 
Proper statement would be: So it was corrupted **after** (or at the shutdown) that first USB Ubuntu session. 
> From a liveCD/DVD/Flash what does gparted show? You can use gparted from your Ubuntu installer or download gparted or parted magic with gparted as a tools ISO.

Best to use Windows tools for Windows & Linux tools for Linux.
I will answer this tomorrow sir, I am downloading Linux Mint which I believe has gparted in its live session installed. But what I can answer is that I have used application namely 'Disks' in Ubuntu (live USB kingston 4gb) & it can perform every format/create task on my hard (160gb) (while internally or externally) with no error.

After seeing Ubuntu Unity I spend $70 (in Pakistan its not a small amount) to get a hardisk, to get an external casing only to found out that I failed, plz sir do guide.

why don't we try grub rescue commands at boot terminal?

---

### Post by oldfred on 2012-12-13
You can try manual boot, but if shutdown incorrectly it is more likely file corruption and fsck is required.

       [https://help.ubuntu.com/community/Grub2#Command%20%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20%20&%20Rescue%20Mode)
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hdX,Y)
      linux /vmlinuz root=/dev/sdXY ro
      initrd /initrd.img
      boot

    
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb2
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb2


If forcing shutdown remember the elephants.
       
 Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by C.S.Cameron on 2012-12-13
Can you try your external , with a fresh install, on a friends computer?

---

### Post by sudodus on 2012-12-14
I am almost 100 % sure that the drive is corrupted.

It may be possible to ***repair*** it according to oldfred's advice, but it may be more convenient to make a ***fresh install ***and test it as a USB drive in some other computer according to C.S.Cameron's advice.

The advantage of oldfred's advice is that you learn what to do if something similar happens to a system where you have invested a lot of time and effort.

Once your system is ready, take ***frequent backups*** and avoid spending a lot of time and effort twice.

---

### Post by pakki on 2012-12-14
All the remaining questions be answered shortly

> **C.S.Cameron said:**
> Can you try your external , with a fresh install, on a friends computer?

I have tried this already on another PC, totally different than mine but same result. First I have to make my 160gb hardisk as **internal** to install Ubuntu because while I install Ubuntu **externally** I am met with this error ```
Attempt to mount a filesystem with type ext4 at '/' failed
```

Before this thread I have comprehensively explained this here:
[http://askubuntu.com/questions/227614/attempt-to-mount-a-filesystem-with-type-ext4-at-failed](http://askubuntu.com/questions/227614/attempt-to-mount-a-filesystem-with-type-ext4-at-failed)

So I really get tired to unplug internal drives then pull out my 160gb from external enclosure & plug it as internal but fair enough if I succeed to get it install somehow

---

### Post by pakki on 2012-12-14
I am writing reply while using Live Linux MInt 14 via 4gb Flash:
After extended failure i converted my external HD partition table to GPT  via win7 disk managment...experimenting 
I attached my 160gb externally & ran gparted...
It throwed me an error *Invalid partition table recursive partition on /dev/sda* but ths 160gb is /dev/sdb? Thus no error in my external HD
Now i deleted all partitions & formated whole of 160gb as ntfs via gparted

 ```
GParted 0.12.1 --enable-libparted-dmraid
 Libparted 2.3
    Delete /dev/sdb1 (unknown, 149.05 GiB) from /dev/sdb  00:00:33    ( SUCCESS )             calibrate /dev/sdb1  00:00:11    ( SUCCESS )             path: /dev/sdb1
start: 34
end: 312,581,772
size: 312,581,739 (149.05 GiB)          delete partition  00:00:22    ( SUCCESS )       ========================================
    Create Primary Partition #1 (ntfs, 149.05 GiB) on /dev/sdb  00:01:02    ( SUCCESS )             create empty partition  00:00:24    ( SUCCESS )             path: /dev/sdb1
start: 2,048
end: 312,580,095
size: 312,578,048 (149.05 GiB)          set partition type on /dev/sdb1  00:00:22    ( SUCCESS )             new partition type: ntfs          create new ntfs file system  00:00:16    ( SUCCESS )             mkntfs -Q -v -L "khan" /dev/sdb1             Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
mkntfs completed successfully. Have a nice day.
             ========================================
```

but even after successful operations this is the bug:
[IMG]http://i.imgur.com/E3pqa.png[/IMG]
So instead of ntfs, gparted shows unknown partition? 
Can this be the problem i cant install Ubuntu while i operate my 160gb externally? 

Output from sudo fdisk -l
```
Disk /dev/sda: 3977 MB, 3977190400 bytes
64 heads, 32 sectors/track, 3792 cylinders, total 7767950 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f7adb25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           0     1800191      900096   17  Hidden HPFS/NTFS

Disk /dev/sda1: 921 MB, 921698304 bytes
64 heads, 32 sectors/track, 879 cylinders, total 1800192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f7adb25

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           0     1800191      900096   17  Hidden HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 160.0 GB, 160041884672 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581806 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   312581805   156290902+  ee  GPT

```
Now I will make it internal & then reply soon

---

### Post by pakki on 2012-12-14
To clear out previous errors i remade partition table using gparted ths time using default msdos method, HD is attached externally...
Made three partitions using gparted in my external HD ...successful but gparted again fail to read its own successfully created partitions?
[IMG]http://i.imgur.com/RYb5I.png[/IMG]
```
 GParted 0.12.1 --enable-libparted-dmraid
 Libparted 2.3
    **Create Primary Partition #2 (ext4, 52.37 GiB) on /dev/sdb**  00:01:14    ( SUCCESS )             create empty partition  00:00:35    ( SUCCESS )             [I]path: /dev/sdb1
start: 198,658,048
end: 308,486,143
size: 109,828,096 (52.37 GiB)[/I]          set partition type on /dev/sdb1  00:00:21    ( SUCCESS )             *new partition type: ext4*          create new ext4 file system  00:00:18    ( SUCCESS )             ***mkfs.ext4 -j -O extent -L "" /dev/sdb1***             [I]Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
3432448 inodes, 13728512 blocks
686425 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
419 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

 [/I]       [I]mke2fs 1.42.5 (29-Jul-2012)
[/I]             ========================================
    **Create Primary Partition #3 (linux-swap, 1.95 GiB) on /dev/sdb**  00:00:58    ( SUCCESS )             create empty partition  00:00:35    ( SUCCESS )             [I]path: /dev/sdb2
start: 308,486,144
end: 312,580,095
size: 4,093,952 (1.95 GiB)[/I]          set partition type on /dev/sdb2  00:00:22    ( SUCCESS )             *new partition type: linux-swap(v1)*          create new linux-swap file system  00:00:01    ( SUCCESS )             ***mkswap -L "" /dev/sdb2***             [I]Setting up swapspace version 1, size = 2046972 KiB
LABEL=, UUID=192177ea-2682-4c6d-8edf-2d35815d656b
[/I]             ========================================
    **Create Primary Partition #4 (ntfs, 94.73 GiB) on /dev/sdb**  00:01:01    ( SUCCESS )             create empty partition  00:00:23    ( SUCCESS )             [I]path: /dev/sdb3
start: 2,048
end: 198,658,047
size: 198,656,000 (94.73 GiB)[/I]          set partition type on /dev/sdb3  00:00:23    ( SUCCESS )             *new partition type: ntfs*          create new ntfs file system  00:00:15    ( SUCCESS )             ***mkntfs -Q -v -L "" /dev/sdb3***             [I]Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
mkntfs completed successfully. Have a nice day.
[/I]             ========================================
  
```

```
mint@mint ~ $ sudo fdisk -l

Disk /dev/sdb: 160.0 GB, 160041884672 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581806 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051053

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       198658048   308486143    54914048   83  Linux
/dev/sdb2       308486144   312580095     2046976   82  Linux swap / Solaris
/dev/sdb3            2048   198658047    99328000    7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

Disk /dev/sdc: 3977 MB, 3977190400 bytes
64 heads, 32 sectors/track, 3792 cylinders, total 7767950 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f7adb25

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           0     1800191      900096   17  Hidden HPFS/NTFS

Disk /dev/sdc1: 921 MB, 921698304 bytes
64 heads, 32 sectors/track, 879 cylinders, total 1800192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f7adb25

     Device Boot      Start         End      Blocks   Id  System
/dev/sdc1p1   *           0     1800191      900096   17  Hidden HPFS/NTFS

```

why the following error:
*Partition table entries are not in disk order*

---

### Post by oldfred on 2012-12-14
> why the following error:
*Partition table entries are not in disk order*
Not an error, just pointing out that sda1 is not first on drive. Not important as partitions can be in any order.

We have seen where Windows partition tools seem to have issues with gpt partitioned drives. It seems to not handle the backup partition table correctly. 
I have used gparted to create gpt partitions on my flash drive, an older 160GB drive and my newer SSD without issue. 

Windows may convert gpt to MBR but leave the backup gpt partition table at the end of the drive. Then Linux tools see both MBR and backup gpt and get confused. Often fixparts is then only way to clear old gpt info.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by pakki on 2012-12-14
So I attached 160gb as internal via 4gb live flash installed linux Mint 14. No partitions were made during install rather opened up gparted in live Mint session 
* new partition table gpt
...& following profile, no problem no nothing (bcz its acting internal)

When after install asked to restart I did so but just it restarted I unplugged my laptop to shutdown. Then pulled out 160gb made it external & boot from it & it did like always...

Now i am writing this in my first boot session while using HD externally what happens after i shutdown or restart i & you both know so i will try my best to put up as much log tht may be helpful...

I just installed gparted ran it & it issued the error:* Invalid argument during seek for read on /dev/sda*  after ignoring it next error *The backup GPT table is corrupt, but the primary appears OK, so that will be used.   *i pressed OKWaiting for gparted to respond...
[CENTER][IMG]http://i.imgur.com/uZ8wU.png[/IMG][/CENTER]
all ok here...further fdisk output
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041884672 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581806 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   312581807   156290903+  ee  GPT

```

so am going to shutdown now what will happen i know that grub rescue f**k
_____________

I am writing this using Win7 because as expected that same unknown filesystem grub rescue thing...
I read somewhere else that following to test whether grub is recoverable or not so I ran the following command set

*ls*
gave me output in following order
(hd0) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)
*set prefix=(hd0,gpt1)/boot/grub*
then
*insmod (hd0,gpt1)/boot/grub/linux.mod*
output was the final disappointment
unknown filesystem

so this means that given the present scenario I willnt be able to run ubuntu from an external independent drive :( I believe that there is nothing else to try...further I also acknowledge that problem may have been at hardware level of my external closure (I mean the electronic chip that converts internal 2.5' HD to be used as external USB) but then mystery remains that why it supported booting for this first time?
[CENTER][IMG]http://i.imgur.com/k3ool.jpg[/IMG][/CENTER]

---

### Post by oldfred on 2012-12-14
If you are using gpt you need a bios_grub partition for grub2 to install correctly. Ubuntu now creates that automatically but when I first installed several versions ago I had to do it before installing. It looks like you do not have one.

       If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

   However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.

            In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

---

### Post by pakki on 2012-12-15
Thnx for replying...

> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted

Now because I have used GPT partition table I can't use fdisk how can I now rebuid Grub using Live cd/usb?
@ [http://zeasite.com/blog/grub-error-fix-rescue-for-windows-xp-vista-7-8-linux/ubuntu/](http://zeasite.com/blog/grub-error-fix-rescue-for-windows-xp-vista-7-8-linux/ubuntu/)

> If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme.

I will not have windows 

> In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

Yes Grub didn't made it or it wasn't visible in Grub but next time I will create this 1mb 'Bios reserved area' ...i came across this I can recall, during installation procedure

> You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

I will try this but as I said fdisk can't operate on GPT how do I get <partition_number>? Is gdisk already installed because I can't install something in live session oldfred? Gdisk also is availble as Win CLI can I use that?

---

### Post by oldfred on 2012-12-15
I always have used gparted to do my partitions on gpt drives. But I download gdisk just to display my gpt drives. I have not used command line since DOS and fdisk then.

       GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

    
       three Linux partitioning tools: the fdisk family [fdisk, sfdisk, and cfdisk], the libparted family [GNU Parted, GParted, Palimpsest Disk Utility, and several others], and the GPT fdisk family [gdisk and sgdisk]. 

    
I also have seen some have issues with Disk Utility on creating partitions, but I do use it when I forget to label my partitions with gparted. I have to have labels to keep some track of what is where.But gpt partitions have both a gpt label & a file system label and I get them confused.

---

### Post by pakki on 2012-12-15
When I was in Live USB session & my hard attached internally » deleted all partitions, write a gpt partition table & ran  installation...
[IMG]http://i48.tinypic.com/1zpqhhy.jpg[/IMG]
during installation
after it had finished I didn't reboot rather opened up gparted
[IMG]http://i49.tinypic.com/2q3afpt.jpg[/IMG]
flags/partitons ok...then
[IMG]http://i46.tinypic.com/35bd0tl.jpg[/IMG]
then
[IMG]http://i48.tinypic.com/dc7af8.jpg[/IMG]

issued shutdown » make my internal HD as external & removed any other USB/CD media

Booted Linux via externally » opened gparted
issues...
[IMG]http://i49.tinypic.com/244s11u.jpg[/IMG]

issued shutdown » proper shutdown » again booted via external HD same error unknown filesytem grub rescue 


Now oldfred is there any other trick or what, I am really tired now. From my side I provided/followed as much as I can. Plz throw something effective at me

---

### Post by pakki on 2012-12-15
after the disappointment i again booted via Live usb, attached my external hard, then invoked gparted to know what is corrupted what not...
[IMG]http://i45.tinypic.com/2dlug7d.jpg[/IMG]

guess what whole of the ext4 partition's gone thats why the grub rescue but why does it goes corrupt justafter first external session

---

### Post by oldfred on 2012-12-15
With gpt partitions you should only have a parted 'boot flag' on an efi partition for booting with UEFI.

You use gparted or others to see bios_grub flag on the 1MB unformatted bios_grub partition. Formatting or other flags then prevent it from working. And in gparted since it is unformatted it will be unknown (or not formatted).

Not sure why when you ran gdisk and parted it did not show partitions?

       In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

    
With gdisk you see efi partition as ef00 and bios_grub as ef02. 

I was thinking I might move my SSD to a new system with UEFI so I did create an efi partition, but with my BIOS boot it is not used.

```
fred@fred-Precise:~$ sudo gdisk -l /dev/sde
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3645 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  Precise
   4        58925056       117229743   27.8 GiB    0700  Quantal

```

---

### Post by pakki on 2012-12-15
Was your reply an information or purposed solution? I am afraid i can't get anything out of it? What u want me to do next, plain english plz

---

### Post by oldfred on 2012-12-15
Make sure you do not have boot flag on the bios_grub, and that it is not formatted.

Try running gdisk again. It may repair just by opening, or you may have to go advanced and then write new table with corrections.

       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by pakki on 2013-01-18
Replying late founding solutions elsewhere....WITHOUT success

Problem wasn't resolved & if someone out there do have this proble try not to waste time figuring out solution. Both Linux Mint & Ubuntu 12.xx share same installer & thus produces same error at same place/point so it must be its generic issue...Fedora 17 & now 18 install & run smoothly with no gliches. 

I have given up on Ubuntu until its installer somehow removes this 'permanent' bug that just halts your installation progress. Am contended with Fedora which at least installs

---

