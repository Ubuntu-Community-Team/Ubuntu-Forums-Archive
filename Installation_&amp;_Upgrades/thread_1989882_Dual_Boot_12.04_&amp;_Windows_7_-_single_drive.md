---
title: "Dual Boot 12.04 &amp; Windows 7 - single drive"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by albertkao on 2012-05-28
My computer has Windows 7 preinstalled.
I want to install kubuntu desktop 12.04 to make a dual boot computer.
Is the instructions on the webpage best practice about "Read Using Grub Legacy for the boot partition to see why I recommend using Ubuntu Server edition 9.04 for this step.":
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Partition_design](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Partition_design)

I find it odd to use 9.04 to install Grub Legacy when 12.04 is available.
Is there a better way to make my computer dual boot?

---

### Post by wilee-nilee on 2012-05-28
9.04 is end of life it is a old wiki, and grub 2 is the bootloader now.

---

### Post by oldfred on 2012-05-28
Make good backups and a repairCd.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Most preconfigured Windows 7 machines use all 4 primary partitions:
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

While a server install is different, the desktop installers have not changed a lot.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://*********************.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://*********************.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

The main change is Unity, but you can install gnome panels which is close to the old version. Some like Unity, some hate it.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://*********************.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://*********************.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by albertkao on 2012-05-29
Thank you for your reply.
My computer has 6GB RAM, 200GB free space in the hd.  I plan to allocate 100GB for 12.04 and the rest of hd for future OS.
Is this allocation ok?
```
/dev/sda5 /          20GB   ext4
/dev/sda6 linux-swap 12GB   ---
/dev/sda7 /home      68GB   ext4
unallocated         100GB
```

unallocated 5.69MB

---

### Post by oldfred on 2012-05-29
Should be good.

You do not need swap that size. With 6GB of RAM you will probably never use swap unless you edit videos or have every program you have open at the same time. You only need 6GiB if you want to hibernate & with dual boot hibernation is not really recommended.

I might shrink Windows a bit more and create a shared NTFS partition for any data you might want in either system. I still have my Firefox & Thunderbird profiles & all photos for Picasa in my NTFS partition even though I now boot XP rarely.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by albertkao on 2012-05-30
> **oldfred said:**
> Should be good.

You do not need swap that size. With 6GB of RAM you will probably never use swap unless you edit videos or have every program you have open at the same time. You only need 6GiB if you want to hibernate & with dual boot hibernation is not really recommended.

I might shrink Windows a bit more and create a shared NTFS partition for any data you might want in either system. I still have my Firefox & Thunderbird profiles & all photos for Picasa in my NTFS partition even though I now boot XP rarely.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
Is this configuration ok?
```
/dev/sda5 /          20GB   ext4
/dev/sda6 /home      68GB   ext4
/dev/sda7 ???        50GB   shared NTFS
unallocated         100GB
```

---

### Post by oldfred on 2012-05-30
I do not create shared as part of install. I normally partition in advance so all partitions exist as I install.

I call my shared NTFS as /mnt/shared. I use /mnt so it does not show in the left panel of nautilus and link folders into /home. If you prefer to see it in /home you can mount in /media/shared or just directly into /home.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by albertkao on 2012-05-31
> **oldfred said:**
> I do not create shared as part of install. I normally partition in advance so all partitions exist as I install.

I call my shared NTFS as /mnt/shared. I use /mnt so it does not show in the left panel of nautilus and link folders into /home. If you prefer to see it in /home you can mount in /media/shared or just directly into /home.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:
As per your instruction to put my shared NTFS as /mnt/shared, the size of / should be increased:
```
/dev/sda5 /          70GB   ext4
/dev/sda6 /home      68GB   ext4
unallocated         100GB
```

---

### Post by oldfred on 2012-05-31
I am not sure I understand. The / can be 20 or 25GB and the shared NTFS 50GB Root has to be a Linux format like ext4, shared with Windows has to be formated NTFS. You use links to make it look like the NTFS folders are in /home is all.=, but they really are in the NTFS partition.

---

### Post by albertkao on 2012-06-01
> **oldfred said:**
> I am not sure I understand. The / can be 20 or 25GB and the shared NTFS 50GB Root has to be a Linux format like ext4, shared with Windows has to be formated NTFS. You use links to make it look like the NTFS folders are in /home is all.=, but they really are in the NTFS partition.

You are right.
The shared NTFS is in the Windows partition, so my linux disk partition is:
```
/dev/sda5 /          20GB   ext4
/dev/sda6 /home      68GB   ext4
unallocated         100GB
```

If I want to boot Windows by default, then what should I do?
Should GRUB2 installs a boot image to the master boot record (MBR) or the /dev/sda5 partition's boot sector?

---

### Post by oldfred on 2012-06-01
Grub2 has os-prober that runs on every update. It finds other operating systems and adds a boot stanza automatically. Old grub legacy sometimes found XP and nothing else, so we had to create manual boot stanzas for many systems.

When you install it should find Windows and add it to the menu. If not found run this to update from Ubuntu terminal once fully booted (not liveCD).
```

sudo update-grub
```

You install grub2's boot loader to the MBR of the drive not the partition. Or sda, not sda5 and never to any NTFS partitions as they have to have NTFS signatures in the PBR - partition boot sector/record.

---

### Post by albertkao on 2012-06-03
I installed 12.04 successfully.

---

### Post by oldfred on 2012-06-03
Glad that worked.

If you have other issues not related to installing, then post a new thread.

---

