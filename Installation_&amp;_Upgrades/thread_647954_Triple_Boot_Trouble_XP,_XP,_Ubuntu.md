---
title: "Triple Boot Trouble: XP, XP, Ubuntu"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by BattlePanic on 2007-12-22
My current triple boot setup is as follows:  XP, XP, Ubuntu

Unfortunately I can't boot into the second XP partition.  I get the dreaded "missing hal.dll" error.

Prior to installing Ubuntu I had two installations of Windows XP on two separate partitions:

```

----------------------------------------------------------------------------
|                     XP1                       |            XP2           |
----------------------------------------------------------------------------

```

Upon startup, the Windows boot loader (ntldr) was able to boot into either installation with no trouble.

Before installing Ubuntu I made some unpartitioned space available on my drive using Norton Partition Magic in Windows.  My memory is a little hazy, but I think I decreased the size of each XP partition and then moved the second partition to immediately follow the first, such that the newly unpartitioned space was at the end of the drive, like so:

```

----------------------------------------------------------------------------
|                 XP1                  |        XP2        |||||||||||||||||
----------------------------------------------------------------------------

```

I then installed Ubuntu, which installed GRUB as my boot loader.  GRUB was automatically configured with an option to pass control to the original ntldr.  So, in order boot into Windows, I select this option from GRUB and then select which XP installation in ntldr.  The first Windows XP partition boots with no trouble but the second partition is unreachable and I'm given the missing hal.dll error.

My Windows boot.ini is as follows:

```

[boot loader]
timeout=7
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Plump Pop"  /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Contra" /noexecute=optin /fastdetect

```

As far as I an tell, everything in my boot.ini seems to be correct so I'm not sure where the problem lies.  I thought that perhaps the resizing/moving of the Windows XP partitions might have caused ntldr to lose track of where the second partition was, but I also would hope that Partition Magic would have handled such important matters for me, that is what it is designed to do, after all.

Running Partition Magic after installing Ubuntu, this is a rough representation of the information I'm given:

```

|----------Primary Partition-----------|----Extended Partition----|
----------------------------------------------------------------------------
|                 XP1                  |        XP2        | SWAP | Ubuntu |
----------------------------------------------------------------------------

```

I've noticed that the second XP install and Ubuntu's swap partition are now both in the "extended partition" although I don't know if this is significant.  I just gave the Ubuntu installer the unpartitioned space and it divided it up as you see above.  

I'm stumped.  Surely there must be a solution to this problem but I can't figure this one out.  Any thoughts would be greatly appreciated.

---

### Post by Craigus on 2007-12-23
Well, the extended partition is the second partition, and the XP partition within the extended partition is actually the third partition, so maybe :

> boot loader]
timeout=7
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Plump Pop"  /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Contra" /noexecute=optin /fastdetect

However, I'm not sure if XP needs to be on a primary partition, it may. If so, you may have to convert the second XP partition to be a primary one.

---

### Post by BattlePanic on 2007-12-23
I tried this out and it worked!  I modified the last line of my boot.ini to:

```
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Contra" /noexecute=optin /fastdetect
```

Setting the second partition from '2' to '3' as you suggest seems to do the trick.  I could have sworn that the second XP partition was originally enclosed in an "extended partition" before resizing/moving partitions so I never thought changing the partition number since it's position relative to the primary partition had never changed.  Honestly, I'm still a little confused by this but I'm happy to report that things are now working.  Thanks for the tip!

---

### Post by logos34 on 2007-12-23
Just for the record, a second windows installation will boot from a logical partition as long as the  'master' windows partition is on a primary flagged 'active' (it contains the bootloader files).  

I'm confused too...if windows is indeed on a logical inside an extended, then it should show up as sda5 (or hda5) when you run

sudo fdisk -l

although I haven't done what you have resizing with PM and all that jazz, I have had xp home on first logical and it's showed up in fdisk as hda5 (logical paritions start at '5' no matter what), and I thought it showed the same in boot.ini, '(5)' rather than '(3)'...could be mistaken.  (maybe windows just numbers the partitiions in the order they appear on the disk).  All the more odd that you would have to change the number since you only resized it and thus the order did not change.

---

