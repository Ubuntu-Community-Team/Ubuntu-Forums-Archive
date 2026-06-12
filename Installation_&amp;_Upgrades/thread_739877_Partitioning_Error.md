---
title: "Partitioning Error"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by MiniK on 2008-03-30
Hey. I've had a look around and I can't find any answers.

I've got a Windows XP PC and I'm trying to partition the computer and install Ubuntu on the other. I booted from the Ubuntu Live disk and started the install process. When I got to the partition part, I set the Ubuntu partition to 52%. When the Ubuntu partitioning process started, I got an error saying "cannot write to disk - partitioning aborted" or something like that.

Does anybody know how I fix this error?

---

### Post by forestpixie on 2008-03-30
I would first boot back into xp and defrag a few times - then try again with the partitioning. When you boot the livecd - before you run it check the cd for error.

When you set the slider the % you get is the size that the original partition will be eg if you had 100Gb before and you set the slider at 60% - the original partition will resize to 60Gb and you will have 40Gb for the install of ubuntu

---

### Post by MiniK on 2008-03-30
I don't think there can be anything wrong with Windows XP because I only recently formatted my HD and reinstalled it. Also, my friend used this live CD and it works perfect for him - however, he  did not partition - he used the full HD.

---

### Post by logos34 on 2008-03-30
> **MiniK said:**
> I set the Ubuntu partition to 52%. When the Ubuntu partitioning process started, I got an error saying "cannot write to disk - partitioning aborted" or something like that.

If you mean you tried to shrink the ntfs partition by more than half, I don't believe windows will allow that.  That's what I read recently anyway (yeah, I know f***ing Microsoft!).  Try what forestpixie suggested. Or try temporarily disabling swap, hibernationa and system restore in windows--it's possible they're located toward the end of the partition, preventing resizing.  (more [here]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")).

---

### Post by housam on 2008-03-30
- First of all you have to back-up your data - just in case.
- Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.(system >> admin. >> Gparted )
- You can create up to only 4 primary partitions on single HDD.( you already have two of them , one has windows and the other for the recovery )
-I suggest to create one more primary partitions for your data and another one as extended partition which can be devided to many logical partitions (resizing windows partition and creating two new partitions)
- the extended partition can be devided to 2 partitions : one EXT3 ( 10 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / ) .

---

