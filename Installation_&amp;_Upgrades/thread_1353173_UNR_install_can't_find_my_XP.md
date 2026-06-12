---
title: "UNR install can't find my XP"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by randall550 on 2009-12-12
I have an Acer Aspire with Windows XP installed. I am trying to set it up to dual boot with UNR. When I get to the partitioner, it says "This computer has no operating systems on it". Why won't it find my XP and what can I do about it?

---

### Post by darkod on 2009-12-12
First boot with the Try Ubuntu option, open terminal (in Applications-Accessories) and execute:
sudo apt-get remove dmraid

You are not using raid right? This happens sometimes if there are raid settings remains on the hdd.
After that reboot, select the Install Ubuntu and see if it can see the drive now.

---

### Post by randall550 on 2009-12-12
OK, I did that. Started the install again, and now the partitioner is trying to partition my **flash drive**. It gives me the option of erasing my entire hard drive, but won't let me partition it.
Thanks for the speedy reply BTW.

---

### Post by darkod on 2009-12-12
> **randall550 said:**
> OK, I did that. Started the install again, and now the partitioner is trying to partition my **flash drive**. It gives me the option of erasing my entire hard drive, but won't let me partition it.
Thanks for the speedy reply BTW.

Not even if you go into manual option?

---

### Post by mikewhatever on 2009-12-12
Then disconnect the flash drive before the installation. The installer does not rely on Windows XP, and therefore doesn't need to see it. The question is whether it sees partitions on the hdd.

---

### Post by randall550 on 2009-12-12
I just rebooted and started again, but now it's back to the original problem. Won't find the XP.

---

### Post by randall550 on 2009-12-12
The installer is on the flash drive.

---

### Post by darkod on 2009-12-12
While booted from the stick you can open Gparted in System-Administration. That will show you your hdd and partitions. Just to make sure everything looks as expected.

---

### Post by randall550 on 2009-12-12
It doesn't show as expected. It shows 149.05 GiB unallocated (it's a 160G disk) and no partition that is allocated.

---

### Post by darkod on 2009-12-12
> **randall550 said:**
> It doesn't show as expected. It shows 149.05 GiB unallocated (it's a 160G disk) and no partition that is allocated.

That basically means the disk is empty. You can boot into XP and use it right? Can you try it once more, I hate to even think something somewhere went wrong and your hdd is wiped.

---

### Post by randall550 on 2009-12-12
I did that a while ago and it was still there. I'll try it again.

---

### Post by randall550 on 2009-12-12
yep xp is still working

---

### Post by darkod on 2009-12-12
> **randall550 said:**
> I did that a while ago and it was still there. I'll try it again.

If XP is still there I have no more ideas. I haven't used linux a lot but I have never seen Gparted to be so wrong and see the drive as blank. It might be something messed up with the partition table that windows doesn't mind, but linux sees as blank drive.
There is some software called TestDisk that will check the disk and partition table for errors and repair them, but I haven't used it myself and I can't really advise you to start hacking your partition table. I don't want to be blamed for losing your data. :)

---

### Post by darkod on 2009-12-12
PS. The disk in windows is not dynamic right? I believe there was something like this if the disk is dynamic. You can see that in windows in Disk Management.

---

### Post by randall550 on 2009-12-12
Is there another name for Disk Management? I can't find anything by that name.

---

### Post by darkod on 2009-12-12
> **randall550 said:**
> Is there another name for Disk Management? I can't find anything by that name.

windows button + R, type diskmgmt.msc, hit Enter

---

### Post by randall550 on 2009-12-12
It doesn't show that the disk is dynamic. I'm not sure where to look for that information but it doesn't say "dynamic" anywhere in disk management. It does show 3 partitions and nearly 5 g of unallocated space.

---

### Post by darkod on 2009-12-12
In the middle of the screen, where the partitions are shown in a bar. At the beginning says like Disk 0, Basic (Dynamic). But I guess it's basic, that was just an idea.
I'm really puzzled... This is very strange.

---

### Post by randall550 on 2009-12-12
Could those other two partitions have anything to do with it? The partition
that apparently is the main one that says c: has 144 G with 127 free and says it's a system partition. That seems reasonable I guess. Then there are two that are EISA configuration, both empty, one is 4.88 G and the other one is 105 M.

---

### Post by darkod on 2009-12-12
> **randall550 said:**
> Could those other two partitions have anything to do with it? The partition
that apparently is the main one that says c: has 144 G with 127 free and says it's a system partition. That seems reasonable I guess. Then there are two that are EISA configuration, both empty, one is 4.88 G and the other one is 105 M.

5GB partition sounds like some kind of recovery partition, to get your computer OS restored back to factory settings. The 100MB might be some kind of utility partition, not sure. Strange they would show empty though. Windows should be able to read them and the % of usage.
I can't be sure if they have anything to do with this, but my approach is to delete those partition unless you need them. That's a decision only you can make. The main question is do you need them.

---

### Post by randall550 on 2009-12-12
Well, they're empty...not sure if that means anything or not.

---

