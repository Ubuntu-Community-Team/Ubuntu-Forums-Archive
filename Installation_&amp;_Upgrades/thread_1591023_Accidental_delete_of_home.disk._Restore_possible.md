---
title: "Accidental delete of home.disk. Restore possible??"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by cportiz on 2010-10-08
Hi everyone,
I think I did something dumb. I was trying to increase the space allocation to my /home virtual disk on my wubi installation of Ubuntu.  I ran the wubi-add-virtual-disk utility (as I had done before the first time I increased my space), but I received the message "The target virtual disk /host/ubuntu/disks/$virtual_disk already exists, aborting."  So, thinking that all my data was in a different path and that the file home.disk was probably just some configuration file of little importance (I should've checked and I should've made a backup of it myself), I browsed to /host/ubuntu/disks and **ran "rm home.disk",** then reran the wubi-add-virtual-disk utility (stored in my still existing /home/cportiz/Downloads directory), and I thought I had successfully increased my space.  

To my horror, upon restarting my computer, my desktop was empty and basically unusable as there is nothing to click on.  I rebooted on recovery mode and logged on in terminal mode, then browsed to /home and found an EMPTY folder.  I ran locate home.disk and found a file at /host/ubuntu/disks with the size that I specified when I ran the virtual disk utility, but I don't know where my old contents are.  PLEASE tell me I didn't just delete all that stuff.  PLEASE tell me that it is still somewhere on my hard drive and that all I need to do is modify the home.disk file in this or that way or hit restore.  There is not a home.backup file at /host/ubuntu/disks/.

Anyhow, if indeed I've lost everything, I can probably restore most of the work I'd done (only a couple of weeks worth) pretty quickly.  Some of the files were backed up in other computers, etc... but would you help me restore my wubi installation to a functional one?  I would prefer not to have to reinstall ubuntu altogether since I believe the majority of the packages I've installed were housed on /opt meaning I can get back up and running compiling certain programs from source fairly quickly and most of the recovery effort is in rewriting some of the files that were stored in /home.

Has anyone made this mistake before or understand its consequences?? 

Thanks for your help,
Carlos
p.s. I am writing to you from the Windows partition of the machine in question

---

### Post by bcbc on 2010-10-08
The big problem is that you can't recover files individually, you need to loop mount the virtual disk first and if any part of it is corrupted I think it will not work.

If you created a new file home.disk over the space created when you deleted the old one - you are probably completely out of luck. 

You could try data recovery software I suppose, but it seems a long shot (in which case you should stop using your hard drive - boot from live CD - or you might lose more data). 

PS If you forgot to delete the backed up /home (/home.backup I think) when you first created the home.disk there might be some data there - but anything created subsequently will be gone. And odds are you deleted the backup anyway.

---

### Post by cportiz on 2010-10-09
There is not a home.backup at either /home.backup or at /host/ubuntu/disks/home.backup.  I tried checking for other paths by running locate home.backup but it returned nothing.

I don't think that the new home.disk was created over the HD space of the old home.disk, because after I deleted home.disk, I could still browse to all the files in /home. It was only after I rebooted that the folder contents appeared empty.

What are some of the commands used for loop mounting virtual drives? What recovery software is recommended for this type of thing?

Thanks!
Carlos

---

### Post by bcbc on 2010-10-09
I can't really recommend any particular data recovery software - I've only ever used testdisk and photorec. Testdisk is supposed to be able to undelete files. [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

To loop mount a drive see [this]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?")

---

### Post by cportiz on 2010-10-10
I didn't have much luck with testdisk (it found many files that have been recently deleted while in the windows environment, but none from the virtual disk). 

I've been able to find some of the files that were in my /home drive using photorec (from the same people that make testdisk), but there are so many files that it's going to take a bit of work to get the right ones out.  It dumps all recovered files into folders, losing all folder structure, so I'm going to hunt for the few files that would take the greatest effort to reproduce, then delete the rest.  

I think we're finished in terms of what can be done.  

Thanks bcbc!!
Carlos

---

