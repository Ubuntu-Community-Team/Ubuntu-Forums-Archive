---
title: "dpkg error, files list file,"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2007-06-29
I've been attempting to install a couple of upgrades using the graphic update package but get the following messages.  Not had this one before.  I searched these pages and only suggestion I found was to run fsck, which I did, says disk is clean.  Still getting error.  Any suggestions?  Is this already covered in a thread I missed?

Thanks a bunch

Jim

unable to open files list file for package `linux-image-2.6.20-16-generic': Input/output error

---

### Post by jamaas on 2007-06-29
Pieced some pieces together and manged to fix it ...If you get this here is how I fixed it ....

shut down feisty 
reboot with feisty 7.04 cd
open a terminal window
find which partition of your disk is your / (root) directory by running
fdisk -l
In my case it is /dev/sda1.  Yours will be /dev/something but might be hda1 or something else so check carefully
they run fsck by
sudo fsck.ext3 /dev/whateveryoursis   -f
note that both the .ext3 and -f parts are critical ... I didn't use them at first and it didn't work ...  :-(
this may point out lots of inode and other types of errors and ask you if you want to fix them, answer yes to all
when fsck finishes and you get a prompt back, shut down feisty running on CD, and reboot using the original kernel on your hard disk, and all "file list file" errors should be fixed when you attempt to install or remove packages using dpkg, apt-get, synaptic or whaterver.

Good luck!

---

