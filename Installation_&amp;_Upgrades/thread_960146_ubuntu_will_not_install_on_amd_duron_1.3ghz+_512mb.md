---
title: "ubuntu will not install on amd duron 1.3ghz+ 512mb ram."
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by Tdsok on 2008-10-27
Hi
I have a pc with an AMD duron 1.3ghz processor and 512mb of ram.
When i use the ubuntu live cd (8.04) and select live cd mode, the splash screen comes up followed by cli text.
 it follows:

Busy box v 1.1.3 (Debian 1:1.1.3-5ubuntu12) built-in shell (ash)
Enter "help" for a list of built-in commands.

(initramfs)

this appears to be a command prompt of ash. I tried "help" but this just gave me the built in ash commands (eg. echo,exit,export,rmdir,mkdir)

how can I boot off the live cd without this happening?

P.S i tried to install ubuntu from the main menu and the same occours.

---

### Post by ajgreeny on 2008-10-27
It could be that the live CD is faulty, particularly if you downloaded and burned it yourself.  Se if you can check the [md5sum]("https://help.ubuntu.com/community/UbuntuHashes") of the downloaded .iso file (I have no idea how you do that in windows, so can't help if that is all you have available; do a google search).  Also when you have verified the md5sum, make sure you burn the image as slowly as possible with your hardware, I always do it a 4x speed.

---

### Post by Tdsok on 2008-10-27
the cd is not faulty as i have tried the xubuntu live cd and come up with the same problem.
help please!

---

### Post by Tdsok on 2008-10-27
I have done some research and found out that it is a problem many people are having. I have also found that it has something to do with floppy disks, Raid and SATA hard drives and damaged partitions. there are many proposed workarounds but non work for me.
I would really like some help with this. I am using an stright Ide 20gb so i have no idea why i am running into sata identification problems.
please!

---

### Post by wandalalakers on 2008-11-11
> **Tdsok said:**
> I have done some research and found out that it is a problem many people are having. I have also found that it has something to do with floppy disks, Raid and SATA hard drives and damaged partitions. there are many proposed workarounds but non work for me.
I would really like some help with this. I am using an stright Ide 20gb so i have no idea why i am running into sata identification problems.
please!

Have you tried the alternative cd?  I have found two AMD pcs that do not like the live cds.  On both of these pcs, I have to use the alternative cd for the install.

---

