---
title: "gparted can't find my partition"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by 64mgb on 2007-10-24
This is a long story, but I'll try to be brief.  I just upgraded from Feisty to Gutsy.  During the upgrade I received many errors, mostly saying something to the effect that package "x" couldn't be upgraded because it wasn't installed.  Once it was finally done, I could not boot.  It would get to the startup screen and hang, then finally drop into a BusyBox shell.  Eventually I found that I could boot by entering the grub menu and selecting any kernel except the latest (2.6.22 I think).  But once in Ubuntu, there were no icons in the panel that shows running applications...just "buttons" with 2 dots.

Once I got to this point I decided I would copy off everything I wanted to save and start over.  But when I get to the point of creating partitiions in the install routine, it can't see my partition and won't allow me to create one.  When I run gparted separately (from the live cd) it also cannot find my drive.  But when I restart and run gparted from my Ubuntu installation, it finds my drive (although it does take a while).

So, as it stands, I can't even start from scratch.   Any ideas how I can get around this?

Thanks!

Rich

---

### Post by taurus on 2007-10-24
From the LiveCD, open a terminal, Applications -> Accessories -> Terminal, and post the output of this command here.

```
sudo fdisk -l
```
That's a lower case letter l, not 1.

---

### Post by 64mgb on 2007-10-24
> **taurus said:**
> From the LiveCD, open a terminal, Applications -> Accessories -> Terminal, and post the output of this command here.

```
sudo fdisk -l
```
That's a lower case letter l, not 1.

sudo fdisk -l   executed from a terminal on the live cd returns nothing...it just comes back to the prompt.

Thanks,
Rich

---

### Post by taurus on 2007-10-24
Get into the BIOS and see if it even detects your harddrive in there.

---

### Post by 64mgb on 2007-10-24
> **taurus said:**
> Get into the BIOS and see if it even detects your harddrive in there.

Thanks taurus, but it has to be detecting my hardware if I can boot with an older kernel, and while booted to that kernel gparted can find my drive, right?

Rich

---

### Post by taurus on 2007-10-24
Can you boot from that harddrive with an older kernel?

---

### Post by 64mgb on 2007-10-25
> **taurus said:**
> Can you boot from that harddrive with an older kernel?

Yes...from above  "Eventually I found that I could boot by entering the grub menu and selecting any kernel except the latest (2.6.22 I think)."   It will boot ok with any previous kernel I had installed.  I have just one hard drive, with one partition on it.

Rich

---

### Post by 64mgb on 2007-10-25
Since I can boot to an old kernel, is it possible to do that and then run the install routine from the live CD?

Thanks,
Rich

---

### Post by taurus on 2007-10-25
While running the old kernel, what are the outputs of these two commands from a terminal then?

```
uname -a
sudo fdisk -l
```

---

### Post by 64mgb on 2007-10-25
> **taurus said:**
> While running the old kernel, what are the outputs of these two commands from a terminal then?

```
uname -a
sudo fdisk -l
```

rich@garage:~$ uname -a
Linux garage 2.6.20-16-386 #2 Sun Sep 23 19:47:10 UTC 2007 i686 GNU/Linux
rich@garage:~$ sudo fdisk -l
[sudo] password for rich:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21b221b1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14866   119411113+  83  Linux
/dev/hda2           14867       14946      642600    5  Extended
/dev/hda5           14867       14946      642568+  82  Linux swap / Solaris

Disk /dev/sda: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes
Disk identifier: 0x355a3045

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              21      167680     1005958+   6  FAT16
rich@garage:~$ 


Thanks,
Rich

---

### Post by taurus on 2007-10-25
Try booting your machine with GParted LiveCD and see if you can use it to wipe your harddrives clean.  Then, boot from the Ubuntu LiveCD and try to install Gutsy from it.  

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by 64mgb on 2007-10-25
> **taurus said:**
> Try booting your machine with GParted LiveCD and see if you can use it to wipe your harddrives clean.  Then, boot from the Ubuntu LiveCD and try to install Gutsy from it.  

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Man, this is baffling!  I downloaded the gparted live cd and booted on it.  It found my drive and partitions, so I deleted them and created new ones.  Everything looks great.  I reboot on the Ubuntu live CD, and I get the same thing!  Can't see my drive and partitions!   Argh!

Rich

---

### Post by taurus on 2007-10-25
Have you tried the alternate CD?  Otherwise, post the spec of your machine here.

---

