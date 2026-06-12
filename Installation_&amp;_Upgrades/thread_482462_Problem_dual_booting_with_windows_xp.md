---
title: "Problem dual booting with windows xp"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by Whimar on 2007-06-23
Hi there,

I have recently tried installing ubuntu in a dual boot configuration with windows XP media center edition.  Windows is installed on the hard disk as the first partition and I installed Ubuntu in the remaining free space at the end.

Ubuntu installed flawlessly and grub was set up with options to boot both OS.

However, when I try to boot into windows I get this error:

```
Windows could not start because the following file is missing or corrupt:

<windows root>\system32\ntoskrnl.exe

Please re-install a copy of the above file
```

The only way I have been able to get back into windows is to boot windows xp install CD goto recovery console and FIXMBR

I'm not sure if this is a problem with my motherboard (abit ab9-pro)

But I get exactly the same problem with OpenSUSE also

I hope someone can help, thanks in advance!

---

### Post by viciouslime on 2007-06-23
Uh-oh... I'm afraid that's an extremely serious error message. Did you resize the windows partition? It sounds like you probably did, and it also sounds like you didn't defrag it first.

Unfortunately, it looks like you've corrupted the partition, I hope you didn't have any important data on there that you hadn't backed up! The only realistic solution is to format the partition and reinstall windows.

---

### Post by Whimar on 2007-06-23
I dont think my initial explanation was clear

I didn't resize the partition and the drive had been degragmented.  

There is no corruption to the partition as it works fine if I do a FIXMBR from the recovery console.

I think there is a problem with the way that GRUB is booting windows, but I'm not smart enough to know what :P

---

### Post by merlinus on 2007-06-23
Try SuperGrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by Whimar on 2007-06-24
> **merlinus said:**
> Try SuperGrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

What will superGrub offer me?

I have never used it before, what are the advantages?

---

### Post by merlinus on 2007-06-24
Did you read the SuperGrub page at the link I posted?

At the very least, it should let you boot both windows and ubuntu, and help to set up grub to do it from a menu.

-merlin

---

### Post by shrimphead on 2007-06-25
bump.

having the same problem with Ubuntu studio 7.04 and Windows XP on my partners machine

did this fix the problem?

---

### Post by madzieph on 2007-06-25
check out my experience [here]("http://ubuntuforums.org/showthread.php?t=482051")... 

might give you some idea.

---

### Post by Whimar on 2007-07-01
Still can't resolve this issue sadly :(

---

### Post by Pumalite on 2007-07-01
'Missing file' is a known bug of XP in dual boot. Check the Windblows site.

---

### Post by McBrain on 2007-07-08
Any solution known to this? I have the same problem with my new PC!

I rescued the MBR before I installed Kubuntu (the second time, because I have some more problems), so writing the MBR back boots Windows as usual!

Thanks & regards
McBrain

---

### Post by Arrdee on 2007-07-08
If you didn't defrag before you resized Windows, then you may have screwed something up. If you did everything right, keep in mind that you may just have to update boot.ini to correctly boot the right partition. This can happen if you've resized or moved the partition around on the drive. You can use a Windows recovery disk to fix the boot.ini (I think from the recovery console it's [b]bootcfg /rebuild[/b )], or you could try to mount the Windows partition in Linux and edit it with a text editor.

The link a few posts up should have some details to follow.

---

### Post by McBrain on 2007-07-08
The recovery is not the problem, as I just wrote back my before backuped MBR.

No, I did not rezise anything! Absolute clean reinstall of everything, first Windows and then Kubuntu! The partition I created before with the Kubuntu-LiveCD and installed then Windows in the first partition!

---

### Post by Whimar on 2007-07-20
No Solution tot he problem still.  This is driving me crazy!

---

### Post by Whimar on 2007-07-29
Anyone?

---

### Post by jarlz0r on 2007-09-09
I hade the same problem (ntoskrnl.exe...) caused by **trying to start Windows via GRUB**. I found some great help in this guide: [http://ubuntuforums.org/showthread.php?t=208951](http://ubuntuforums.org/showthread.php?t=208951)
Most of the steps are... weird, but the following worked for me:

* Make sure your Windows-partition is mounted. Let's assume it's mounted as /media/windows with write-support. ("mount -t ntfs-3g /dev/WINDOWSPARTITION /media/windows")

* Run "df /", check what your root partition is named. In my case, "/dev/sda2              6823216   4554836   1921780  71% /" showed up, meaning "/dev/sda2" is my root partition.

* Install GRUB to the root-partition: "sudo grub-install [root-partion]"
(which in my case meant running "sudo grub-install /dev/sda2")

* Copy the first 512 bytes of the root-partition, so Windows has something to run: "sudo dd if=[root-partition] of=[windows-partition]/ubuntu.lnx bs=512 count=1"
("sudo dd if=/dev/sda2 of=/media/windows/ubuntu.lnx bs=512 count=1")
Change the "of="-parameter if you need to save the file elsewhere, but make sure it ends up as "C:\ubuntu.lnx" when you want to try booting Ubuntu!

* Add Ubuntu as an option to boot.ini: This can be done either from Linux, if the Windows-partition is mounted with write-support, or from Windows after you've run "fixmbr".
Suppend the line 
c:\ubuntu.lnx="Ubuntu Linux"
to the boot.ini-file. It should now look something like this:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\ubuntu.lnx="Ubuntu"

* Reboot your computer, boot from the Windows install-disc, press "R" for the recovery console, if prompted select your windows install, run "fixmbr" (and perhaps "fixboot". This probably isn't necessary though).

* You should now be able to start either Windows or Ubuntu from the boot-menu (unless you skipped the boot.ini-editing earlier).


This didn't mess anything up for me, but you should be aware that everything might explode, so backup your data!
Also, please note that this method allows for entering GRUB via the Windows boot-menu and vice versa ad infinitum. When having passed through these loops it's not possible to boot Windows, probably due to the underlying cause of the problem :)

---

### Post by brad_c6 on 2007-09-23
Thank you so much, i have a I965 chipset and this has been bothering me for weeks,;)

---

### Post by poltiser on 2007-09-23
I use U7.04 (AMD64)+ Debian 4.0 (AMD64)+ WXP Home (32) on Intel Dual Core with hybryd new motherboard. I deal with partitions and boot using Acronis Disk Director and Os selector. Grub is nice but it does make mistakes often. With Acronis partitioning and booting is safe. I found free extention for XP making ext3 format usable in WXP... Try. I needed to change the order of disks and partitions in Grub - made it each time I was installing Linux but thanks to Os selector WXP started each time easy...
Good luck!

---

