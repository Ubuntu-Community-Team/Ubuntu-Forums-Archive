---
title: "Disk partitioning for dual-boot"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by exXP on 2010-01-10
I have a new win7 system with a 500GB HD.  What is considered the safest way to partition the disk before installing Ubuntu?
exXP

---

### Post by darkod on 2010-01-10
Is it taking the whole disk right now? Just one single partition?
Open win7 disk management, right click on the partition and use Shrink Volume. That will create unallocated unpartitioned space for ubuntu.
After that boot win7 few times to make sure it's happy after the shrink.
Then just boot with the ubuntu cd, select Install Ubuntu and tell it to Use Largest Available free space. That's it.

If you don't know where to find win7 disk management, press windows button + R, type in the box diskmgmt.msc and hit Enter.

---

### Post by exXP on 2010-01-11
Thank you for your response - sorry to be so long answering.
The disk has 3 partitions 1) System 100M 2) HP (C) 453G and 3) Factory Image 12.8 G.
The computer is (obviously) a HP and I'm not sure what the partitions do.  If I shrink the middle partition, I will presumably create a new partition between 2) and 3) where Ubuntu could go.  However, will the present partition 3) still perform its function in Win 7?   From what I have seen so far Win 7 looks quite good and I don't want to lose it.  But I still want Ubuntu.  Perhaps I should start a new thread appealing to HP users who have done this
exXP

---

### Post by darkod on 2010-01-11
Sometimes the factory image can create problems because it would have to remain at the back, as you said. But this doesn't happen always.
One alternative is to use the win7 Backup and Restore feature and create your own image of your system as it is right now. Depending how much stuff you have installed this image may be quite large. Otherwise, once you have this image created on DVDs or similar, you don't actually need the factory image. Your own image is much better anyway because it will restore your windows as it is right now. I think there is also option to create bootable dvd/cd, and then to have the backup image on external hdd, that might be better than burning 5-6 DVDs (sometimes more).

Regardless how you like the above idea, for installing ubuntu you would have to:
1. Backup the data you need from your windows partition.
2. Open disk management in win7 and shrink the C: partition for at least 30GB (or more depending how much space you want to allocate to ubuntu).
3. Boot win7 few times to check it's happy after the shrink. It will probably do few disk checks.
4. The shrink will create 30GB unallocated space on your hdd, leave it as it is. DO NOT create any partitions for ubuntu yourself, especially not from windows.
5. Once ready to install ubuntu, boot with ubuntu cd, Install Ubuntu option, and in step 4 tell it to use Largest Available Free space. That will use the 30GB to install ubuntu there.

That should be it.
After installing ubuntu don't be confused if the grub bootloader menu offers a choice for win7 and maybe vista too, or another win7. One will be your win7 installation, and the other will be the factory recovery partition (if you keep it). Selecting the other entry should start the win7 recovery process.

---

### Post by exXP on 2010-01-11
Thank you again.  I'll sleep on this and try it when I feel lucky.  I've used Ubuntu from 6.10 up 9.04 so I feel I really must have it.  Given the choice of Windows or Ubuntu, I'd probably choose Ubuntu!
exXP

---

### Post by jontyrp on 2010-01-11
> **exXP said:**
> Thank you for your response - sorry to be so long answering.
The disk has 3 partitions 1) System 100M 2) HP (C) 453G and 3) Factory Image 12.8 G.
The computer is (obviously) a HP and I'm not sure what the partitions do.  If I shrink the middle partition, I will presumably create a new partition between 2) and 3) where Ubuntu could go.  However, will the present partition 3) still perform its function in Win 7?   From what I have seen so far Win 7 looks quite good and I don't want to lose it.  But I still want Ubuntu.  Perhaps I should start a new thread appealing to HP users who have done this
exXP

Hi exXP,
The partitions on your HP HDD do the following;
1) (100Mb) - Windows 7 Boot Partition
2) (HP (453Gb)) - The Windows 7 System Partition, where Windows runs from.
3) (Factory Image (12.8Gb)) - The HP Restore Image for returnting the system to the factory delivered State.

As has already been suggested you should use the Disk Management App in the Computer Management Console to shrink the "C" Partition. A couple of things to be aware of though, is that you should defragment the ''C" Partition before you try the shrinking. If you don't do this you might find that you can not shrink the partition all that much. An alternative would be to use a third-party disk partitioning program, such as Acronis Disk Director Suite, my personal favourite, instead. Also be aware that you can ONLY have 4 (FOUR) Primary Partitions on your HDD, so you can only create 1 (ONE) new Primary Partition as you already have 3 (THREE) on there!

