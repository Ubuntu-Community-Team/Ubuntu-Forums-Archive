---
title: "Error creating partitions"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by lwinkenb on 2005-10-26
When I try to write the new partitions to the disk, ubuntu gives the following error:

error informing the kernel about modifications to partition
/dev/mapper/Ubuntu-swap_1p1 - Invalid Argument.  This means linux wont know about any changes you made to /dev/mapper/Ubuntu-swap_1p1 until after you reboot.  

If I try and continue, it will give an error trying to install the base system.  Does anyone know what the problem is here?

---

### Post by lwinkenb on 2005-10-26
Well I reburned a new CD, and attempted to reinstall.  Now the error message I get is:

"An error was returned while trying to install the initrd-tools package onto the target system.  Check /target/error/log/bootstrap.log for the details.

I did a search on the boards, and the only other thread I could find on this issue was [this one.]("http://www.ubuntuforums.org/showthread.php?t=75430&highlight=initrd-tools") I tried what was suggested in that thread, but it didnt help.

I did a MD5 check on the ISO before I burned it, so I know that it wasn't corrupted during the download.  I'm pretty much out of ideas here.

---

### Post by lwinkenb on 2005-12-02
I ended up figuring out the problem here.  My CD-ROM drive was busted, and it kept failing when it tried to read the same part of the disk.  A new drive fixed the problem.

---

