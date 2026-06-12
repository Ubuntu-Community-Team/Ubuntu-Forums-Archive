---
title: "error when starting Windows XP"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by Homie Bongo on 2006-08-19
Hello everybody,
so here is my problem: I try to boot my Windows XP from *hda* but it says right after the bios sequence something like: **An error occured during the Windows startup**.

I just installed Ubuntu on *hdc* without *hda* connected and I tried later to add Windows into the *menu.list*. My last try was:
> 
title		Windows XP Professional
root		(hd1,2)
savedefault
makeactive
chainloader +1

which didn't work anyway :) However I can't start Windows now even choosing it from the Bios menu (as I am still used to). My Windows XP is on *hda3* and I am not sure how it used to boot - if there was an bootloader in *hda1* or if it could just boot from its partition. This is beginning of hda (from fdisk -l):
> [FONT="Fixedsys"]
___Device_Boot______Start_________End______Blocks___Id__System
/dev/hda1_______________1___________4_______32098+__83__Linux
/dev/hda2___*___________5_________254_____2008093+__83__Linux
/dev/hda3_____________255________4044____30443175____7__HPFS/NTFS
[/FONT]
I tried having Linux on there - that's why there are some partitions left

Maybe I wouldn't need Windows XP that much, if I had my NTFS partitions accessible (using *ntfs-3g*), but:
> 
sudo mount -a
Couldn't mount device '/dev/hdc3': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down a nd try again.
Mount failed.

Can anybody give an advice how to boot into Windows XP?
Thank you!

---

### Post by Herman on 2006-08-19
Hello, Homie Bongo
If you mean your Windows XP is on your first hard disk (hda), and you installed Ubuntu on your third hard disk (hdc), with (hda) unplugged, then Ubuntu would have written grub to hdc's MBR. So if you are booting with Grub now, you would havew to have hdc plugged in and configured in your BIOS as hda. 
Then you say your Windows XP is on *hda3* (meaning your first hard disk, third partition) and and you are not sure how it used to boot. There may have been an bootloader in [I]hda1.
Now I'm totally confused. :confused:
[/I]
If Windows is on a non-first hard disk (was on a first hard disk but now is moved),I think you need to use a pair of 'map' commands probably, to trick your Windows into thinking it's still on the first partition of the first hard disk. Then I'm not sure whether you'll have some other configuring to do or not. I'm so experienced with Windows.
This help by confused57 might have something useful in it for you. [**Dualboot Two Hard Drives**]("http://www.ubuntuforums.org/showthread.php?t=179902")

If you simply mean Windows is on your first hard disk, and is on the third partition, (hda3), then just try editing your menu.lst like this:
```
title        Windows XP Professional
rootnoverify        (hd0,2)
savedefault
makeactive
chainloader +1
```However, If you mean Windows used to be on number 1 partition on your first hard disk and now it's partition number is changed to number 3, Windows might need some configuring to make it boot as the non-number 1 partition, even if it is still on the first hard disk. I think you have to at least edit boot.ini and tell it it's number3. That will be tricky as it's NTFS, so you can't open it from Ubuntu and write to it, and you can't boot it to edit the file from Windows. You may be able to use [INSERT]("http://www.inside-security.de/insert_en.html") to do that with. I have never tried it, I've only read a little about it.

A  Super Grub Disk is a  really comforting thing to have handy when you are working with booting and bootloaders. It's only  500 kb or so to download, and it's free!  [**Super Grub Disk. **]("http://adrian15.raulete.net/grub/tiki-index.php")
[Super Grub Disk Documentation]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")
Super Grub Disk can boot Windows for you. It can perform some useful tricks for you like [Special Boot]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Special_Boot")  -->[Swap Hard Disk and Boot]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Swap_Hard_Disk_and_Boot")
Or  [Classic Boot]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Classic_Boot")--> **Boot Master Boot Record** (of the other disk if you select it).
Or [Classic Boot]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Classic_Boot")  -->[Boot Partition.]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Boot_Partition")
Super Grub Disk should be able to get it booting (if it's bootable) for you until you fix you grub menu.
Good luck with it. If you need system-specific help, please post again. If you can, it would be nice to see your complete output from 'sudo fdisk -lu' (including all three or more hard disks).
Regards, Herman :D

---

### Post by Homie Bongo on 2006-08-20
Thank you for the links Herman, I will check them out!
This is the complete fdisk output:
> 
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63       64259       32098+  83  Linux
/dev/hda2   *       64323     4080509     2008093+  83  Linux
/dev/hda3         4080510    64966859    30443175    7  HPFS/NTFS
/dev/hda4        64966860   320159384   127596262+   f  W95 Ext'd (LBA)
/dev/hda5        64966923    74220299     4626688+  83  Linux
/dev/hda6        74220363    91634759     8707198+  83  Linux
/dev/hda7        91634823   305845469   107105323+   7  HPFS/NTFS
/dev/hda8       305845533   314890064     4522266    7  HPFS/NTFS
/dev/hda9       314890128   319147289     2128581   83  Linux
/dev/hda10      319147353   320159384      506016   82  Linux swap / Solaris

Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63       64259       32098+  83  Linux
/dev/hdc2           64260    27214109    13574925   83  Linux
/dev/hdc3        27214110   394395749   183590820    7  HPFS/NTFS
/dev/hdc4       394395750   398283479     1943865   82  Linux swap / Solaris

My current Grub is on *hdc* and so in Bios I chose the master disk of second IDE to be booted.

I can see now my menu.list is little complicated. i wrote "root		(hd1,2)" because I added *hda* to the /boot/grub/device.map later - the *hda* wasn't connected and neither it was mapped when i installed Ubuntu. device.map:
> 
(hd0)	/dev/hdc
(hd1)	/dev/hda

I am sorry to be confusing. The *hda* with Windows on it should work by itself. I didn't move Windows or have done anything else with it. However it doesn't work anymore when I choose in Bios to boot from the master disk on first IDE. I am not sure if something could have happened with it because of my menu.list command. Do you think I could have ruined something in the Windows partition with my Grub boot command?

---

### Post by Jonie on 2006-08-20
It won't go :( 

Read my post:

[http://www.ubuntuforums.org/showthread.php?t=239837](http://www.ubuntuforums.org/showthread.php?t=239837)

---

