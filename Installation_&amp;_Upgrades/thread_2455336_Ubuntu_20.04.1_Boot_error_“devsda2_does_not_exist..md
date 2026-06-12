---
title: "Ubuntu 20.04.1 Boot error: “/dev/sda2 does not exist. Dropping to shell.”"
date: 2020-12-17
forum: Installation &amp; Upgrades
---

### Post by eliefayad on 2020-12-17
[COLOR=#242729][FONT=Arial]I installed Ubuntu 20.04.1 LTS on my old PC (Sony VAIO Fit 15A) using a configured live USB. While installing I kept all recommended settings and did not check the box to download third party applications.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I am completely new to the world of Linux and I wanted to use this PC to get into it.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]That being said, when I boot up my PC and choose "Ubuntu" from the list in the GNU GRUB screen I get the following error:
[/FONT][/COLOR]
> Gave up waiting for root file system devices. Common problems:
     - Boot args (cat /proc/cmdline)
            -Check rootdelay=(did the system wait long enough?)
     - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda2 does not exist. Dropping to a shell!

[COLOR=#242729][FONT=Arial]And then a BusyBox built-in shell appears.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After 4 hours of trying to search online for some solutions and with the lack of experience I have with Linux I wasn't able to neither understand or solve the issue.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Is there any way this can be fixed?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Please let me know what kind of extra information I can supply to make it easier.[/FONT][/COLOR]

---

### Post by Bashing-om on 2020-12-17
Hello eliefayad - Welcome to the forum :D

What procedure did you follow to install ubuntu ? If manually partitioning. did you "set" sda2 as "/"  (that is root)?
Let's begin the discovery by looking at the present partitions.
Boot the live installer in "try ubuntu mode" and activate a terminal.
Post back the results - between code tags - of terminal command:
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Where here we see if sda2 is in fact the root partition - then from that live installer we mount the partition and see what the boot code points to.

[INDENT]small steps for my small mind
[INDENT][INDENT]but, we will get there
[/INDENT][/INDENT][/INDENT]

---

### Post by eliefayad on 2020-12-18
Hello! :D


I installed ubuntu using the recommended settings and I let it do the partitioning automatically.


Here is the output of the command:

```


Disk /dev/loop0: 1.98 GiB, 2103640064 bytes, 4108672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 29.9 MiB, 31334400 bytes, 61200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 54.98 MiB, 57626624 bytes, 112552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 255.58 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 49.8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 946.44 GiB, 1016218828800 bytes, 1984802400 sectors
Disk model: WDC WD10S12X-55J
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 173471B4-2201-4C0A-A6B3-6AB31B577171


Device       Start        End    Sectors   Size Type
/dev/sda1     2048    1050623    1048576   512M EFI System
/dev/sda2  1050624 1984800767 1983750144 945.9G Linux filesystem




Disk /dev/sdb: 7.28 GiB, 7807401984 bytes, 15248832 sectors
Disk model: DataTraveler 2.0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0b010de4


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15248831 15246784  7.3G  c W95 FAT32 (LBA)


```




One more thing that may be worth mentioning is that yesterday I got help from someone and we arrived here while troubleshooting:


 - installation from live usb: blkid doesn't see the partition. it can be mounted and read
 - install method: normal install on freshly wiped disk (we removed all partitions and reinstalled ubuntu again). We tried to do a manual partition before but for some reason (that I don't really quite understand yet) we were not able to assign flags to the partitions so we ended up doing it automatically again.


Unfortunately the person was busy and we were not able to continue.

---

### Post by yancek on 2020-12-18
I would not expect you to see a Grub boot menu with only one operating system installed, but since you do, when you see the Grub menu with Ubuntu highlighted, press the 'e' key to edit the menuentry one time.  When you see the menuentry on the screen, use the arrow keys to go down to a line which begins with the word linux and type in rootdelay=10 (show in example below).  Then continue to boot by using the key combination shown at the bottom of the screen.  This will cause the boot process to delay for 10 seconds and it might be able to find sda2.    

```
linux    /boot/vmlinuz-5.4.0-58-generic rootdelay=10. 
``` 

You might try starting with a larger number if this doesn't help.

If this still fails then go to the step suggested above of mounting sda2 from the Ubuntu live installer and post the output of the menuentry for Ubuntu in grub.cfg.

---

### Post by eliefayad on 2020-12-20
> **Bashing-om said:**
> Hello eliefayad - Welcome to the forum :D

What procedure did you follow to install ubuntu ? If manually partitioning. did you "set" sda2 as "/"  (that is root)?
Let's begin the discovery by looking at the present partitions.
Boot the live installer in "try ubuntu mode" and activate a terminal.
Post back the results - between code tags - of terminal command:
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Where here we see if sda2 is in fact the root partition - then from that live installer we mount the partition and see what the boot code points to.
[INDENT]small steps for my small mind[INDENT][INDENT]but, we will get there
[/INDENT]
[/INDENT]
[/INDENT]


Hello! 
I posted the result of the command. How should I proceed from here?

Thank you for the help!

---

### Post by Bashing-om on 2020-12-20
eliefayad; Hey - :D

As yancek observes the root partition does exist; please follow his directive in post 4 above and advise of the result.

[INDENT]all in the process
[/INDENT]

---

### Post by ActionParsnip on 2020-12-21
If you use UUIDs instead of old /dev/whatever names it'll probably be OK

---

### Post by CatKiller on 2020-12-21
A likely new-user, doesn't boot, issue is that you boot the USB in one mode (Legacy/CSM, say), which installs the OS in that mode, and then try to boot the OS in the other mode (UEFI, in this example). Which then doesn't work.

The bit to pay attention to is whether you've got Legacy/CSM enabled in your UEFI, and whether you're booting the USB in UEFI. You want the modes to match.

You'll also want to make sure that you're using AHCI rather than RAID to access the drive.

---

