---
title: "Partioning Help Needed Fast"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by mfmbcpman on 2006-11-12
I am installing Ubuntu 6.1 on my dell e1705 laptop right now. I am now stuck on something. 

My computer comes with two hidden partitions I need, Media Direct and diagnostics.

I have XP installed on a 20 gb partition. I have an 80 gb hard drive. I am editing the partition table manually. I created a fourth partition from the unallocated space but now the installer says there needs to be two partitions for Ubuntu, a 256 mb minimum swap space, and a 2 gb min for root, and I am at the limit of four partitions so I don't know what to do. Am I doing somehing or is there someway around this?

---

### Post by yabbadabbadont on 2006-11-12
Remove the primary linux partition you created and create an extended partition that takes up the rest of the space.  Now create logical partitions in the extended partition for your swap and whatnot.  Linux has no problem booting from logical partitions.

---

### Post by mfmbcpman on 2006-11-12
It only lets me make one logical partition on the extended partition though.

I'll describe in more detail what I'm doing. I have 3 partitions already. I click on the unallocated space and select new partition. I select extended partition and add. Then I select that, then New. Create as: Logical Partition. What should the filesystem be created as?

---

### Post by mfmbcpman on 2006-11-12
By the way, is there any reason for the 4 partition limit?

---

### Post by mfmbcpman on 2006-11-12
> **mfmbcpman said:**
> It only lets me make one logical partition on the extended partition though.

I'll describe in more detail what I'm doing. I have 3 partitions already. I click on the unallocated space and select new partition. I select extended partition and add. Then I select that, then New. Create as: Logical Partition. What should the filesystem be created as?

Never mind, I figured out how to create more than one.

---

### Post by louieb on 2006-11-12
The four primary partition limit goes back to the days when IBM and Bill Gates got together. IBM made a pc called the XT. Bill made an opperating system for it and called it DOS. Later on extended and logical partitions were created to get around this limit.   
This is the same Bill Gates that said a personal comuter should never need more that 640k of memory.

---

