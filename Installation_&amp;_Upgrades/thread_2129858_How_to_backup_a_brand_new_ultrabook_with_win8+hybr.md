---
title: "How to backup a brand new ultrabook with win8+hybrid ssd?"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by balthus666 on 2013-03-27
Hello all,

This is my first post here. I've been using ubuntu since 6.0 and I can't go back to windows anymore :)
I just bought a brand new samsung NP540U (500GB HD+24GB ssd) with windows8 already installed.
I've already read few posts regarding installing and configuring thee disk.
Since I'm not sure I can successfuly make a dual boot, I would like to know if there is a good way to backup things from the harddrive.
There are few partitions :windows, recovery, efi, unknown on ssd... 
What would be the best way to backup things if I want to restore it as it was from the shop?

I'm currently backuping the whole disk (sda+sdb) with clonezilla, but will it be useful later? Can I recover partition this way?
What about the raid between the HD and the SSD. Many posts says that the first thing is to remove it, so how can it be backuped/restored? Will the full disk clonezilla image sufficient?

Thanks for your help :) As soon as I know how to proceed in a safe way, I can get rid of windows 8 (which I find even worst than other previous windows version).

Regards,

---

### Post by sudodus on 2013-03-27
Welcome to the Ubuntu Forums :-)

I'm using ***Clonezilla*** too, and it can backup whole drives, but I would check it with new kinds of partition tables, at least check at the Clonezilla web site, but ideally perform a restore operation to another drive and try to run your computer from that drive.

Another method, that will definitely work, is to make a clone or image with ***dd***. This is a very powerful but also very risky tool. It is nicknamed 'data destroyer', because a small mistake will destroy the data on a drive beyond recovery. There is no double-checking ...

---

### Post by balthus666 on 2013-03-27
> Welcome to the Ubuntu Forums [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]
Thanks for your quick answer and warm welcome! :)
> but I would check it with new kinds of partition tables
Yes, I'm also trying to find info regarding the new partition tables. 
I'm a bit lost with those new GPT, secure boot, UEFI stuffs. It was much easier before and it seems this complexity is just driven by big companies (m$oft) to prevent easy installation of alternative os. (another good reason to *dd* if=/dev/zero of=/dev/windows8)

> Another method, that will definitely work, is to make a clone or image with ***dd***
Yes, I will also try to make a copy with DD to an iso file but I'm not sure if it is sufficient. For example If I clone the samsung recovery partition and later restore it, how should it be restored? Same place on the drive? How does the F4 recovery option at boot will find back the partition (by its name or position?)
Also not sure it the recovery partition is enough to restore the raid on the disk and other partitioning... :(
Anyone else a suggestion?

Regards,

---

### Post by sudodus on 2013-03-27
> **balthus666 said:**
> Thanks for your quick answer and warm welcome! :)

Yes, I'm also trying to find info regarding the new partition tables. 
I'm a bit lost with those new GPT, secure boot, UEFI stuffs. It was much easier before and it seems this complexity is just driven by big companies (m$oft) to prevent easy installation of alternative os. (another good reason to *dd* if=/dev/zero of=/dev/windows8)

;-)
> 
Yes, I will also try to make a copy with DD to an iso file but I'm not sure if it is sufficient. For example If I clone the samsung recovery partition and later restore it, how should it be restored? Same place on the drive? How does the F4 recovery option at boot will find back the partition (by its name or position?)
Also not sure it the recovery partition is enough to restore the raid on the disk and other partitioning... :(
Anyone else a suggestion?

Regards,

You know dd already, so use it for the whole drive (or each drive). I have done it several times, and restored successfully.

```
sudo dd if=/dev/sda of=/dev/sdx bs=4096
``` will clone the drive sda to another drive of at least the same size.

```
sudo dd if=/dev/sda bs=4096 | gzip > dd-sda.gz 
``` will make a compressed image of the drive sda. During the these dd operations, partitions of the drives should *not* be mounted.

---

### Post by oldfred on 2013-03-27
These tools say they backup Windows 8.
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

I would also make a Windows 8 repair flash drive.
      
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Windows has specific partition requirements. I might document your exact configuration with BootInfo report from Boot-Repair and save that to another backup drive.
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[URL="http://technet.microsoft.com/en-us/library/hh824947.aspx"]http://technet.microsoft.com/en-us/library/hh824947.aspx

      [/URL]
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
    [URL="http://technet.microsoft.com/en-us/library/hh824947.aspx"]
[/URL]

---

### Post by balthus666 on 2013-03-27
Wow, thanks for the link. Lot of intersting links, but I don't think I will pay for some windows product to backup ;)
I prefer to follow the penguin free way :)
Here is the content of the disk: 
[http://paste.ubuntu.com/5653179](http://paste.ubuntu.com/5653179)

I didn't know that tool but really nice to share info to ppl.
So far I have cloned with clonezilla the full disk and also a second backup with each partitions.
I've also backup the gpt table with boot-repair to an external usb :) I
So I think I can try to make some space and install ubuntu :)
Thanks for the help!

Regards

---

### Post by balthus666 on 2013-03-28
Hello, 
Some news regarding the installation.
I've scrapped the windows 8 partition, kept the 2 recovery partition, deleted the 2 partitions of the ssd, install ubuntu as described on this page:
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

Installation was very easy and smooth. So far, everything works fine (except the gnome-classic mode which doesn't show the window decoration, except if I use the safe mode).
Happy with my new notebook.
Pro: Ubuntu seems happy, nice design, Function keys (F1...F12) instead of stupid alternative controls, touch screen (but i don't find it so useful), keyboard feeling is great.
CON: The resolution is still 1368x768 could have been a bit higher, 
glossy screen.
Dunno what to do with the recovery partition (around 40GB lost) Can it be dropped and recovered later? (even not sure I would use win 8)

---

### Post by sudodus on 2013-03-29
> **balthus666 said:**
> Hello, 
Some news regarding the installation.
I've scrapped the windows 8 partition, kept the 2 recovery partition, deleted the 2 partitions of the ssd, install ubuntu as described on this page:
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

Installation was very easy and smooth. So far, everything works fine (except the gnome-classic mode which doesn't show the window decoration, except if I use the safe mode).
Happy with my new notebook. :-)> 
Pro: Ubuntu seems happy, nice design, Function keys (F1...F12) instead of stupid alternative controls, touch screen (but i don't find it so useful), keyboard feeling is great.
CON: The resolution is still 1368x768 could have been a bit higher, 
glossy screen.

Please post the specs of the graphics card/chip and the native resolution of the screen!
> 
Dunno what to do with the recovery partition (around 40GB lost) Can it be dropped and recovered later? (even not sure I would use win 8)
Did you make a full backup of the drive before installing Ubuntu? In that case you need not keep the recovery partition on the internal drive. Otherwise, back it up before re-using the space!

You can make a data partition, where you keep photos etc, or you can make a test partition, where you install other distros of linux (in particular: versions and flavours of Ubuntu). Actually, 12GB is plenty of space to test-install linux.

---

