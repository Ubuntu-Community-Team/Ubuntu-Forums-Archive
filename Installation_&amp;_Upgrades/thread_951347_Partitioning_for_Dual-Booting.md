---
title: "Partitioning for Dual-Booting"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by techlover on 2008-10-18
Hi I'm new to Ubuntu and would like to create dual-booting for my laptop (windows xp is currently installed).

My laptop has a single hard disk drive that came partitioned in 2 drives (C: and D:, each 50GB).  Since C: is used for windows, I'm thinking of installing Ubuntu on my D:.  

1. During the installation process, if I were to delete the D: partition to set up swap and "/", would I lose all my data on both drives or just on D:?

2. Also, is there a way to differentiate which is my C: or D: in the partition window (since both of them are equal in size)?

3. I understand that all laptops have an additional recovery partition.  With my 4 partitions as C:, recovery, "/" and swap, does that mean I cannot set up any more partitions?

4. After Ubuntu has been set up, would I still be able to make use of D: (e.g. backing up files) when I'm using windows?

Thanks in advance.

---

### Post by Bucky Ball on 2008-10-18
1/ just d. C will be marked as NTFS. Just leave that alone.

2/ See 1.

3/ You should be able to burn a cd of the recovery partition to use as a recovery cd. You can then delete the recovery partition. All depending on how big you make your partitions, you can use your whole disk or not. Remember, if you create an extended partition, that will only count as *one* partition, regardless of the number of logical drives in it, but generally yes, 4 is the limit.

4/ If you have formated  the drives to a type Windoze understands. There is software to get around this, but ext3 (linux) is not recognised natively by Windoze. I have a 20 gig fat32 partition for sharing between the two OSs.

Hope that helps. :)

---

