---
title: "ubi-partman exit code 10"
date: 2014-12-01
forum: Installation &amp; Upgrades
---

### Post by kevcoder on 2014-12-01
A guy I commute on the bus with was interested in Linux so I passed him my USB key (created with unetbootin, Lubuntu 14.04 and with persistence).  

When he is trying to install on his Acer laptop (not sure of the exact model yet, but only that he bought it new in 2012) he gets the error in the Title.  He clicks continue and everything seems to work, but his machine just locks up at various points in the install process.  He sent me a screen shot so I know the issue is not simply him.

We are not personal friends, so I've only been providing phone support, but this guy is a windows power user and thus not afraid to wipe his drive, and is pretty motivated.

I'd hate to be the guy that convinced him that "Linux is hard".

googlefu tells me that this is know issue with the ubuntu installer on some acer laptops.

So...[INDENT]is there an easy fix that I can walk a noobie trough over the phone?
[/INDENT]
or[INDENT]is there another distro that does not have this issue that I can put on a usb stick?
[/INDENT]

---

### Post by oldfred on 2014-12-01
If he is a power user, he may have an ultrabook which adds a SSD an dual video. Which do complicate it. :)

And if from 2012, it may also be UEFI, but might not be, as that was about the time systems with UEFI started coming out. All Windows 8 pre-installed systems are UEFI. 
Or it could be UEFI hardware but with Windows 7 installed in BIOS mode.

How you install to BIOS and UEFI is very different.

Often the partman exit is BIOS where all 4 primary partitions are used, which all Windows 7 systems seem to do. Or issues that you are installing in the wrong UEFI or BIOS mode.

Need details on his system. And would be better to get him to post in forum as we need model, video chip and partition info:
Have him post this from terminal in live installer:
sudo parted -l

```
Partition Table: gpt

Number  Start   End    Size   File system  Name       Flags
 1      1049kB  404MB  403MB  fat32        new_efi32  boot


```

If it says gpt like above then it is UEFI.
If it says msdos then it is MBR partitioning. And likely will then show 4 primary partitions used.

---

### Post by kevcoder on 2014-12-01
Wow throw him into the CLI!!! I was hoping to avoid that...

> How you install to BIOS and UEFI is very different.

I don't own a pc built before 2009. Is there no distro/installer that will easily handle both for the novice user?

I ride the bus tomorrow so I'll see him then.

---

