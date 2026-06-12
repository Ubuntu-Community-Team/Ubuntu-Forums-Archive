---
title: "Question: Reformatting &amp; Installation"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by mutantapple on 2006-11-19
Hi there, I have a problem with my hard drive not being detected. Does anybody have any ideas on how to reformat the drive though a commandline or something? I'm not exactly sure what the problem is since I had this OS installed already but then I had to mess around with the partition names and accidently deleted 2 of 2 partions on the drive.

When I tried to run the CD installation "Install" thing under "Gnome Partion Editor" it isn't able to write onto the drive. What's worse is now the system doesn't even detect a Hard drive! I've ran gparted and it still detects no drive.

Does anyone have any idea on how I would tackle this dilemma? Or is there a way to manually reformat the hard drive completely though the BIOS, and what would be the command line function to do so.


Thanks.:-k

---

### Post by K.Mandla on 2006-11-19
If you want to see if your drive is undetected or just hiding, try *sudo fdisk -l*. That should list all the connected drives that the system recognizes.

Usually reformatting is done through the *mkfs* command, but each file system has its own unique command. *mkdosfs* will format the drive as FAT, *mke2fs *creates ext2 and *mke2fs -j* creates ext3, and so forth.

If you want to blank the drive completely and start over from scratch, try [Killdisk]("http://www.killdisk.com").

Hope some of this helps. ;)

---

### Post by mutantapple on 2006-11-21
Awsome, thanks for the lead. I managed to located a new hard disk so I just replaced the old one and reinstalled the OS.

"Problem Neutralized!" :KS

---

