---
title: "ubuntu-16.04-mini-i386.iso installer throws &quot;isolinux.bin missing or corrupt.&quot;"
date: 2017-02-24
forum: Installation &amp; Upgrades
---

### Post by Rooster2000 on 2017-02-24
I am trying to install Lubuntu 16.04 to my old Asus A6B00L laptop, but keep getting "isolinux.bin missing or corrupt" error when booting from the USB installer.
This same USB installer starts fluently in my ASRock B150M desktop, and I have also wrote it with this computer, under Linux Mint 18.
I have tried to write it with a tool called *USB Image Writer*, as well as with dd:

```
sudo dd if=ubuntu-16.04-mini-i386.iso of=/dev/sdb
```

The USB stick has following partitions written to it:

```
~ $ sudo fdisk -l
...
Disk /dev/sdb: 249,4 MiB, 261488640 bytes, 510720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x69bab23c

Device     Boot Start   End Sectors Size Id Type
/dev/sdb1  *        0 86015   86016  42M 17 Hidden HPFS/NTFS
/dev/sdb2       86016 98303   12288   6M  1 FAT12
```

Based on other posts considering this error message, and the fact that it works on my desktop, I would assume that this is some kind of incompability between laptop BIOS and something on USB installer. I installed Lubuntu 14.04 to this laptop from the same USB stick by using *ubuntu-14.04-mini-i386.iso*. I think I wrote it with *UNetBootin* or dd under Lubuntu 14.04. I might still try this installer from Linux Mint 18 too.

Other than that, any ideas how I could get Lubuntu into that laptop of mine? The reason I am using mini installer in the first place is that the only USB stick this laptop recognizes on bootup is my old 256MB Swissmemory, and that cannot have any other installers but mini. CD/DVD drive of the laptop doesn't work.

---

### Post by Bucky Ball on 2017-02-24
Presuming it's a 32bit machine. A 64bit machine should swallow either, but if 64bit, perhaps try the 64bit installer.

As your machine will not recognise anything but an old 256Gb USB stick, though, one would have to ponder whether there may be something else amiss with that machine's USB.

---

### Post by Rooster2000 on 2017-02-25
I tried *ubuntu-14.04-mini-i386.iso* with dd from Linux Mint 18, but still no luck.
I also tried both *ubuntu-14.04-mini-i386.iso* and *ubuntu-16.04-mini-i386.iso* with dd from Lubuntu 14.04, but no luck either.

I installed *UNetBootin* to my Lubuntu 14.04, but to use it, I should have erased the USB stick, and interestingly, that couldn't be done with *Disks* (or something):

```
Error deleting partition /dev/sdb1: Command-line `parted --script "/dev/sdb" "rm 1"' exited with non-zero exit status 1: Error: Invalid partition table - recursive partition on /dev/sdb.
 (udisks-error-quark, 0)
```

**Edit 2017-02-26**: This was because I tried to remove each partition one by one, instead of just selecting *Format disk*, which erased all the partitions succesfully.

> **Bucky Ball said:**
> Presuming it's a 32bit machine. A 64bit machine should swallow either, but if 64bit, perhaps try the 64bit installer.

It is a 64bit machine. Yeah, why not give it a try too.
**Edit:** Tried it, wrote *ubuntu-16.04-mini-x64.iso* with dd from Linux Mint 18. At least it gives another kind of error message on laptop: "Operating system load error."

> **Bucky Ball said:**
>  As your machine will not recognise anything but an old 256Gb USB stick, though, one would have to ponder whether there may be something else amiss with that machine's USB.

It does recognize these larger USB sticks correctly if they are inserted after boot, it is just that for some reason, it doesn't accept them as bootable ones.

---

### Post by oldfred on 2017-02-25
There was an old bug on isolinux and similar issue on some newer versions.

       in the directory from "isolinux.cfg" to "syslinux.cfg"
[http://ubuntuforums.org/showthread.php?t=2078599](http://ubuntuforums.org/showthread.php?t=2078599)
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

Another suggestion:

 just rename folder on flash drive: isolinux -> syslinux, 
rename the isolinux.bin and isolinux.cfg files in the syslinux folder to syslinux.bin and syslinux.cfg

---

### Post by Rooster2000 on 2017-02-26
> **oldfred said:**
> rename the isolinux.bin and isolinux.cfg files in the syslinux folder to syslinux.bin and syslinux.cfg

If the USB installer is written with dd, I am not able to modify anything in the partition where these files are, as it is write-protected.

```
$ sudo mount /dev/sdb1 /home/user/mount/
mount: /dev/sdb1 is write-protected, mounting read-only

