---
title: "how to backup before upgrade attempt?"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Frontierbacon on 2008-11-15
hello, obviously i've tried googling on this but results we're inconclusive.

i need to upgrade from 7.10 to 8.04.. since newer wine versions dosent come out for 7.10.. however last time i tried upgrading with the distro upgrade tool, ubuntu got completely screwed and had to reinstall, and lost everything (the pain).

im not risking this again, so im thinking i take a backup of my linux partition, which i can then restore with later from a live cd if all hell breaks loose.

im thinking i can basically just take a raw copy of / . and compress it into a rar or tar.gz file, but im not sure? im relatively new to linux. i know if i we're to go that way, i have to ignore mounted and linked folders offcause, plus there are several folders in root file directory that have ram mounted somehow i believe? must ignore thoose as well.

ultimately, is there a simply program that can do this for me? a program that when opens has 2 button.. MAKE BACKUP,, RESTORE BACKUP. the first making a .something file with an image of the entire os parittion, and secound button (which would be from live cd) you select a .something file and a partition, and it starts restoring.

if not can someone give me sure fire instructions on how to do it manually? in the simplest way.

thanks.

---

### Post by Mr_JMM on 2008-11-15
Have you got a separate /home partition? (If so, this will be a lot easier!)

A one button option may not be possible unless it's the one on an external drive!

[edit]
A quick search found this useful guide:
[http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")

---

### Post by lswb on 2008-11-15
Where are you going to store the backup? If you have an external drive or a large enough unused partition on your hd, you can just use gparted to copy the exisiting installation. I share your pain with the upgrades, I've only been able to do it sucessfully one time. 

I have one of those cheap external usb enclosures with a 80GB laptop drive installed. Before I do anything "dangerous" I use gparted to clone the endangered partition onto the external drive. (you could use a separate partition on the internal drive as well) Then you can try the upgrade. If it doesn't work, go for the clean install and use the backup to recover your data.

You _can_ compress the backup with tar/gz or whatever but in my experience, it really really takes a long long long time to compress several GB, and it does complicate the restore somewhat.

---

