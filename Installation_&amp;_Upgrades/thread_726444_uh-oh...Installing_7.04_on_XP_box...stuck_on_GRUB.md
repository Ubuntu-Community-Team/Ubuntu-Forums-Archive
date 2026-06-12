---
title: "uh-oh...Installing 7.04 on XP box...stuck on GRUB"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by Ian-on-the-Trent on 2008-03-16
Hi.

I have installed 7.04 on an XP box. The installation from the Live disk appeared to go flawlessly, I deleted the last 5GB partition on an 80GB hard drive and repartitioned it as "/", "swap", "/home". These are all logical partitions since the original windows partition was logical.

When rebooting the following messages appear:
[INDENT][FONT="Fixedsys"][SIZE="2"][B]GRUB Loading stage1.5.

GRUB loading, please wait...[/B][/SIZE][/FONT][/INDENT]

It hangs here.

Does anyone have any suggestions? I am scouring the 'net for solutions.

Thanks,
Ian.

---

### Post by scragar on 2008-03-16
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
try reinstalling grub, it may be broken for some reason.

---

### Post by Pumalite on 2008-03-16
Boot your Ubuntu Live CD and post:
sudo fdisk -lu
df -h
[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5)

---

### Post by Ian-on-the-Trent on 2008-03-16
> **scragar said:**
> [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
try reinstalling grub, it may be broken for some reason.

When I installed Ubuntu, I did not create a partition for "/boot" as I had assumed the installation would have done so. Is this an error on my part? As well, does it matter if Ubuntu is installed on the last 5GB of the 80GB HDD?

---

### Post by Ian-on-the-Trent on 2008-03-16
> **scragar said:**
> [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
try reinstalling grub, it may be broken for some reason.

Thanks for the link unfortunately, neither option (reinstalling grub on the MBR or partition root) worked.

---

### Post by Pumalite on 2008-03-16
It must be quite a tight fit

---

### Post by Ian-on-the-Trent on 2008-03-16
> **Pumalite said:**
> It must be quite a tight fit

What do you mean?

---

### Post by Pumalite on 2008-03-16
Post:
df -h

---

### Post by Ian-on-the-Trent on 2008-03-16
> **Pumalite said:**
> Post:
df -h

ubuntu@ubuntu:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  192K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
tmpfs                 506M   12K  506M   1% /tmp
/dev/hda11            865M   17M  804M   3% /media/disk
/dev/hda9             2.9G  1.9G  793M  72% /media/disk-1
ubuntu@ubuntu:/$

---

### Post by Ian-on-the-Trent on 2008-03-16
Additionally, this is the content of /boot/grub/menu.lst

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=298664e5-20d2-4b47-97e7-2591068dd4d5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=298664e5-20d2-4b47-97e7-2591068dd4d5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Ian-on-the-Trent on 2008-03-16
***And...***

ubuntu@ubuntu:/$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3148739     1574338+   7  HPFS/NTFS
/dev/sda2         3148740    19920599     8385930    7  HPFS/NTFS
/dev/sda3        19920600   156296384    68187892+   f  W95 Ext'd (LBA)
/dev/sda5        19920663    65384549    22731943+   7  HPFS/NTFS
/dev/sda6        65384613   110848499    22731943+   7  HPFS/NTFS
/dev/sda7       110848563   156296384    22723911    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    16482689     8241313+   7  HPFS/NTFS
/dev/hda2        16482690   156296384    69906847+   f  W95 Ext'd (LBA)
/dev/hda5        16482753    20675654     2096451    7  HPFS/NTFS
/dev/hda6        20675718    52130924    15727603+   7  HPFS/NTFS
/dev/hda7        52130988    62621369     5245191    7  HPFS/NTFS
/dev/hda8        62621433   146512799    41945683+   7  HPFS/NTFS
/dev/hda9       146512863   152505044     2996091   83  Linux
/dev/hda10      152505108   154497104      995998+  82  Linux swap / Solaris
/dev/hda11      154497168   156296384      899608+  83  Linux

---

### Post by Ian-on-the-Trent on 2008-03-17
'Morning.

I'm still stuck at the grub loading stage. Any suggestions?

---

### Post by Pumalite on 2008-03-17
df -h is fine. To help you with the rest, I need:
sudo fdisk -lu

---

### Post by Ian-on-the-Trent on 2008-03-17
> **Pumalite said:**
> df -h is fine. To help you with the rest, I need:
sudo fdisk -lu

I'll have to do the above again. I reinstalled Ubuntu but 7.10 instead of 7.04. Same problem though.  Back in 15-30min.*

btw...I can't even boot the computer using a Win98 floppy. An error message concerning not being able to find partition information appears.

---

### Post by Ian-on-the-Trent on 2008-03-17
***Btw Pumalite, thanks for getting back to ***me.

**ubuntu@ubuntu:/$ df -h**
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  192K  506M   1% /dev
devshm                506M     0  506M 


**ubuntu@ubuntu:/$ sudo fdisk -lu**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3148739     1574338+   7  HPFS/NTFS
/dev/sda2         3148740    19920599     8385930    7  HPFS/NTFS
/dev/sda3        19920600   156296384    68187892+   f  W95 Ext'd (LBA)
/dev/sda5        19920663    65384549    22731943+   7  HPFS/NTFS
/dev/sda6        65384613   110848499    22731943+   7  HPFS/NTFS
/dev/sda7       110848563   156296384    22723911    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    16482689     8241313+   7  HPFS/NTFS
/dev/hda2        16482690   156296384    69906847+   f  W95 Ext'd (LBA)
/dev/hda5        16482753    20675654     2096451    7  HPFS/NTFS
/dev/hda6        20675718    52130924    15727603+   7  HPFS/NTFS
/dev/hda7        52130988    62621369     5245191    7  HPFS/NTFS
/dev/hda8        62621433   146512799    41945683+   7  HPFS/NTFS
/dev/hda9       146512863   152505044     2996091   83  Linux
/dev/hda10      152505108   154497104      995998+  82  Linux swap / Solaris
/dev/hda11      154497168   156296384      899608+  83  Linux

---

### Post by Pumalite on 2008-03-17
You have a mix of SATA and IDE. Not good.
Where are you at now? Are you in Ubuntu or did you post from your Live CD?

---

### Post by Ian-on-the-Trent on 2008-03-17
Live CD. I can't boot into anything right now.  XP worked okay with IDE / SATA. Just not good for dual boot?

---

### Post by Pumalite on 2008-03-17
Try first changing the order of boot in BIOS and tell me if you can boot.
The other thing to have handy is a Super GRUB disk. You can boot anything with that:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Ian-on-the-Trent on 2008-03-17
My current boot order is:
1. Floppy
2. CDROM
3. HDD0

I'll look for that super grub disk.

---

### Post by Pumalite on 2008-03-17
I meant change the order of your hard drives.

---

### Post by Ian-on-the-Trent on 2008-03-17
Found SuperGrub but I don't know how to put it onto a floppy. Should I start up an XP based machine to copy to floppy?

I'll have to come back in a couple of hours...I have to feed the family and help with homework. TTYL

---

### Post by Ian-on-the-Trent on 2008-03-17
The SATA drive has never been bootable...quirky XP install...even with downloaded drivers I could never get it to work as the boot drive. So I have always used the IDE.

---

### Post by Pumalite on 2008-03-17
Boot your Live CD aqnd at the Terminal:
sudo mkdir /media/hda9
sudo mkdir /media/hda11
sudo mount -t ext3 /dev/hda9 /media/hda9
sudo mount -t ext3 /dev/hda11 /media/hda11
Get the menu.lst from the partition that contains 'boot' (probably hda9)
cat /media/hda9/boot/grub/menu.lst

---

### Post by Ian-on-the-Trent on 2008-03-17
Must go. I'll be back after jobs are done. Until then...many thanks.
Ian.

---

### Post by Ian-on-the-Trent on 2008-03-18
> **Pumalite said:**
> Try first changing the order of boot in BIOS and tell me if you can boot.
The other thing to have handy is a Super GRUB disk. You can boot anything with that:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Downloaded and copied image to floppy. Rebooted but:
GRUB Loading stage2Read Error...

Still stuck.

---

### Post by Ian-on-the-Trent on 2008-03-18
***And as requested:***
**df -h **
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  192K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
tmpfs                 506M   12K  506M   1% /tmp


**sudo fdisk -lu**
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3148739     1574338+   7  HPFS/NTFS
/dev/sda2         3148740    19920599     8385930    7  HPFS/NTFS
/dev/sda3        19920600   156296384    68187892+   f  W95 Ext'd (LBA)
/dev/sda5        19920663    65384549    22731943+   7  HPFS/NTFS
/dev/sda6        65384613   110848499    22731943+   7  HPFS/NTFS
/dev/sda7       110848563   156296384    22723911    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    16482689     8241313+   7  HPFS/NTFS
/dev/hda2        16482690   156296384    69906847+   f  W95 Ext'd (LBA)
/dev/hda5        16482753    20675654     2096451    7  HPFS/NTFS
/dev/hda6        20675718    52130924    15727603+   7  HPFS/NTFS
/dev/hda7        52130988    62621369     5245191    7  HPFS/NTFS
/dev/hda8        62621433   146512799    41945683+   7  HPFS/NTFS
/dev/hda9       146512863   152505044     2996091   83  Linux
/dev/hda10      152505108   154497104      995998+  82  Linux swap / Solaris
/dev/hda11      154497168   156296384      899608+  83  Linux

---

### Post by Ian-on-the-Trent on 2008-03-18
> **Pumalite said:**
> Boot your Live CD aqnd at the Terminal:
sudo mkdir /media/hda9
sudo mkdir /media/hda11
sudo mount -t ext3 /dev/hda9 /media/hda9
sudo mount -t ext3 /dev/hda11 /media/hda11
...

**Completed the above.**

> **Pumalite said:**
> ...
Get the menu.lst from the partition that contains 'boot' (probably hda9)
cat /media/hda9/boot/grub/menu.lst

**This is the result. I removed the remarks for clarity. Let me know if you would rather see them.**

default         0

timeout         10

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,8 )
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2d68015e-07d0-48f9-b1a2-4dfae7bfb70d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,8 )
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2d68015e-07d0-48f9-b1a2-4dfae7bfb70d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,8 )
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0 )
savedefault
makeactive
chainloader     +1

