---
title: "ntfs partitions: resize/create during FF installation"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by gmcauley on 2007-04-23
I am trying to install Kubuntu (64bit) on my HP Pavilion dv2000 laptop (AMD Turion 64 X2) that already has Vista.

The Live CD / installation seems to work great until a get to the 'Prepare disk space' page.

The only option under 'Guided' is to 'use the entire disk' (based on what I have read about the installer, I expected more options (ie, resize)).  Anyway, I want to dual boot with Vista, but when I choose 'Manual': 1) there is no way to resize (shrink) the Window ntfs partition, and 2) if I try to create a new partition table, ''ntfs' is not listed in the 'Use as' drop down when creating a new partition.

How can I create a new ntfs partition?  Better yet (what I really want), how can I resize the existing ntfs partition?  Is this a Vista problem?

---

### Post by cessna_89702 on 2007-04-23
Do you have unallocated space on their because thats the only way it will do the guided thing i think?

When I installed I used the partitioner from system administration area not the one in the install.

So try that partitioner if you havent you it seems easier to me. i dont think you need to make a new ntfs

---

### Post by gmcauley on 2007-04-25
Thanks cessna_89702 for your reply.

> **cessna_89702 said:**
> Do you have unallocated space on their because thats the only way it will do the guided thing i think?

No, I don't have unallocated space.  I have been trying to shrink the ntfs partition from within Vista, but it only lets me shrink by ~6Gb.  This may be (at least in part) due to the pagefile.  However, I guess I could try to shrink it even by ~6Gb if this enables the 'guided' mode.


> **cessna_89702 said:**
> 
When I installed I used the partitioner from system administration area not the one in the install.

So try that partitioner if you havent you it seems easier to me. i dont think you need to make a new ntfs

I tried to use qtpart from the LiveCD to shrink the partition but it gave me an error message saying something like the ntfs partition is corrupted and that I should run 'dskchk /f' in Windows.  After I did this however, I got the same message from qtpart.

I am also thinking of reinstalling Vista, but I only have HP recovery disks and I am not sure  if they will let me do a custom install of Vista (eg, create partitions).  I have heard that some of the manufacturers disks only allow an exact 'factory installation'.  I hope this is not the case for HP.

---

### Post by az on 2007-04-25
If Vista will not srhink your disk, perhaps there is a hardware problem.  But yes, shrinking it by 6 Gig will create some free space and you will able to use guided partitioning on that.  That option should become the default if you free up the space.

---

### Post by cessna_89702 on 2007-04-25
When I did a dual boot I had to run ```
chkdsk /f
```  in Windows. I have XP and I couldnt resize my ntfs until I did that and rebooted and let it run the code. Then I partitioned and it worked fine

---

