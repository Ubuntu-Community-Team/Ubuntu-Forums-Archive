---
title: "Remove Ubuntu"
date: 2015-12-25
forum: Installation &amp; Upgrades
---

### Post by darrenjohnson on 2015-12-25
Hi,

I have ubuntu installed on my old laptop. I'd like to sell it, but i'd get a buyer more quickly if it had windows 7 back on it. How would I go about removing ubuntu or is it possible to boot from USB and install windows 7 cleanly?

Regards,
Darren

---

### Post by Bucky Ball on 2015-12-25
Boot from the Ubuntu install media. 'Try Ubuntu' and launch Gparted from the desktop. Delete all partitions and leave free space. You may need to delete grub but not au fait with how to do that (or Win may just flatten everything in that department).

Boot from the Win install media and you know the rest. ;)

---

### Post by Vladlenin5000 on 2015-12-25
You can do it either way.

The method outline by Bucky Ball will be easier to the Windows installer because it'll handle it as a "bare metal" installation (and it'll flatten everything in the boot department).
Doing as you asked (boot from USB and just install) is also possible and the end result should be exactly the same. The only difference is at one point of the installation process the Windows installer will tell you that there are no space to install. At that point you're supposed to select and delete one by one the previous partitions and when the installer reports the full drive as unallocated space everything will run as in the previous method. Doing so is much faster and easier, IMO, because using an Ubuntu media just to delete partitions is an unneeded step.

---

### Post by Bucky Ball on 2015-12-26
I was unaware Windows could delete EXT* partitions cleanly. Live and learn.

If it does, bung in the Win USB and fire away.

---

### Post by Vladlenin5000 on 2015-12-26
Yes, it does. It doesn't recognize them as such (EXT*) though but recognizes there are partitions and that is what matters. I can't remember exactly how they're shown but I guess is "unknown", "RAW" or something like that.
Likewise, in a dual boot system, if you go to the Windows disks manager utility all the partitions are there. It just doesn't recognized their file system therefore ignores them completely. Being able to recognize a partition and being able to read it are two different things, the former doesn't imply the latter and the latter doesn't prevent the former in any way.

---

### Post by Bucky Ball on 2015-12-26
They're shown, in my Win7 at least, as 'Healthy'. That's it. No filesystem or anything else.

---

### Post by Vladlenin5000 on 2015-12-26
You can even delete them there but if course you don't want to do that :biggrin:
The same in the installer. In the step below, going to the advanced options you'll be able to format, delete and/or create new partitions.
[ATTACH=CONFIG]266384[/ATTACH]

---

### Post by yoshii on 2015-12-26
If you want to prep the computer for Windows 7 or 8 or 10 and don't mind erasing everything, use gParted.  And delete all partitions, and create a new partition table of type GPT.  GPT will let the next person create more than just 4 partitions.  If you create a partition table using the default MSDOS MBR, then they can only create up to 4 partitions.  MBR is the older technique.  GPT is the newer technique.  Much older computers will need MBR, but much newer recent computers will need GPT unless the person chooses to use MBR.  MBR is called Legacy Mode in some computer hardware setup systems such as UEFI and even on some BIOSes.  

Personally, I like MBR better because then I can install GRUB4DOS and edit my own Linux Boot menu very easily from within Puppy Linux.  I can only have up to 4 partitions, including the SWAP (virtual RAM) area, but I don't mind.

---

### Post by Bucky Ball on 2015-12-27
@yoshi2: OP wants to put Windows back on it before selling, not prepare a blank disk for the next user, and gparted has already been suggested.

---

