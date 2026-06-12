---
title: "Advice setting up dual boot, partitions"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by luv2runxc on 2010-12-18
Hi, I am new here and new to Ubuntu. I'd like to dual-boot it with Windows 7, but I'm not sure exactly how I should set things up. Searching has helped but I would really appreciate advice specific to my scenario.

What I'm looking for: Windows 7 to run a couple games (mainly Starcraft II) and for anything that doesn't run on mac or linux, and Ubuntu to do most of my normal everyday stuff (documents, programming projects, web browsing, listening to music).
Hardware: 1TB hard drive, 4GB RAM, AMD Athlon II 435 processor.

My current plan for partitions:
~100 GB: Windows 7 64-bit installation and program files. I've installed Starcraft II, Matlab, and OpenOffice and already hit 50 GB somehow, and want to leave some breathing room.
~20 GB: "/" root partition; Ubuntu v10.10 64-bit installation and program files. I'm planning on installing things like Eclipse and Matlab for programming, possibly more in the future - do I need more space for this?
~5 GB: /home partition for settings. If I'm creating a separate data partition (below), is this a good idea and a good size? I'm not clear on the role of the home folder exactly. Do I even need it separate from the Ubuntu root partition?
~850 GB: data partition that will be shared by Windows 7 and Ubuntu.
Swap space: just use a 4 GB swap file in the Data section rather than a swap partition. Reasoning: 4 GB of RAM is a good amount, so I should need swap rarely. The speed hit shouldn't be a huge deal, and I already have 4 partitions planned which is a lot, plus a few system partitions. If I really need more memory I figure I should get more RAM, I mainly want to rely on swap for hibernating only.


Does this setup seem like a good idea? Are the sizes ok? What changes should I make?

(edit) Can/should I put /home in the Data partition, and can I still format it so that Windows can access everything there? This would be the most convenient option, cause everything I want to back up would be in one partition!

Thanks in advance for any advice!!

---

### Post by sikander3786 on 2010-12-18
Welcome to the forums :-)

If you feel ok, 100 GB would be enough for Windows.

As you've got lots of space, I would recommend to extend the size of Ubuntu '/' partition to 30 GB in order to save you the troubles later. I know you might not ever use up the entire 30 GB but it is always better to be on the safer side.

5 GB /home partition would be enough for storing the settings unless you don't use it to store your personal files/data etc. You'll be storing them to /data partition instead.

You can have a Data partition in all the space left behind and you need to format it NTFS in order to access it both in Windows and Ubuntu.

You can't place a Swap file on an NTFS partition. If you are sure you won't ever need to hibernate/suspend you system, you can live without a swap partition. 4 GB RAM is enough for most tasks. Yet it is recommended that you at least create a Swap partition = size of RAM if you want to hibernate.

You can't put your /home on the shared data partition because NTFS doesn't support Linux permissions ;-) /home need to be ext3/ext4.

Said that, my partitioning plan would be,

1. Primary Windows partition, 100 GB, NTFS

2. Primary Shared Data Partition, XX GB, NTFS

3. Extended Partition

3a. Logical Ubuntu / Partition, ext4, 30 GB

3b. Logical /home Partition, ext4, 5 GB

3c. Logical Swap Partition, 4 GB

---

### Post by zeimusu on 2011-01-01
Would it be possible use ifsdrive ([http://www.fs-driver.org/](http://www.fs-driver.org/)) in windows, have a single shared ext2 partition with /home. I notice that this is a 64bit system, I'm not sure that ifs filesystems will work with 64bit. Generally I'd worry about doing this, the ifs driver isn't open source so I'd worry about it just not working, and I'm not sure about its performance, but I wonder if anyone has done this.

---

