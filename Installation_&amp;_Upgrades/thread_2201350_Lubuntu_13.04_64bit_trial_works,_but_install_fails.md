---
title: "Lubuntu 13.04 64bit trial works, but install fails with 'No bootable device found'"
date: 2014-01-24
forum: Installation &amp; Upgrades
---

### Post by elpidiovaldez5 on 2014-01-24
I am trying to do a clean install of Lubuntu 13.04 64bit. The Bios has no settings for EFI.

I boot from USB, connect wifi and run 'install'.  I have tried a default install and setting my own partitions as follows:

swap: 6 Gb
/ 20Gb ext4
/home 96Gb ext4

In all cases the system fails to boot from the 120Gb  Vertex ssd saying 'No bootable device found'.

Now I have spent hours browsing internet solutions and I am now overwhelmed by the amount of information available.  I have tried boot-repair/recommended fix - it made no difference. 

I feel the solution is to do with setting a /boot partition with either an efi or legacy boot record, however I see no way to do this from the installation tool.  The more I read on the internet the more complicated it seems to get, but I am not trying to dual boot or anything complicated.  I cannot believe that it can be so difficult. A little expert advice would be very welcome !

---

### Post by tfrue on 2014-01-24
Post the boot-info URL and I will try and help you.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

The boot-info part should be in there.

---

### Post by elpidiovaldez5 on 2014-01-24
Well I got things working in the end, although I have no idea why.  I did create a 200mb ext4 partition at the start of the disk mounted at /boot.  I don't know if this was the key or not.

Many thanks to tfrue fr the offer of help.  At least I felt I had some moral support.  I am glad I do not need to trouble you any further.

---

### Post by tfrue on 2014-01-25
No trouble, that's what we're here for! Glad to hear that it's working though.

Chris

---

### Post by tfrue on 2014-01-25
Also, don't forget to mark this thread as "Solved", Thanks

---

