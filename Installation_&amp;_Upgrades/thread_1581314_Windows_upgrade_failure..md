---
title: "Windows upgrade failure."
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by tedygram311 on 2010-09-24
I just updated vista to 7 and since then my life has been terrible. I have been trying to get back into linux and redistribute a partition but can't for some reason.  I know that I need to move it but I am not sure exactly what is going on please help.
This is the output for fdisk in terminal:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x915d4d92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13       21603   173422592    7  HPFS/NTFS
/dev/sda3           21604       28985    59287553    5  Extended
/dev/sda5           21604       28677    56820736   83  Linux
/dev/sda6           28678       28985     2465792   82  Linux swap / Solaris

I have never seen the cylinder boundary thing before and attached is gparted.  I just want this cleaned up a little but am coming up with nothing.  Please help.  I am also running gparted and the os off of the disk right now, I am ready to fix this when someone responds.

---

### Post by CharlesA on 2010-09-24
Are you not able to boot from ubuntu on the hard drive?

Check [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") to see how to reinstall Grub.

---

### Post by Mark Phelps on 2010-09-25
> **tedygram311 said:**
> I just updated vista to 7 and since then my life has been terrible. 
Did you do an in-place upgrade from Vista to Win7? IF so, you should have checked at a Windows7 forum first (e.g., sevenforums.com is one of the best).  They would have told you NOT to do that.

> I have been trying to get back into linux and redistribute a partition but can't for some reason.  I know that I need to move it but I am not sure exactly what is going on please help.

I have never seen the cylinder boundary thing before and attached is gparted.  I just want this cleaned up a little but am coming up with nothing. 
If you run chkdsk on the first partition, that might fix it.  Boot into Win7, select that partition, and check it for errors.  

If that doesn't, do NOT use GParted on it.  That is your Win7 boot partition and if you mess with it using GParted, you run the risk of corrupting it and rendering Win7 Unbootable.

When in Win7, you were sure to use the Backup function to create and burn a Win7 Repair CD, right?  Probably not ... So, before you do ANYTHING else, do that.

Of course, I'm presuming that you want to (1) fix the first partition and (2) continue to use Win7.

---

### Post by tedygram311 on 2010-09-25
Well I ended up just reformatting the whole thing because I had to study for a test anyway.  What I was trying to do was combine that last partition instead of just having a standalone partition that they could both use.  I can have that with the windows partition.  As for the upgrade, I backed up everything I had removed vista and then booted 7 into the old partition.

---

