---
title: "Can't boot into Ubuntu soon after upgrade to 17.4"
date: 2018-02-22
forum: Installation &amp; Upgrades
---

### Post by SiddharthaWolf on 2018-02-22
Hi,

I'm having trouble booting into an older ASUS dual-boot laptop that I (possibly unwisely) upgraded to 17.4 recently in the hope that it may resolve package conflicts that I suspected may have been making it perform slowly (in reality, it may have been wiser to act on the major memory hoggers, which seemed to be compiz, and find a way of dealing with that, but that's another issue...).

I've tried Boot Repair (via Live USB, which was fine, though quite slow) and it suggested there are errors with the way the boot partition is set up (see [http://paste.ubuntu.com/p/4Rf22mwMSG/](http://paste.ubuntu.com/p/4Rf22mwMSG/)). Specifically that a "locked-ESP" was detected and that I may want to create a new boot partition.

I have no problem doing this, but thought it might be wise to check in with someone more knowledgeable first in case there's something I'm missing or anything else I should consider (and also so that the report can be explained in plainer English to me).

A bit more info: Went into GParted as suggested to see partition table, the first partition is already fat32, 487 MB and containing the boot flag... Is the problem that it's dev/sda1 rather than /boot/efi?

Many thanks!

---

### Post by TheFu on 2018-02-22
Yes, it was unwise to install an unsupported release. 17.04 support ended last month.
Use 16.04 (LTS with 5 yrs of support) or 17.10 with support until July.

For help with issues like this, boot repair's information is needed. Please post the URL, but really, you should use a supported release and 16.04 is best for non-experts.

IMHO.

---

### Post by SiddharthaWolf on 2018-02-22
Hi TheFu, thanks for the quick reply. I think I included the BootRepair log with my original post, but please let me know if this isn't what you meant and/or further details would be helpful. 

Assuming I can get the boot issue sorted out, I'll be sure to return to 16.04.

Cheers

---

### Post by TheFu on 2018-02-22
Sorry, I looked at the link, but it was empty.  Turns out it just took a long time to load and display.

Is the boot-repair version current? Appears to be 14.04-based, which shouldn't be used for newer systems.  The lack of GPT partition support is an issue. 
I'm confused as to why correcting this is needed when you'll be moving back to 16.04?  Just boot off a flash drive running the 16.04.3 ISO, copy off any data you need to be saves and install 16.04 into the partition(s).

I can't help with the issue, since I've avoided EFI booting and stopped dual booting years ago.

---