$ sudo mount -o remount,rw /home/user/mount/
mount: cannot remount /dev/sdb1 read-write, is write-protected
```

Is there a way to turn the partition write-protection off? Based on a quick search I didn't find a way to do that.

I did install *UNetBootin* and formatted USB stick with FAT partition, and wrote *ubuntu-16.04-mini-i386.iso* to it, but it doesn't boot at al even on my desktop. There are two options available for the USB sticks (the partition and some UEFI -alternative) but neither of them work, they are loading a bit something from the stick, screen being blank, but then Linux Mint starts normally from the hard disk. I think this is a problem that I had with UNetBootin under Lubuntu 16.04 already, it couldn't create bootable USB sticks from latest (16.04) installer files.

**Edit:** I also tried to write *ubuntu-16.04-mini-i386.iso* with UNetBootin under Lubuntu 14.04, but even that didn't make an USB installer that would boot on this laptop. For this installer I tried those renaming things too:
syslinux.cfg -> x-syslinux.cfg-x
isolinux.cfg -> syslinux.cfg
isolinux.bin -> syslinux.bin
/usr/lib/syslinux/vesamenu.c32 (of Lubuntu 16.04) -> vesamenu.c32

But still it doesn't boot.

---

### Post by Rooster2000 on 2017-03-01
Another aspect to this could be updating the laptop BIOS, but unfortunately it seems that it wouldn't help either.

According to *AsusTek BIOS ROM Easy Flash Utility v1.03*, The BIOS version of the laptop is

```
Platform: A6L
Ver: 0207
Date: 11/07/05
```

On boot, BIOS is defined as:

```
American Megatrends Inc.
BIOS ID: 63-0100-000002-00101111-110705-MONTARA-0ABBD001-Y2KC
```

By following [these]("https://www.asus.com/US/support/FAQ/1008859") BIOS update instructions from Asus website, I found only two BIOS updates for [A6L]("https://www.asus.com/support/Download/3/41/0/7/8/"):

```
2005/12/13
BIOS Ver.0207AS
Solve the bug of can not set 1280x1024 resolution for external display (NEC FE770, ViewSonic 770) on A6Ne/A6L

2005/11/08
BIOS Ver.0207AS
Solve can not set 1280x1024 resolution for external display (NEC FE770, ViewSonic 770) on A6Ne/A6L.

