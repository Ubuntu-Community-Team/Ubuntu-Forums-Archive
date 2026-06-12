---
title: "Partitioning to Install Lucid for Triple-Boot"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by leehach on 2010-05-24
I have a computer dual-booting Hardy & Vista. I want to test drive Lucid, so I would like to install it to a new partition, but have it use my currently existing /home and /data partition. Need to know whether to use the "Guided" side-by-side partitioning option or the "Manual" option.

Since I would like to specify my existing partitions to mount as /home and /data, I tried to follow the manual partitioning option, but I'm concerned about what happens to my GRUB menu, since I've seen several posts about people not being able to boot their old OSes (particularly Windows) after installing GRUB2 as part of Lucid (if I understand correctly). So what's the best route here? 

Thanks,

---

### Post by darkod on 2010-05-24
> **leehach said:**
> I have a computer dual-booting Hardy & Vista. I want to test drive Lucid, so I would like to install it to a new partition, but have it use my currently existing /home and /data partition. Need to know whether to use the "Guided" side-by-side partitioning option or the "Manual" option.

Since I would like to specify my existing partitions to mount as /home and /data, I tried to follow the manual partitioning option, but I'm concerned about what happens to my GRUB menu, since I've seen several posts about people not being able to boot their old OSes (particularly Windows) after installing GRUB2 as part of Lucid (if I understand correctly). So what's the best route here? 

Thanks,

Yes, you need to use the manual partitioning option.

As for grub, grub2 to be more precise, you have two options: let Lucid install grub2 to the MBR, or tell Lucid not to install bootloader at all, and keep Hardy grub1. Then after installing Lucid, create manual entry in grub1 for Lucid.

If you want to skip installing the bootloader watch out for the last screen of the installer, hit the Advanced button and choose not to install bootloader.

As for grub2 not booting windows, you misunderstood the problem. Grub2 is just fine booting any OS, including windows. The recent problem plenty people have, is when they are doing an upgrade 9.10->10.04 or 8.04->10.04, there is a window asking you where you want to put grub2, and lets you choose both disks and partitions (they are all listed). It also says, if unsure on which disk is grub that you are currently using, just select all disks.

However, people not making a difference between a partition and a disk, have been marking all of the disks and all of the partitions, putting grub2 on their windows partition too. And since the windows bootloader is just chainloaded to grub, when you select windows it won't boot because the grub2 you put on the partition interferes with the windows bootloader.

---

### Post by oldfred on 2010-05-24
Also if you do not want to install grub2, do not use ext4. Grub legacy was slightly updated with 9.04 to see ext4 partitions. If you use ext4 you will have to somehow update grub legacy, or better just install grub2.

I have 3 Ubuntu's and XP. I keep last install, current install, and beta in separate root partitions and mount my /data. If you mount your /home from 8.04 you may get a lot of updates to user settings and program settings that then may not be compatible with 8.04 versions. With all my data in the /data partition my /home is jsut 1GB so I copy it over for the new version and link in the /data partition.

---

### Post by leehach on 2010-05-24
> **darkod said:**
> As for grub, grub2 to be more precise, you have two options: let Lucid install grub2 to the MBR, or tell Lucid not to install bootloader at all, and keep Hardy grub1. Then after installing Lucid, create manual entry in grub1 for Lucid.

If you want to skip installing the bootloader watch out for the last screen of the installer, hit the Advanced button and choose not to install bootloader.


Thanks, quite helpful. Follow-up questions:

If I let Lucid install GRUB2, will it automatically find and create entries for the already existing OSes (Hardy & Vista) as it would with the Guided option?

If I retain GRUB1, what would the entry for Lucid look like (or can you point me to a place where this has already been answered). 

And how would using GRUB1 work with Lucid updates? Every time Hardy updated the kernel, I got a new GRUB entry. If Lucid usually works with GRUB2, would it be able to keep GRUB1 updated?

Thanks, and thanks for clarifying the issue with installing GRUB2 to multiple partitions.

--Lee

---

### Post by darkod on 2010-05-24
> **leehach said:**
> Thanks, quite helpful. Follow-up questions:

If I let Lucid install GRUB2, will it automatically find and create entries for the already existing OSes (Hardy & Vista) as it would with the Guided option?

If I retain GRUB1, what would the entry for Lucid look like (or can you point me to a place where this has already been answered). 

And how would using GRUB1 work with Lucid updates? Every time Hardy updated the kernel, I got a new GRUB entry. If Lucid usually works with GRUB2, would it be able to keep GRUB1 updated?

Thanks, and thanks for clarifying the issue with installing GRUB2 to multiple partitions.

--Lee

I don't know that much in depth about using grub1 because I started using ubuntu since Karmic which came with grub2. :)

Yes, grub2 will detect all OSs (windows and Hardy) regardless whether you use a guided method or manually partition. IMHO, it's better to use grub2 anyway.

Not sure if grub1 adds new kernels automatically. One more reason to go with grub2. :)

Right now, I don't know the exact syntax for a manual entry in grub1 for Lucid, but it shouldn't be difficult to find. In fact, you should be able to copy the Hardy entry and just change the kernel filename and root partition.

---

### Post by leehach on 2010-05-24
> **darkod said:**
> Yes, grub2 will detect all OSs (windows and Hardy) regardless whether you use a guided method or manually partition. IMHO, it's better to use grub2 anyway.


That's exactly what I needed to know. Because Guided partitioning made a point of saying it gave you a menu of OSes to choose from at startup, I wasn't sure about the implications of the fact that the Manual method does **not** say it recognizes preexisting OSes.

Now that that's clarified, I'll do the install using the Manual method and upgrading to GRUB2.

Thanks again.

---

