---
title: "Install on old machines with non-bootable CD-drives and no USBs."
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by renegade81 on 2008-04-09
(my very first post)

Hi, everyone!

I've been trying to install Ubuntu Server Edition on an old IBM laptop (760ED) with the following config:
[LIST]
[*]A harddrive (with an old GRUB in the MBR, which is bugging me a bit)
[*]A CD-ROM drive (non-bootable)
[*]No on-board NIC
[*]No USB-ports
[*](2x PCMCIA-slots - incl. a NIC but the BIOS doesn't detect it)
[/LIST]
Oh, and most importantly there's a PS/2-connector for a mouse :lolflag: - that's it!

On another machine I have access to a Winblow$ XP (incl. CD-RW, an internet connection, USBs etc. - but no floppy drive). I have the Ubuntu Server install-CD, and furthermore I'm lucky enough to have an external 2.5" harddrive, so that data is able to be transfered to the IBM-harddrive.

What I've thourght about doing, is to transfer the boot-data to the IBM-drive telling it to start the install from the CD (and then overwriting the newly created boot-data). But how do I do this? I've been reading these posts: [http://ubuntuforums.org/showthread.php?t=28948]("http://ubuntuforums.org/showthread.php?t=28948") and [http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html"), but the difference is, that my IBM-machine doesn't have any OS running on it - it's totaly blank (except for the annoying GRUB in MBR...?!?).

So, my Qs are:
[LIST=1]
[*]How can the MBR be removed from the harddrive (and not destroying the one on my WinXP)?
[*]How do I create a bootable UNIX-system from a Windows-machine?
[*]Is it at all possible to boot a CD from the harddrive? - And how is this done?
[/LIST]
I'm really looking forward to any reply regarding this problem, so that yet another old piece of junk can get it's renascence :guitar:

Best regards,
:: rEneGaDE ::

---

### Post by koshari on 2008-04-09
why dont you try popping the hdd, placing it in a 2.5-3_1/4 adaptor and installing ubuntu on the hdd on a different machine, then sticking it back into the intended machine?

---

### Post by renegade81 on 2008-04-09
I've thought about this, but don't I get problems with the device drivers, when the installation is moved back to the old IBM machine?

Btw. I think that others would also need a guide, if they don't know how to take out their harddrive - or they don't have an adapter for IDE 2.5-to-3.5...

---

### Post by kerry_s on 2008-04-09
if it's that old->
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

yeah you need to use a special linux for specs like those. with 133mhz and 48mb of ram anything you put on it will be slow.
dsl says it can run on 16mb and you can do a poormans install.->
[http://damnsmalllinux.org/wiki/index.php/Category:Installing_DSL](http://damnsmalllinux.org/wiki/index.php/Category:Installing_DSL)

---

### Post by renegade81 on 2008-04-09
Now, how should that solve my problems? I know the site, but it's the process that interests me... Okay let's pretend that the processor is 1THz and the amount of RAM is 1TB :mrgreen:

---

### Post by kerry_s on 2008-04-09
> **renegade81 said:**
> Now, how should that solve my problems? I know the site, but it's the process that interests me... Okay let's pretend that the processor is 1THz and the amount of RAM is 1TB :mrgreen:

okay.

---

### Post by renegade81 on 2008-04-10
I solved the problems my self.. For others whom might be interested, **here is one solution** to this:

First of all, I needed to overwrite the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") of my harddrive with the Smart Boot Manager, which is able to boot up a CD! There are different ways to do this - in this case I got it from the Ubuntu Install CD (it's called sbm.bin and is located in the /install folder). It's also possible to extract it from the ISO with the nice [IZArk]("http://www.izarc.org/download.html") utillity or download it from . I placed it in the folder C:\my_boot
But now I had a problem writing harddrives using Rawrite, so I downloaded the latest [dd for Windows]("http://www.chrysocome.net/dd") from [Chrysocome.net]("http://www.chrysocome.net/"). Here is a direct link to the version I used: [http://www.chrysocome.net/downloads/dd-0.5.zip]("http://www.chrysocome.net/downloads/dd-0.5.zip"). After unpacking (also using IZArk) dd was placed it in the same folder as sbm.bin - i.e. C:\my_boot

If you've done the same as I, follow these instructions:

(You may need to delete all partitions from the destination disk via Start > Control Panel > Administration > Computer Administration > Storage > Logical Disk Manager)

Now, in a command prompt (to get this click the Windows start-button at the bottom left, and select "Run...". Type in "cmd" and press "OK") type: ```
CD C:\my_boot
``` and press enter. Do a: ```
dd --list
``` and identify the drive to boot from. Right-click the mouse and select "Mark". Press the left mouse button to mark up the drive name you've just identified (mine is called "\\?\Device\Harddisk1\Partition0") and right-click the mouse when this is done. **BE VERY SURE _NOT_ TO SELECT A DRIVE THAT CONTAINS DATA THAT YOU WISH TO KEEP!** Now type: ```
dd if=sbm.bin of=
``` right click the mouse and select "Insert". The result in my case was: ```
dd if=sbm.bin of=\\?\Device\Harddisk1\Partition0
``` If you see something like this: ```
rawwrite dd for windows version 0.5.
Written by John Newbigin <jn@it.swin.edu.au>
This program is covered by the GPL.  See copying.txt for details
2880+0 records in
2880+0 records out
```you are done. The drive *should be* able to boot up showing the Smart Boot Manager, from where the option "CD-ROM" is available and thus booting any bootable CD.

Please post more solutions to this problem, so that (almost) any complicated system configuration can get started.

---

### Post by dstew on 2008-04-10
That a good method. You can also make a [SmartBootManager floppy]("https://help.ubuntu.com/community/SmartBootManager"). In a Linux system using the Linux version of dd:```
dd if=sbm.bin of=/dev/fd0 
``` Old laptops with non-bootable CD-ROMs would often have a floppy drive.

---

