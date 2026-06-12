---
title: "Installing Windows on an Ubuntu only machine"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by NJD on 2006-08-13
Hi, i had an installation of Windows XP on my machine dual booting with Ubuntu. I at one point, while finding my feet with the new OS changed the drive that contained Windows to ext3 and subsequently erased my windows installation =D> . My question is, if i reinstall windows onto that partition, after changing the file table back to FAT will the existing startup dual boot option work once again? The dual boot screen has windows on it despite the fact that it is currently wiped from the PC.

Many thanks for any guidance.

Regards,

Nathan.

---

### Post by carney1979 on 2006-08-13
Your grub (dual-boot) screen still has Windows on it because your /boot/grub/menu.lst file still has the boot info for Windows.

Yes, you can reinstall Windows back to it's original partition. But you need to be very careful to install it to it's original partition, and not your current Ubuntu partition.

Also, when you reinstall Windows, it will overwrite your hard drive's MBR (Master Boot Record) so you can no longer boot into Ubuntu. It will appear that Windows has "reclaimed" your complete hard drive. But if you were careful not to overwrite your Ubuntu partition, then you can set it all right again by using a rescue CD and doing a "grub-install /dev/hda" from a command prompt, or whatever your drive's designation is.

Best of luck!

David

---

### Post by NJD on 2006-08-13
Ah excellent, Thanks for that!! so i literally just pop in the Live CD and drop into terminal and run grub-install /dev/hda then all will be well? forgive me, i'm a real Linux novice - i can follow directions well but i'm still figuring a lot of things out with it.

---

### Post by carney1979 on 2006-08-14
Sorry for a lack of a timely reply. We had a big family outing today.

It's late now (in the USA, EST). I need to sleep, then I will experiment and find the easiest solution for you.

I will hopefully post an answer by early afternoon, my time.

David

---

### Post by carney1979 on 2006-08-14
NJD:

Do me a favor and open a terminal and post the output of:

```
sudo fdisk -l
``` 

(note that -l is a lowercase -L)

David

---

### Post by Squirrelking on 2006-08-14
Hi sorry for hijacking but I thought I may as well post here as I have a similar problem. I have a clean boot Ubuntu 6.06 but need XP for use using wireless adaptors (not supported under Ubuntu and unfortunately I will be at sea without any other internet access for the next 3 months so cant mess about with tweaking and such)

Anyway my output for the last code was: 
> 
Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3495    28073556   83  Linux
/dev/hda2            3496        3648     1228972+   5  Extended
/dev/hda5            3496        3648     1228941   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         258     2072353+   b  W95 FAT32
/dev/sda2             259       19456   154207935    f  W95 Ext'd (LBA)
/dev/sda5             259       19456   154207903+   7  HPFS/NTFS


Second disk is USB so useless for booting. I have a copy of Qparted installed and I'm ready to partition enough space for a minimal XP install. After that it seems it gets complicated though...

Cheers, and sorry again for the hijack

---

### Post by carney1979 on 2006-08-14
Squirrelking

Try modifying your grub menu file (as root or via sudo) so you have an entry for WinXP on the USB drive that looks like this:

title  Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root  (hd1,0)
makeactive
chainloader +1

This may allow you to boot WinXP from the USB drive. If it doesn't work, it may be because you need to modify the hd1 in all three places due to the drive being a sata drive.

I'm not sure what you'd have to change it to, but do a bit of research and you'll find it.

Give the above example a go first, though. MAKE SURE YOU DO NOT MODIFY THE ENTRY THAT BOOTS LINUX.

Best of luck.

David

---

### Post by confused57 on 2006-08-14
> **Squirrelking said:**
> Hi sorry for hijacking but I thought I may as well post here as I have a similar problem. I have a clean boot Ubuntu 6.06 but need XP for use using wireless adaptors (not supported under Ubuntu and unfortunately I will be at sea without any other internet access for the next 3 months so cant mess about with tweaking and such)

Anyway my output for the last code was: 


Second disk is USB so useless for booting. I have a copy of Qparted installed and I'm ready to partition enough space for a minimal XP install. After that it seems it gets complicated though...

Cheers, and sorry again for the hijack
It's very difficult to get Windows to boot, if it is located on a partion located after the Ubuntu partition.  I've only seen a couple of other posters who have had success doing so.  You could install Windows on a partition after Ubuntu, then reinstall grub using the Live CD:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
As I mentioned, it more than likely wouldn't dualboot that way...but if you want to try.
It would probably be best to install Windows on the first partition and reinstall Ubuntu on a partition located after the Windows install.

Edit:  The suggestion given by carney1979 may work, worth a try.

---

### Post by Squirrelking on 2006-08-14
cheers guys, I'll get my mate who is a little more ubuntu savvy to give me a hand and see how it works out, great help :)

---

### Post by punong_bisyonaryo on 2006-08-14
Good day!

