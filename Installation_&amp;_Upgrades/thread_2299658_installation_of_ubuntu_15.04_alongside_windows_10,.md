---
title: "installation of ubuntu 15.04 alongside windows 10,please :("
date: 2015-10-20
forum: Installation &amp; Upgrades
---

### Post by sefi3 on 2015-10-20
ok...
so i'm working on this for a long long long time and i can't find the solution in the web. 
my laptop is dell inspiron 14z-5423, he came with pre installed windows 8, the updated to 8.1 and now 10.
yestarday i unallocated 36gb from the hd to install ubuntu.

here is my status:

1. from my windows, 35.8 gb unallocated
[IMG]http://s23.postimg.org/60n5pgasr/Untitled.png[/IMG]


2. then i  start  live ubuntu, and tried to install.
firstly i didnt had the screen of: "install alongside windows"
secondly , the partitions are empty:
 

[IMG]http://s23.postimg.org/mlus541wr/Screenshot_from_2015_10_20_09_40_16.png[/IMG]


3. soo, i start looking around the web and tried Couple of staff, and here is the errors/ status:

Gparted:


[IMG]http://s23.postimg.org/lts45wxpn/asda.png[/IMG]

[IMG]http://s23.postimg.org/5ciwk91gr/Screenshot_from_2015_10_20_09_41_46.png[/IMG]

[IMG]http://s23.postimg.org/4uj5qnmi3/image.png[/IMG]


and then i tried to see if fdisk :[IMG]http://s23.postimg.org/b5od72nqj/Screenshot_from_2015_10_20_09_41_31.png[/IMG]

[IMG]http://s23.postimg.org/r90u6vp9n/Screenshot_from_2015_10_20_09_41_42.png[/IMG]




please!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
help me.

---

### Post by grahammechanical on 2015-10-20
Please confirm that you have read this Ubuntu community guide. It also applies to machines with Windows 10 installed.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Note the general principles. Please confirm that you have followed this advice.

> 
[LIST]
[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 
[/LIST]



It is my understanding that from Windows 8 onwards Microsoft is able to reduce Windows loading times because Windows does not actually shut down but instead goes into hibernation. This leaves the file system (partitions) in a state that Linux will not be able to read.

Regards.

---

### Post by oldfred on 2015-10-20
Please post screen shots as attachments, not in line. Not everyone has high speed Internet.
You can attach easily with the Forums advanced editor and the paper clip icon.

You may need to use gdisk to fix the backup partition table issue.
       repair gpt:
[URL="http://www.rodsbooks.com/gdisk/repairing.html"]http://www.rodsbooks.com/gdisk/repairing.html
[/URL]
 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR.

 sudo gdisk /dev/sda
Command (? for help): 

 
[URL="http://www.rodsbooks.com/gdisk/repairing.html"]
[/URL]

---