```

Based on the descriptions I guess it wouldn't solve anything considering USB bootup.

---

### Post by oldfred on 2017-03-01
The 2005/2006 time frame was where they started to change BIOS to allow USB booting.
So you may not be able to boot from USB? Or has it worked before.

The work around then for those old systems was to use plop.
 Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)
[https://www.plop.at/en/bootmanagers.html](https://www.plop.at/en/bootmanagers.html)

---

### Post by Rooster2000 on 2017-03-03
> **oldfred said:**
> So you may not be able to boot from USB? Or has it worked before.

> **Rooster2000 said:**
> I installed Lubuntu 14.04 to this laptop from the same USB stick by using *ubuntu-14.04-mini-i386.iso*. I think I wrote it with *UNetBootin* or dd under Lubuntu 14.04.

> **Rooster2000 said:**
> I also tried both *ubuntu-14.04-mini-i386.iso* and *ubuntu-16.04-mini-i386.iso* with dd from Lubuntu 14.04, but no luck either.

> **Rooster2000 said:**
> I also tried to write *ubuntu-16.04-mini-i386.iso* with UNetBootin under Lubuntu 14.04, but even that didn't make an USB installer that would boot on this laptop.

It has booted from USB before, I just don't remember how did I create that USB installer exactly, and cannot replicate it. At the moment I would be happy to create a working installer with *ubuntu-14.04-mini-i386.iso* too*.*

---

### Post by Bucky Ball on 2017-03-03
Try [UNetbootin]("https://unetbootin.github.io/").

---

### Post by Rooster2000 on 2017-03-03
> **Bucky Ball said:**
> Try [UNetbootin]("https://unetbootin.github.io/").

> **Rooster2000 said:**
> I did install *UNetBootin* and formatted USB stick with FAT partition, and wrote *ubuntu-16.04-mini-i386.iso* to it, but it doesn't boot at al even on my desktop. 
...
I also tried to write *ubuntu-16.04-mini-i386.iso* with UNetBootin under Lubuntu 14.04, but even that didn't make an USB installer that would boot on this laptop.

Today I also tried to write *ubuntu-16.04-mini-i386.iso* with UNetBootin and dd under Lubuntu 16.04. When written with dd, it gives this "isolinux.bin missing or corrupt." error. With UNetBootin it just gets stuck with blank screen. I don't know which one gets closer of working.

Here is a collection of all the alternatives I have tried so far. Something might be missing, and I don't remember exactly how did it not work for each of them.

[TABLE="class: grid, width: 900"]
[TR]
[TD][B]Host OS
[/B][/TD]
[TD][B]Write method
[/B][/TD]
[TD][B]Installer
[/B][/TD]
[TD][B]Tested on
[/B][/TD]
[TD][B]Result
[/B][/TD]
[/TR]
[TR]
[TD]Linux Mint 18[/TD]
[TD]dd[/TD]
[TD]ubuntu-16.04-mini-i386.iso[/TD]
[TD]Desktop[/TD]
[TD]Works ok[/TD]
[/TR]
[TR]
[TD]Linux Mint 18[/TD]
[TD]USB Image Writer[/TD]
[TD]ubuntu-16.04-mini-i386.iso[/TD]
[TD]Desktop[/TD]
[TD]Works ok[/TD]
[/TR]
[TR]
[TD]Linux Mint 18[/TD]
[TD]dd[/TD]
[TD]ubuntu-16.04-mini-i386.iso[/TD]
[TD]Laptop[/TD]
[TD]"isolinux.bin missing or corrupt"[/TD]
[/TR]
[TR]
[TD]Linux Mint 18[/TD]
[TD]USB Image Writer[/TD]
[TD]ubuntu-16.04-mini-i386.iso[/TD]
[TD]Laptop[/TD]
[TD]"isolinux.bin missing or corrupt"[/TD]
[/TR]
[TR]
[TD]Linux Mint 18[/TD]
[TD]dd[/TD]
[TD]ubuntu-14.04-mini-i386.iso[/TD]
[TD]Laptop[/TD]
[TD]Doesn't work[/TD]
[/TR]
[TR]
[TD]Lubuntu 14.04[/TD]
[TD]dd[/TD]
[TD]ubuntu-16.04-mini-i386.iso[/TD]
[TD]Laptop[/TD]
[TD]Doesn't work[/TD]
[/TR]
[TR]
[TD]Lubuntu 14.04[/TD]
[TD]dd[/TD]
[TD]ubuntu-14.04-mini-i386.iso[/TD]
[TD]Laptop[/TD]
[TD]Doesn't work[/TD]
[/TR]
[TR]
[TD]Linux Mint 18[/TD]
[TD]dd[/TD]
[TD]ubuntu-16.04-mini-x64.iso[/TD]
[TD]Laptop[/TD]
[TD]"Operating system load error."[/TD]
[/TR]
[TR]
[TD]Linux Mint 18[/TD]
[TD]UNetBootin[/TD]
[TD]ubuntu-16.04-mini-i386.iso[/TD]
[TD]Desktop[/TD]
[TD]Doesn't work[/TD]
[/TR]
[TR]
[TD]Lubuntu 14.04[/TD]
[TD]UNetBootin[/TD]
[TD]ubuntu-16.04-mini-i386.iso[/TD]
[TD]Laptop[/TD]
[TD]Doesn't work[/TD]
[/TR]
[TR]
[TD]Lubuntu 16.04[/TD]
[TD]dd[/TD]
[TD]ubuntu-16.04-mini-i386.iso[/TD]
[TD]Laptop[/TD]
[TD]"isolinux.bin missing or corrupt"[/TD]
[/TR]
[TR]
[TD]Lubuntu 16.04[/TD]
[TD]UNetBootin[/TD]
[TD]ubuntu-16.04-mini-i386.iso[/TD]
[TD]Laptop[/TD]
[TD]Blank screen[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2017-03-03
Have you tried this? I think it is a wrapper around dd.
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

I have not used dd. But usually just use grub to directly boot ISO.
The hybrid ISO for direct dd write have been a standard for quite a while, but I vaguely remember some differences with the mini version.
Have you tried the server version? It only has a few more defaults than the mini, if you do not install any server packages with tasksel.
 [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel) 

[https://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](https://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)

We find many users have issues with one installer or one flash drive. And then a different installer or different flash drive then works.
  Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

### Post by Bucky Ball on 2017-03-04
Well, 'blank screen' suggests a video issue. Have you tried booting and/or installing with the 'nomodeset' option? 

Have [a look here]("https://ubuntuforums.org/showthread.php?t=1613132") and add 'nomodeset'. Proceed. 

Have you done any research on any of these issues, like fixing the black screen? A black screen does not necessarily signify there is anything wrong with the install and you are certainly not the first to get to here. It may signify there is some conflict or problem with video, though.

On the blank screen install, does it boot to a list of option for you to select at boot? If so, choose the first option there, hit the 'e' key, look for the line that ends in 'quiet splash' or one or a combo of those words, add a space after the last word then 'nomodeset'. Follow the instructions at the bottom of the screen to save changes and continues. (Think you hit 'b'.)

It may have nothing to do with this, but unsure that the possibility of a simple video issue has been fully explored ...

---

### Post by Rooster2000 on 2017-05-11
For some reason, I have lost my motivation to solve this problem for now on. We'll see if it comes back at some point.

---

### Post by efflandt on 2017-05-11
The only laptop I have from 2005 is a low end Compaq (32-bit Sempron) that I got from someone when I replaced that with a 2009 Dell laptop. It cannot boot USB flash, but Toshiba laptop from 2006 can, and can also run 64-bit (core-2 duo Intel). I don't know how big the network installer is from [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads) , but maybe you could burn that to a CD and boot that. Of course you will need some sort of networking with Internet access during the install, either Ethernet or WiFi if that works.

I have a little Netgear WNCE2001 wireless bridge that I use when I do not want to or cannot configure WiFi settings when installing Linux, but I don't think Netgear still makes that or WNCE3001 dual-band because I do not even find it on Netgear's website. It uses 5V 1A including its own power brick or alternate USB cable to power it (if your USB provides more than 500 mA USB 1.0 or 2.0 default). Examples: [https://www.ebay.com/p/NetGear-WNCE2001-Wireless-Adapter/141345289](https://www.ebay.com/p/NetGear-WNCE2001-Wireless-Adapter/141345289)

---

### Post by sudodus on 2017-05-16
There are good and bad mini.iso files. Even if they boot, they must match the current packages in the repositories in order to create a working operating system. I suggest that you try the mini.iso files from [http://cdimages.ubuntu.com/netboot/](http://cdimages.ubuntu.com/netboot/).

See this link for more details, [mini.iso, minimal install, netboot iso](https://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730)

Today, May16 2017, I downloaded and tried the current 32-bit and 64-bit 16.04 LTS 'xenial' mini-iso files after *cloning* to a USB pendrive with mkusb-dus, which uses dd under the hood, and they work for me. (I created minimal ubuntu systems in a real computer, a Toshiba laptop.)

After booting into the installed systems, I had to press for example *ctrl + alt + F1* to arrive at a login prompt. This will be fixed, after a window manager, a desktop environment or the Ubuntu Server meta package is installed.

Start from a 64-bit Ubuntu Server iso file, if you want to boot in UEFI mode.

---

