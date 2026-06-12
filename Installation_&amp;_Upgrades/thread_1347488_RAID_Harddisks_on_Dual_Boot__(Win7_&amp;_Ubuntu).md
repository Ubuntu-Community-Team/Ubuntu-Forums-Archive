---
title: "RAID Harddisks on Dual Boot  (Win7 &amp; Ubuntu)"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by rDwyP44y on 2009-12-06
[INDENT][COLOR="Green"][FONT="Arial Black"]I am in need of some help and some Info.[/FONT][/COLOR][/INDENT]

[INDENT][I]My Desktop Specs:[/INDENT]
[LIST]
[*]two 1TB SATA HDD's (2 x 1TB) and a 120 GB IDE/ATA HDD.
[*]ASUS M3A78-EM Motherboard [(specs here)]("http://asus.com/product.aspx?P_ID=KjpYqzmAd9vsTM2D")
[*]4 GB RAM
[/LIST][/I]

[INDENT][B]What I want to do is:[/INDENT]
*//120GB for operating Systems, 2TB shown as one HDD for Data//*
[LIST]
[*]Install Windows 7 & Ubuntu 9.10 on the 120 GB (50GB for Win7, 50GB for Ubuntu, rest GB's unpartitioned/unallocated space {which I can do with GParted)
[*]And have both of my 1TB HDD Merged as one (so that When I am under Windows 7 or Ubuntu 9.10, it is Seen as one single 2TB Hard-drive)
[/LIST]
[/B]
I Believe the RAID I am trying to get is [RAID 0]("http://en.wikipedia.org/wiki/RAID_0#RAID_0"), which is supported by my Motherboard [in the specs by the manufacture]("http://asus.com/product.aspx?P_ID=KjpYqzmAd9vsTM2D")
[B][CENTER][COLOR="Green"]
[FONT="Arial Black"][SIZE="4"]How Do I get this done?[/SIZE][/FONT][/COLOR][/CENTER][/B]
[I]
// I think my system is a 64 bit system, I have an AMD prcessor :lolflag://[/I]

[SIZE="1"]Additional Info:
[LIST]
[*]All of the HDD's I will re-format, since  backed up all important Data already... So will do a Clean/Fresh install!
[*]I have thought of RAID 1, but I decided I would go for RAID 0, and do manual/scheduled back ups of important data to my External 1TB HDD
[*]I do alot of video editing and photoshoping, thats why preferred to have my computer with 2TB total (in RAID 0) rather then 1TB total (in RAID 1)
[*]I will be adding another 4GB of RAM within a few weeks.
[/LIST][/SIZE]

---

### Post by phillw on 2009-12-06
Hi,

Using FakeRaid is not yet supported with Grub2 (at my last check) [http://ubuntuforums.org/showthread.php?t=1338445](http://ubuntuforums.org/showthread.php?t=1338445)

10.04 looks as if it will support it - have a read of that thread.

Regards,

Phill.

---

### Post by darkod on 2009-12-06
You are planning to install on the 120GB without raid but use raid0 data partition/drives.
The install should go fine but I have no idea if it will recognize the raid0 data later. You might try using Alternate Install CD, not the standard Desktop CD (LiveCD). The documentation says for LVM and/or RAID to use alternate install image/cd.

---

### Post by rDwyP44y on 2009-12-06
What alternate images/CD's are their? I only see two options for 9.10 Koala... one for 32Bit, and another for 64Bit ??

---

### Post by darkod on 2009-12-06
That's it, same as the desktop image. Either 32bit or 64bit, I guess you wanna go with 64bit. Be advised, the installer is text based, but you still end up with GUI system. Make sure you select gnome-desktop if needed during installation or you might end up with text based system. Not sure if the GUI is selected by default.

PS. Look here:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

You want alternate install cd.

---

### Post by jpichie on 2009-12-06
Unfortunately the alternate disc does not work. As the problem is not getting Ubuntu to install to the RAID (as this works on the live/alternate disc), but getting GRUB2 to install to the RAID. I am trying the Lucid Lynx daily build to see if maybe this will work.

---

### Post by darkod on 2009-12-06
> **jpichie said:**
> Unfortunately the alternate disc does not work. As the problem is not getting Ubuntu to install to the RAID (as this works on the live/alternate disc), but getting GRUB2 to install to the RAID. I am trying the Lucid Lynx daily build to see if maybe this will work.

In this case he wants the 120GB drive to be the location for both the installation and grub2. It should install fine because that's outside the raid. The issue might be "seeing" the raid0 volume after that. I guess the OP would like to access it from ubuntu too.

---

### Post by gilson585 on 2009-12-20
if you revert to grub1 after the install it will boot from fakeraid. instructions here [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

---

### Post by rDwyP44y on 2009-12-21
> **gilson585 said:**
> if you revert to grub1 after the install it will boot from fakeraid. instructions here [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

Thanks alot for the link, but Im not quite sure how *fakeraid *works but i will look into it, since I got holiday vacations now :P

[B][COLOR="SeaGreen"]Also one question....

At the moment I have two 1TB HDD, and I want to put them into RAID 1 (mirroring) .. but say in the future I add another 1TB HDD  ( to make my system a total of 3TB) Can i change from RAID 1 to say RAID 3/RAID 4/RAID 5? Without any problems?

Remember I will be using the SATA TereByte HDD's for data, and a single IDE/PATA  120GB for my Operating systems (Ubuntu & Windows)

[/COLOR]
Thanks alot in advance
[/B]

---

### Post by gilson585 on 2009-12-21
Fakeraid is very common. It basicly is not true hardware raid. Hardware raid is where the raid controller makes the 2 disks act as one and does all the computations on-board. Fakeraid uses a s/w driver to link the drives together and puts the computational load onto the cpu, slightly less efficient but perfectly good for home use. A hardware raid controller would set you back at least $250 and is not worth getting unless you have a disk intensive server running. As far as that goes I see you mentioned raid 0 in your first post, that is stripping and it increases disk performance. Then now you say your gonna use raid 1 which is mirroring, it provides the same performance as just one drive except now you have data redundancy in case one drive fails. As for adding one later, you should check your manual. I have yet to encounter an onboard raid controller that is capable of changing a live setup w/o resetting the raid array. Hopefully this helps you make some quick decisions on what you'd like to do w/o doing a bunch of research. If it helps at all here's a wiki on raid [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

