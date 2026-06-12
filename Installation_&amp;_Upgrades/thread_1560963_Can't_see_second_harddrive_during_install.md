---
title: "Can't see second harddrive during install"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by sugam on 2010-08-25
I have Windows 7 installed to the first harddrive. I have an empty 2nd drive that Ubuntu will not see.

I'm trying to get Ubuntu to install side by side with Windows 7, but it only see's the disk that Win7 is installed on. I tried setting "nodmraid" with no success. 

Also, I'm getting random lockups during the install. Checking for time clock, pressing forward button, etc. I was hoping there was a "safe graphics mode" option (F4), but it looks like it was removed.

I would greatly appreciate any help. I've been stumbling around on this for 2 days now.

---

### Post by techxcell on 2010-08-25
Here are a few things you can do:

1. Check if the jumper settings are correct. One should be master and the other slave. 
2. Check that the disk is not disabled in the BIOS.
3. If you can see the second disk in Windows 7, delete all partitions, create a new partition, set it active.
4. If all else fails. Unplug the disk on which you have Windows 7. Leaving just the 2nd disk in, boot from the ubuntu CDROM.

Let me know how it goes.

---

### Post by dabl on 2010-08-25
In addition to what techxcell wrote, which is all good, you need to look at the "mode" of the SATA channel in BIOS (I assume the hard drives are SATA drives).  If it is set to AHCI, change it to "Legacy IDE" or "PATA" or whatever the other option is.

If that works to make it visible in Ubiquity (the Ubuntu installer), then after you install your system, and have it booting correctly, you can probably change the SATA back to AHCI and it will still boot correctly.

---

### Post by sugam on 2010-08-25
> **techxcell said:**
> Here are a few things you can do:

1. Check if the jumper settings are correct. One should be master and the other slave. 
2. Check that the disk is not disabled in the BIOS.
3. If you can see the second disk in Windows 7, delete all partitions, create a new partition, set it active.
4. If all else fails. Unplug the disk on which you have Windows 7. Leaving just the 2nd disk in, boot from the ubuntu CDROM.

Let me know how it goes.

1. Both drives are SATA. No need for master/slave jumpers.
2. The disk is not disabled.
3. I can see the drive in Win7. I've deleted the volume and created a NTFS partition. Ubuntu failed to see the drive each time.
4. If I unplug the drive I won't get the dual boot options (i'm not good enough to mess around with grub manually). If this ends up being my only option I'll do it, but it's still annoying that Windows setup can see both HD's without problem.

---

### Post by sugam on 2010-08-25
> **dabl said:**
> In addition to what techxcell wrote, which is all good, you need to look at the "mode" of the SATA channel in BIOS (I assume the hard drives are SATA drives).  If it is set to AHCI, change it to "Legacy IDE" or "PATA" or whatever the other option is.

If that works to make it visible in Ubiquity (the Ubuntu installer), then after you install your system, and have it booting correctly, you can probably change the SATA back to AHCI and it will still boot correctly.

The SATA mode I was in was IDE. I changed it to AHCI and tried it with/without "nodmraid", but neither worked.

---

### Post by techxcell on 2010-08-25
You should try the 4th option. The question of dual boot arises after we can confirm the second disk drive is fault free and capable of booting an OS at all!

Ah! yes... Another thing you can do is check if a BIOS upgrade is available for your system from the manufacturer. Linux uses the BIOS to enumerate disk drives. Most of the time this problem is caused by the BIOS not supporting a particular manufacturer's HDD. I had a similar problem with Samsung Drives once.

---

### Post by dabl on 2010-08-25
Also, you can probably see it and install on it using the Alternate Install CD, instead of the Live CD.  Live CD uses Ubiquity, but Alternate CD uses a conventional (but very functional) character-mode installer, which doesn't have the blind spot for SATA drives.

---

### Post by techxcell on 2010-08-25
> **dabl said:**
> Also, you can probably see it and install on it using the Alternate Install CD, instead of the Live CD.  Live CD uses Ubiquity, but Alternate CD uses a conventional (but very functional) character-mode installer, which doesn't have the blind spot for SATA drives.

Good call dabl! I agree. Do this first.

---

### Post by sugam on 2010-08-25
Good suggestions. Thanks guys! I will be trying the alternate install. Just have to download it first.

---

### Post by sugam on 2010-08-26
> **techxcell said:**
> You should try the 4th option. The question of dual boot arises after we can confirm the second disk drive is fault free and capable of booting an OS at all!

Ah! yes... Another thing you can do is check if a BIOS upgrade is available for your system from the manufacturer. Linux uses the BIOS to enumerate disk drives. Most of the time this problem is caused by the BIOS not supporting a particular manufacturer's HDD. I had a similar problem with Samsung Drives once.

Tried the alternate install and no luck. Connected just the drive in question and it still wouldn't work. Going to grab the support tools and see if resetting it to factory defaults will work.

Thanks for the help guys I really appreciate it. :p

---

