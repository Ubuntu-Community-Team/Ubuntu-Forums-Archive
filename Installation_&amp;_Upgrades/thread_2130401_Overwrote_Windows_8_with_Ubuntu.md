---
title: "Overwrote Windows 8 with Ubuntu"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by Mr Coffee on 2013-03-29
I apologise about this being mostly about Windows, but do need some help.

I first had a Windows 8 64bit installation (pre-installed) and wanted to install Ubuntu on this laptop. But i was stupid and didn't doublecheck and i've now overwritten my Windows 8 installation with Ubuntu 64bit. Which normally would be fine, but i need some Windows applications for work, and really want to get it back. 
Since i've still got my Windows 8 code, i thought i could just re-download an iso and install and use my code to activate it. Nopp, i can't. I disabled secure boot (and uefi?) to be able to install Ubuntu, but now i can't install Windows 8. I made a seperate partition for it, but it said it couldn't install into a GPT partition, even though i selected a Windows 8 64bit iso. This is what my partitions look like right now;
[http://i.imgur.com/lacbP4w.png](http://i.imgur.com/lacbP4w.png)

Now i'd love to be able to keep my Ubuntu, and i realise that if i do manage to install Windows 8 i have to fix grub through boot-repair and i know how to that. It's just that i don't know how to figure out how to re-install Windows 8 since i overwrote it. Any help would be greatly appreciated!

Cheers

---

### Post by oldfred on 2013-03-29
I do not know if standard Windows installer works with UEFI or not. But everyone has said you have to boot installer in UEFI mode to install in UEFI mode. Windows will only boot in UEFI mode when drive is gpt partitioned.

You still have the msres or Microsoft reserved partition which must be just before the main Window NTFS partition. You cannot have Ubuntu inbetween.

Windows has specific requirements for partitions.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)
Older Windows info on gpt - 2008 updated 2011 for Windows 7
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

Some threads where users show partitions
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)

And if you look at the BootInfo reports from any of the UEFI threads you will see the partitioning those users have.

Some older info on UEFI with WIdnows 7.
 Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by Mr Coffee on 2013-03-29
So stupid question, but how do i move the partition, specifically so the msres and the ubuntu one swap around, as you suggested?
Also, i can't find any UEFI settings at all in my bios, which is what makes it weirder. I can set it to boot legacy mode, disabled fast boot and secure boot, but still nothing that says uefi or anything. Still feel a bit lost.

---

### Post by darkod on 2013-03-29
If you are willing to also reinstall ubuntu, I would actually do it another way. The computer came with win8 and gpt partition table on the disk, which has never changed so far. So, if you booted the win8 dvd in legacy mode, it will not install on gpt.

BUT, making a legacy dual boot is MUCH, MUCH BETTER and easier than uefi dual boot. So, if you don't mind reinstalling ubuntu, I would backup any data from it, boot with the ubuntu cd in live mode, write a new blank msdos table on the hdd.
Then install win8 in legacy mode (make sure to keep the bios setting to boot in legacy mode only) making a partition on the hdd with the size you want for win8 (don't let it take the whole disk).
After that is done, boot with the ubuntu cd and install it.
Now you have legacy dual boot.

Making an uefi dual boot still has many issues and even if you do install win8 in uefi mode, you will still need to do the same for ubuntu, and hope it works out fine. Legacy dual boot works great.

---

