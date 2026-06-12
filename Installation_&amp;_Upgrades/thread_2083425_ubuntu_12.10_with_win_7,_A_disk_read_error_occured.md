---
title: "ubuntu 12.10 with win 7, A disk read error occured?!"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by Nicanorex on 2012-11-12
I'm guessing that you have done this one before, but i just can't find it...

I have a notebook HP Pavilion dv7, which had 4 primary partitions, as you can see here, before messing up everything: 

[IMG]http://i46.tinypic.com/2r78yld.png[/IMG]

What we can see here is:  my four primary partitions (SYSTEM, C, HP_TOOLS and RECOVERY) and a big blank space, all NFTS except for HP_TOOLS which was FAT32.

What I did: As we can't install linux with already 4 primary partitions, i eliminated HP_TOOLS, (after coping its files to a folder in C), i did a new extended partition with new logical partitions for ubuntu and re did FAT32, HP_TOOLS and re copied its contain. Then i installed ubuntu.

Obviously i messed up something, here is what i have now, seen from Gparted:

[IMG]http://i49.tinypic.com/2laqws0.png[/IMG]

And the problem is? I can't start Windows 7 now, nor Windows7 (loader) nor Windows Recovery, as seen on grub start up menu. I keep getting  **A disk read error occured**.

Also, my fdisk -l resul, sorry for the spanisht:

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1              63        2047         992+  42  SFS
La partición 1 no se inició en el limite físico del sector
/dev/sda2   *        2048      409599      203776   42  SFS
/dev/sda3          409600   976972099   488281250   42  SFS
/dev/sda4       976975870  1953523711   488273921    5  Extendida
La partición 4 no se inició en el limite físico del sector
/dev/sda5       976975872   985372671     4198400    b  W95 FAT32
/dev/sda6       985374720  1006060266    10342773+  83  Linux
/dev/sda7      1006061568  1012205567     3072000   82  Linux swap / Solaris
/dev/sda8      1012207616  1953523711   470658048   83  Linux


I have to say that all my files in C are intact, so it would be cool, not having to re install windows 7.

Soooo, as you can see, i'm no genius in computer science, so if you guys could help me, i would really appreciate it. Thanks and take care!

Just for the record, linux it's cool, i would keep it alone, but i have to run Solidworks for work :mad:

---

### Post by oldfred on 2012-11-12
Somewhere you created partitions with Windows MMC. It came up with a box saying it was converting to dynamic partitions. Normal partitions are basic. Dynamic partitions are Windows proprietary, do not work with Linux nor even some Windows repair tools. Officially it is a one way conversion. Windows says to backup, scrub drive and reinstall to new basic partitions.

Some third party partition tools will convert back if you do not have too many partitions nor have really implemented the dynamic part were some data in a logical partition is really in different physical partitions. 

The free versions used to do the conversions. But now it looks like they all want you to buy the upgrade to enable dynamic conversion.  You might be able to find the older versions on some of the download sites. Or pay for upgrade.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)

If you can get back to your 3 primary partitions without any data the testdisk from a Linux liveCD may work. Best for all the conversions to have as few actual partitions as possible.  I have not seen anyone with both SFS and an extended. Ususally once you create SFS or dynamic partition Linux stops working. Or did you create partitions in Windows after installing Ubuntu? Always create partitions with gparted or other Linux tools.

---