I'been an Linux user since Breezy Badger. Save for wine to use some essential applications (just about to try it) and using the NDIS wrapper to install some drivers (need more info on this), I am almost completely migrated to Linux from Windows.

However, it seems that Dapper Drake seems to have lost the control that I have over my Linux box, making it a bit too similar to Windows in terms of control (or rather the lack of). New stuff has been added indeed. But say, for the screensaver, I can't select which screensavers go into random anymore. I have no idea how to set my system time to either GMT or local time. I've just upgraded to Dapper Drake, and I've yet to figure out how much more of the control that is lost.

---

### Post by kbsuperstar on 2006-08-14
Wow, I made my own thread with the same problem in "Absolute Beginner Talk," but no one is responding. Maybe you can help me, carney1979? My computer has only Ubuntu 6.06 Dapper on it, and I'd like to resize the partition for Ubuntu so I can dedicate 5GB for Windows XP.  I have GParted and the GParted live CD, but on GParted it doesn't allow me to shrink my /dev/hda1, which is currently partitioned entirely for Ubuntu. With the live CD, i try to boot but all it says is "hw_random not detected," or something like that.

sudo fdisk -l brings up the following

```
Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3497    28089621   83  Linux
/dev/hda2            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11549    92759310    b  W95 FAT32
/dev/sda2           11549       11694     1164681+  82  Linux swap / Solaris
/dev/sda3           11694       12188     3976087   83  Linux

```

You might notice that sda1 is already partitioned for Windows and is formatted in FAT32, but that's 'cause it's actually an external HD (mass USB storage device) where I keep all my music, videos, and pictures. I can't boot from this drive, so I don't want to resize it.

The internal HD is what I want to repartition. It's like 30 GB and currently it's all partitioned for Ubuntu.

Do I need some certain software or apps to resize the Linux partition, or might I be able to use the Windows XP installer disk or the Ubuntu live CD??

I'm trying to repartition a small bit for Windows just 'cause Ubuntu can't recognize my network printer and Wine sucks for playing games online ](*,) 


Any advice would be helpful. Thanks!

---

### Post by kbsuperstar on 2006-08-15
```

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2860    22972918+  83  Linux
/dev/hda2   *        2861        3497     5116702+   c  W95 FAT32 (LBA)
/dev/hda3            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11549    92759310    b  W95 FAT32
/dev/sda2           11549       11694     1164681+  82  Linux swap / Solaris
/dev/sda3           11694       12188     3976087   83  Linux

```

Now I need to be able to boot with GRUB, but it only boots in windows. How do I reinstall GRUB? I tried ```
sudo /sbin/grub-install /dev/hda
sudo /sbin/grub-install /dev/hda1
sudo /sbin/grub-install /dev/hda2

```

but I just keep getting this error

```
Could not find device for /boot: Not found or not a block device.
```

HELP!

---

### Post by carney1979 on 2006-08-16
>    Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2860    22972918+  83  Linux
/dev/hda2   *        2861        3497     5116702+   c  W95 FAT32 (LBA)
/dev/hda3            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris
 
Wow. I've never seen a setup with part of a Linux install, then Windows, then the rest of the Linux install.

Sorry, it looks to be beyond my ability.

I would have thought grub-install /dev/hda would have done it....

Sorry.

David

---

### Post by NJD on 2006-08-17
ok, this is my mess of a hard drive, is there any way you can help? sorry for the late reply and thanks for all the help thus far ;-)

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         851     6835626    f  W95 Ext'd (LBA)
/dev/hda2   *        1892        4865    23888623+   c  W95 FAT32 (LBA)
/dev/hda3             852        1891     8353800   83  Linux
/dev/hda5               2         802     6434032+   b  W95 FAT32
/dev/hda6             803         851      393561   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by NJD on 2006-08-17
Windows was originally on HDA3

---

### Post by carney1979 on 2006-08-17
NJD:

You may want to print these instructions before starting, so you'll have them for future reference.

Here's what you need to do.

Reinstall Windows, making **_very_** sure **_not_** to wipe out your Ubuntu installation.

Pop in your Ubuntu Live CD and reboot. The Live CD should boot. If not, you may need to adjust your disk drive boot order in your computer's bios.

Once you have booted onto the Live CD's desktop, open a terminal (Applications >> Accessories >> Terminal, if you use the Live CD with Gnome).

In the terminal, type in:

```
sudo mount /dev/hda3 /mnt
sudo chroot /mnt
``` 
You should not need a password. This will actually mount your Linux file system on your hard drive and make it active. Any further commands that you type will be run from your Linux partition on your hard drive.

Next, type in:

```
sudo grub-install /dev/hda
``` 
Finally, type in:

```
exit
``` 
...or maybe:

```
sudo exit
``` 
...if just "exit" doesn't work.

Reboot the machine, removing the Live CD when prompted.

Hopefully, you will see the familiar grub menu when you reboot. 

If you've changed nothing else, you should be able to boot into Windows or Linux as before.

Best of luck! Let me know how it went.

Sincerely,

David

---

