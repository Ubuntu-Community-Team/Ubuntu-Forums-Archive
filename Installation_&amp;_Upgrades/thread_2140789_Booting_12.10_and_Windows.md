---
title: "Booting 12.10 and Windows"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by pimaster on 2013-04-30
Hi, I recently fell in love with the beautiful world of open source Linux, however I have several copies of windows I don't want to go to waste. Ideally I would be able to boot 12.04/12.10/13.04 with 7, 8 & xp. I have copies of all three, however last time I tried to install them, I installed them in the order 8, 7, Ubuntu then xp. Windows 8 & 7 shared the windows boot loader and on the grub menu were under Windows 8. I don't mind this but then when I installed xp it took over the Windows 8 boot completely. Should I install them in a different order to ensure they get their own boot loader on grub, installing Ubuntu then after each Windows install use boot repair disk? A couple of notes, all my copies of windows (other than xp) are upgrade copies which I upgrade from xp home (I have 4 copies of xp) and I have enough room for many partitions (1tb hdd)
Thanks all!

---

### Post by darkod on 2013-04-30
Windows combines boot files if you install more than one version, so grub2 has no choice but showing one entry that will then lead you to more windows versions (as second menu choice). Windows uses the boot flag to decide where to put the boot files. So, what you need to do to have all three windows versions separate in grub menu, is this:
1. Boot with the ubuntu cd, open Gparted, and make three ntfs partitions with the sizes you want for your windows OSs. Put a boot flag on only one partition, for example the first one.
2. Boot with the windows media that you want, and install on partition #1. If you plan to upgrade it, do it right away.
3. When that is done, boot ubuntu in live mode again, open Gparted and remove the boot flag from #1, and activate it on #2.
4. Install the windows you want on #2. Again, if you need to upgrade, do it right away while the boot flag is there.
5. Boot ubuntu live mode again and remove the boot flag from #2, activate it on #3.
6. Install the windows version you want there.

That will make sure windows keeps the boot files separate for different versions, and they will be on the corresponding windows partition.
After that install ubuntu, but all ubuntu partitions will need to be logical since you already have three primary ntfs partitions for windows.

Because ubuntu and grub2 don't use the boot flag, it doesn't matter on which ntfs partition you leave it. But if in the future you need to fix the boot process of any windows, you need to put the boot flag on that partition so that the windows repair sees it as only partition with the flag.

---

### Post by oldfred on 2013-04-30
Room is relative with MBR(msdos) partitions and Windows only booting from primary partitions.

If you want separate entries for each copy of Windows install in grub, make each in a primary NTFS partition with the boot flag. Windows always installs its boot loader into the active (boot flag) partition as that is all Windows can boot from. Only one boot flag per drive. Each adds the old install to the BCD in the active. If you installed XP last it does not know about the newer installs, so its boot.ini will have issues.

         To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Then all your Linux & data partitions have to be logical in the one remaining primary partition. You can use 10 to 25GB for each Linux install. 
Then use a large NTFS data partition for any data you want to share with all systems. 
      
 
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by pimaster on 2013-05-01
Will this work with 12.04? Thank you very much for the help!

---

### Post by oldfred on 2013-05-01
I thought you were installing all three versions of Ubuntu. You can install any or all of them. It just is Windows has to have primary partitions.
Linux will boot from logical partitions and data can be in logical partitions. I prefer to make the primary partitions smaller, but NTFS does need up to 30% free, so not too small, and have large data partitions.

---

### Post by pimaster on 2013-05-01
Thanks, say if I need to re-install one of the windows copies, do I format the partition in ntfs, boot from ubuntu cd, set flag as boot, install, run ubuntu boot repair disk, would that work? Also when setting flag boot, can I use gparted bootable disk version? Thanks :)

---

### Post by darkod on 2013-05-01
> **pimaster said:**
> Thanks, say if I need to re-install one of the windows copies, do I format the partition in ntfs, boot from ubuntu cd, set flag as boot, install, run ubuntu boot repair disk, would that work? Also when setting flag boot, can I use gparted bootable disk version? Thanks :)

Yes, that is how you should reinstall windows on any partition. It has to have the boot flag before you start installing, otherwise it will combine the boot files to one of your other windows installations.

I haven't used the gparted live cd but I guess you can use it too to set the boot flag. But since you will have your ubuntu cd you always use that.

---

### Post by pimaster on 2013-05-01
I just find that booting gparted live is quicker than ubuntu installation disk

---