---

### Post by Pumalite on 2008-03-18
Ev3erything looks fine. It should boot. If not, then you have the ols IDE+SATA mix problem. Take a look at this:
[http://ubuntuforums.org/showthread.php?t=46003](http://ubuntuforums.org/showthread.php?t=46003)

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by Ian-on-the-Trent on 2008-03-18
Would it be worthwhile to disconnect the SATA drive and try booting?

...I just did and the computer was able to boot. Your conclusions were spot on!!

Now I need to figure out what to do next.  I will start a new thread (if needed) to deal with this.

Oh, before I do that, is there a way to uninstall Ubuntu and return my computer to it's original (XP) boot configuration. I think I need to do that before I start tearing things apart again.

Many thanks Pumalite!!

---

### Post by Ian-on-the-Trent on 2008-03-18
Oh yes, and I can boot to either Ubuntu or XP so long as the SATA is disconnected. (Now if I could only uninstall Ubuntu.)

---

### Post by Pumalite on 2008-03-18
I'm glad we found the bug. You can use the same Gparted Live CD and erase Ubuntu (delete partitions). Then fix your Windows MBR with your Installation CD>Recovery>FIXMBR>FIXBOOT. Or with Super Grub: 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
I think one solution for you is to install XP and Ubuntu on the SATA drive and divide the IDE in 2 partitions: one for storage and the other one as a separate /home partition for Ubuntu.(just my two cents woth).

---

### Post by Ian-on-the-Trent on 2008-03-19
Again, many thanks Pumalite.

I certainly will consider your "two cents" worth but that is for another day. I'm glad to be up and running again.  And to wrap up this thread, an excellent guide for removing Ubuntu and getting Windows back is located here:
[HowTo: Remove Ubuntu (& Restore Windows)]("http://ubuntuforums.org/showthread.php?t=508927")

It's very muck like your suggestion although reversed in some ways. In my situation, while in XP I used MbrFix first and once I was rebooted to Windows I deleted, repartitioned, and formatted the space formerly occupied by Ubuntu. (I have XP Pro and used the Disk Management tools.)

When I get my next box built (this will be my sons' gaming PC) I'll permanently acquire the unit we were just working on and get the dual boot working.

Until then.....cheers!

---

### Post by Pumalite on 2008-03-19
Good luck.

---