Hope all goes well with your attempt to dual-boot.

Jonathan.

---

### Post by raymondh on 2010-01-11
The system 100mb is a windows bootloader image ...  default in a win7 install.  That 100mb contains pre-cached repair files.  Needed?    Not if you have a install disc, or are using GRUB.

Since you have 3 primary partitions already, the ubuntu liveCD will install a extended partition that will house ubuntu root (/) and swap.

GRUB2 will also install/overwrite the bootloader.

If you decide you want to go back windows and it's original bootloader, you'll need to restore the MBR using either a win7 install disk or a 3rd-party recovery disk like [neosmarts']("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") (as hinted above)

As always, have a working/tested back-up.

Raymond

---

### Post by presence1960 on 2010-01-11
> **jontyrp said:**
> Hi exXP,
The partitions on your HP HDD do the following;
1) (100Mb) - Windows 7 Boot Partition
2) (HP (453Gb)) - The Windows 7 System Partition, where Windows runs from.
3) (Factory Image (12.8Gb)) - The HP Restore Image for returnting the system to the factory delivered State.

As has already been suggested you should use the Disk Management App in the Computer Management Console to shrink the "C" Partition. **_A couple of things to be aware of though, is that you should defragment the ''C" Partition before you try the shrinking. If you don't do this you might find that you can not shrink the partition all that much_**. An alternative would be to use a third-party disk partitioning program, such as Acronis Disk Director Suite, my personal favourite, instead. *_Also be aware that you can ONLY have 4 (FOUR) Primary Partitions on your HDD, so you can only create 1 (ONE) new Primary Partition as you already have 3 (THREE) on there!_*

Hope all goes well with your attempt to dual-boot.

Jonathan.

I would also disable System restore in Control Panel as well as defragging C: at least two times. Once Ubuntu is installed you can then enable System restore.

These actions are necessary to have a smooth resize of windows C: because windows has a bad habit of scattering files from one end of it's partition to the other end. Defragging those & getting rid of System Restore temporarily will make the resize much smoother.

I would not create a primary partition but rather an extended partition. If you create a primary you are going to be up the creek without a paddle if you desire a separate home or another data partition or a swap partition. See [here]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics") and read about extended partitions.

Inside an extended partition you can create as many logical partitions as you like- the only restriction being the amount of space you allocated to the extended partition. Unlike windows, linux will boot from an extended partition.

---

### Post by exXP on 2010-01-12
Thanks to every one for the very helpful replies. I feel much more confident now.
exXP

---

### Post by presence1960 on 2010-01-12
> **exXP said:**
> Thanks to every one for the very helpful replies. I feel much more confident now.
exXP

Let us know how it goes!

---

### Post by exXP on 2010-01-13
Success!  However there was a miner glitch when I tried to install 9.04.  The disk partitioner came up with the correct breakdown of partitions but when I selected 'Greatest Free Space' it put most of the unallocated space back into the main Win 7 partition and was going to allow 9.04 a measly 2.7GB!  I aborted this quickly and tried  9.10 instead.  This worked perfectly.  I would rather have had 9.04 since there appear to be stability problems with 9.10 but I'm hoping that they get solved along the way.
Thank you all for your help along the way.
exXP ( I guess I'll have to change my name now that XP is passe)

---

### Post by presence1960 on 2010-01-13
> **exXP said:**
> Success!  However there was a miner glitch when I tried to install 9.04.  The disk partitioner came up with the correct breakdown of partitions but when I selected 'Greatest Free Space' it put most of the unallocated space back into the main Win 7 partition and was going to allow 9.04 a measly 2.7GB!  I aborted this quickly and tried  9.10 instead.  This worked perfectly.  I would rather have had 9.04 since there appear to be stability problems with 9.10 but I'm hoping that they get solved along the way.
Thank you all for your help along the way.
exXP ( I guess I'll have to change my name now that XP is passe)

Glad you got it working. Enjoy Ubuntu.

---

### Post by raymondh on 2010-01-13
Glad as well :)

happy ubuntu-ing

Raymond

---

### Post by exXP on 2010-01-15
I thought I had made a reply yesterday but it seems to have gone astray.  The gist of what I said was that the operation was successful!  Thank you all for helping along the way.  One minor glitch was that I could not use 9.04, which would have been my preference.  When I tried to install GParted showed the correct arrangement of partitions but when I specified 'Install Using the Largest Free space', it returned the bulk of this free space to Win7 and allotted a measly 2.7GG to Ubuntu.  So I aborted and tried 9.10.  No trouble there.  Since then 9.10 has been reliable and I've had none of the freeze-ups that I was getting with my previous system.
exXP

---

