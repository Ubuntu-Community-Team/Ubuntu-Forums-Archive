---
title: "Fresh edgy install over Dapper in a dual boot"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by nnovillo on 2006-10-23
Hi there!

I had a dual boot notebook with both windows and Dapper Drake, which were doing great.
I upgrated to efty edge, and it was still better. 
I mess efty afterwards, and as I can't fix it I want to install it fresh, but WITHOUT breaking my windows partition.
I am in step 5 of the CD installation, and I want to make sure that the partitions that edgy choose by default is correct to install a fresh edgy without breaking windows nor the dual boot.

This is the info I have:

/media/hda1  23 gb  Partition 1 Disk IDE/ATA 1 (Primary) [HDA1]
swap         957 mb  Partition 5 Disk IDE/ATA 1 (Logical) [HDA5]
/            13 gb   Partition 2 Disk IDE/ATA 1 (Primary) [HDA2]

If I format only the last 2 ones, Is the computer going to work without touching the windows and let me dual boot?

Thanks!!!

Nike

---

### Post by Sef on 2006-10-23
All you have to do is set Ubuntu root to be reformatted and it will take care of the swap.  Leave the Windows partition alone.  

**Back up** your data before doing this.  It should work without a problem, but it is not 100% guaranteed.

---

### Post by nnovillo on 2006-10-24
Hi there,

Thank you very much for your help.

Just for the record, I installed Edgy Eft stepping on Dapper, I left the default installation partition, and it didn't break neither windows nor the dual boot.

Cheers,

Nike

---