### Post by 64mgb on 2007-10-25
> **taurus said:**
> Have you tried the alternate CD?  Otherwise, post the spec of your machine here.

No, I have not tried the alternate CD.  I'll give that a try tomorrow.  If that doesn't work, what specs do you want?

Thanks for your time taurus - I appreciate it.

Rich

---

### Post by taurus on 2007-10-25
The spec of your machine like mobo, CPU, RAM, video card, harddrive, etc.

---

### Post by 64mgb on 2007-10-26
> **taurus said:**
> The spec of your machine like mobo, CPU, RAM, video card, harddrive, etc.

Man....the alternate CD cannot detect my drive either!  I think I'm going to do some tinkering with the gparted live cd to see I can figure something out, or maybe boot on a DOS floppy and do fdisk and format from there to see what it does.  I went into the BIOS setup and it detects my drive.

I have a PC Chips motherboard with a Celeron 3.06 processor, Maxtor 120GB hard drive (IDE, NOT SATA), 256MB RAM, the video is onboard the motherboard (don't remember the driver but can get it if needed), in fact the network, video, and sound are all on the motherboard.  Anything else?

Since I wiped out my partitions with the gparted live CD I can't boot at all now, but it does get to where it says "Starting grub", but then stops with error 17.

Thanks,
Rich

---

### Post by 64mgb on 2007-10-30
OK...I finally got Ubuntu (actually Kubuntu) reinstalled on this machine.  I couldn't get it to do anything with Ubuntu 7.10, either from the Live CD or from the Alternate CD.  I even tried a different hard drive...no luck.  So I finally decided to try loading Windows 2000 just to make sure the hardware was ok.  That loaded fine.  So, I had a Kububtu 7.04 Live CD laying around and decided to try that.  It loaded fine.  When I went to bed last night it was still working on upgrading to 7.10...I'll let you know how that ends up.  If that goes ok, I'll try starting over and download the Ubuntu 7.04 Live CD and try loading that, then upgrading from there (this is the same process I tried initially that caused my problems, but will try again with a fresh install of 7.04).

So, it looks like there is some sort of compatibilty problem between Ubuntu 7.10 and my hardware.

Rich

---

### Post by pxwpxw on 2007-10-30
**64mgb**

Some people have had problems with Gutsy not loading the ide drive modules.

If you finish up back at an (initramfs) prompt, you can check what ide modules are loaded by
```

(initramfs) cat /proc/modules | grep ide
## or just 
(initramfs) cat /proc/modules
#### and possibly load what is needed by
(initramfs) modprobe ide-drive
(initramfs) modprobe ide-cd
(initramfs) modprobe ide-core
(initramfs) exit

```
Which may, or may not, be your problem.

The same issue may stop the 710 Live CD.

---

### Post by 64mgb on 2007-10-30
> **pxwpxw said:**
> **64mgb**

Some people have had problems with Gutsy not loading the ide drive modules.

If you finish up back at an (initramfs) prompt, you can check what ide modules are loaded by
```

(initramfs) cat /proc/modules | grep ide
## or just 
(initramfs) cat /proc/modules
#### and possibly load what is needed by
(initramfs) modprobe ide-drive
(initramfs) modprobe ide-cd
(initramfs) modprobe ide-core
(initramfs) exit

```
Which may, or may not, be your problem.

The same issue may stop the 710 Live CD.
Thanks pxwpxw - I'll refer to this if I have issues when I retry.

Rich

---

### Post by 64mgb on 2007-10-30
OK...I tried these command from a terminal after starting the Ubuntu 7.10 on the Live CD:

modprobe ide-drive
modprobe ide-cd
modprobe ide-core

It couldn't find ide-drive, but seemed to load ide-cd and ide-core ok.  Same problem.  Now I'm going to try loading 6.06 and see if I can upgrade to 7.10 (possibly through 6.10 and 7.04 first?).  I wish I had a 7.04 Live CD, but the only one I have is for my MythTV box that has an AMD 64 bit processor.

Rich

---

### Post by pxwpxw on 2007-10-31
> **64mgb said:**
> OK...I tried these command from a terminal after starting the Ubuntu 7.10 on the Live CD:

modprobe ide-drive
modprobe ide-cd
modprobe ide-core

It couldn't find ide-drive, but seemed to load ide-cd and ide-core ok.  Same problem.  Now I'm going to try loading 6.06 and see if I can upgrade to 7.10 (possibly through 6.10 and 7.04 first?).  I wish I had a 7.04 Live CD, but the only one I have is for my MythTV box that has an AMD 64 bit processor.

Rich

I got my modules wrong, the ide group were as found in apple ppc. Now checking on a i386 PC running Feisty704 with ide drives, there are no ide modules listed  (although some are available).

```

admax@oldibm:~$ uname -a
Linux oldibm 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686 GNU/Linux

admax@oldibm:~$ lsmod | grep ata
ata_piix               15620  3 
ata_generic             9092  0 
libata                125848  2 ata_piix,ata_generic
scsi_mod              142220  5 sbp2,sg,sr_mod,sd_mod,libata

```
Module piix is also available, don't know what it does exactly.
```

admax@oldibm:~$ sudo modprobe piix
admax@oldibm:~$ lsmod
Module                  Size  Used by
piix                   10756  0 [permanent]

``` 
Then for sata the situation is different.

The easiest way to see what is relevant is to run lsmod for something that works, and then compare results for the full list. Depends on the kernel configuration.

Hope you find an answer.

---

### Post by 64mgb on 2007-10-31
Well, I finally have Gutsy working on this box, although not entirely.  I found a place to download the Feisty live cd, so I did that and started from scratch with Feisty.  That all went well, so I then upgraded to Gutsy.  The upgrade went fine, but now when I boot, it goes to the splash screen for a while, then drops into a BusyBox shell with an initramfs prompt.  I can boot to the kernel that was installed with Feisty (2.6.20-16-generic), which is where I'm at as I write this.

I wonder what would happen if I downloaded the latest kernel and compiled it?

Rich

---

### Post by pxwpxw on 2007-11-01
> **64mgb said:**
> Well, I finally have Gutsy working on this box, although not entirely.  I found a place to download the Feisty live cd, so I did that and started from scratch with Feisty.  That all went well, so I then upgraded to Gutsy.  The upgrade went fine, but now when I boot, it goes to the splash screen for a while, then drops into a BusyBox shell with an initramfs prompt.  I can boot to the kernel that was installed with Feisty (2.6.20-16-generic), which is where I'm at as I write this.

I wonder what would happen if I downloaded the latest kernel and compiled it?

Rich

A good question, but I.m guessing, the same thing.

While feisty is running, I would get a full listing of modules with lsmod, and then when gutsy goes to (initramfs) cat /proc/modules and compare to see what differs.

You can also add "break=bottom" to the kernel comandline to see what feisty is loading at the (initramfs) stage.

 I doubt if my module suggestions above are correct, there may be other modules for your system.

I dont know if there is any later kernel likely to fix this, maybe.

If you find there are missiing modules, then it is possible to update-initramfs to include the module at startup.

I would also have a good search in the forum, because there have been various problems with gutsy, in addition to modules, you are not alone. Thats about all I can suggest.

---

### Post by 64mgb on 2007-11-01
> **pxwpxw said:**
> A good question, but I.m guessing, the same thing.

While feisty is running, I would get a full listing of modules with lsmod, and then when gutsy goes to (initramfs) cat /proc/modules and compare to see what differs.

You can also add "break=bottom" to the kernel comandline to see what feisty is loading at the (initramfs) stage.

 I doubt if my module suggestions above are correct, there may be other modules for your system.

I dont know if there is any later kernel likely to fix this, maybe.

If you find there are missiing modules, then it is possible to update-initramfs to include the module at startup.

I would also have a good search in the forum, because there have been various problems with gutsy, in addition to modules, you are not alone. Thats about all I can suggest.

Thanks pxwpxw - I appreciate you spending time on this. I'll try looking at the modules tonight and see what it says.  The one suggestion that I don't know how to do is to 'add "break=bottom" to the kernel comandline to see what feisty is loading at the (initramfs) stage'.  How do I do that?

Rich

---

### Post by pxwpxw on 2007-11-02
> **64mgb said:**
> Thanks pxwpxw - I appreciate you spending time on this. I'll try looking at the modules tonight and see what it says.  The one suggestion that I don't know how to do is to 'add "break=bottom" to the kernel comandline to see what feisty is loading at the (initramfs) stage'.  How do I do that?

Rich

When the grub menu comes up (or if hidden, escape will bring it up), see the messages - "e" will let you edit the text at the end of the kernel line.

delete any "quiet splash"

add break=bottom

hit enter then "b" to boot

The edit does not get saved,
from (initramfs) you can exit or reboot

---

