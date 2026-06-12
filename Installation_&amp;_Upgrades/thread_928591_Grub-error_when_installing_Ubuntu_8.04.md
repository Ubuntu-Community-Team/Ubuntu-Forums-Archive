---
title: "Grub-error when installing Ubuntu 8.04"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by SomeIdiot on 2008-09-24
Hey all,
 
This is my first post on this forum and generally I am pretty new to Linux. 

I get the following error when trying to install Ubuntu:

"Executing 'grub-install (hd0)' failed.

This is a fatal error."

I am trying to install on a 20 GB partition. I have already installed Windows XP x64 on a separate partition and the intention is to dual boot these. Additionally I have a ~75 GB NTFS partition.

Well I must say I am pretty lost. I have tried a few guides I have found around these forums about how to install Grub from a live CD, but none have worked for me.

Any help would be appreciated.

---

### Post by Sealbhach on 2008-09-24
Hi,

this thread may have a solution for you.

[http://ge.ubuntuforums.com/showthread.php?t=785260](http://ge.ubuntuforums.com/showthread.php?t=785260)

I think the reason is that XP is already on hd0 so grub can't install itself there.


.

---

### Post by caljohnsmith on 2008-09-24
If the installer fails at 94% with that Grub error, then that is unfortunately a known bug. But the good news is that there are at least two workarounds, and the easiest is probably:

[http://ubuntuforums.org/showthread.php?t=810205](http://ubuntuforums.org/showthread.php?t=810205)

Let me know if that applies to you or not.

---

### Post by fourthofjuly on 2008-09-24
> **SomeIdiot said:**
> Hey all,
 
This is my first post on this forum and generally I am pretty new to Linux. 

I get the following error when trying to install Ubuntu:

"Executing 'grub-install (hd0)' failed.

This is a fatal error."

I am trying to install on a 20 GB partition. I have already installed Windows XP x64 on a separate partition and the intention is to dual boot these. Additionally I have a ~75 GB NTFS partition.

Well I must say I am pretty lost. I have tried a few guides I have found around these forums about how to install Grub from a live CD, but none have worked for me.

Any help would be appreciated.
for starter, maybe you should try the wubi installer method which is far more easier than partitioning...

[http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by SomeIdiot on 2008-09-24
> **caljohnsmith said:**
> If the installer fails at 94% with that Grub error, then that is unfortunately a known bug. But the good news is that there are at least two workarounds, and the easiest is probably:

[http://ubuntuforums.org/showthread.php?t=810205](http://ubuntuforums.org/showthread.php?t=810205)

Let me know if that applies to you or not.

What i understand from the thread that you link to is that it is necessary to delete all the partitions, however I would really hate to have to have to delete all my data and my Windows partition.

Are there any way around this, so that I can preserve the partitions that are already made (or at least the windows installation)?

Just to recap, my partitions are:
C: 15 GB NTFS
D: 20 GB EXT3
E: 80 GB NTFS

The partitions were made using the XP partition tool when installing windows.

Also, I couldn't make out from the thread what the problem actually is. Any info on this?

---

### Post by caljohnsmith on 2008-09-24
Sorry, I guess I should have been more clear about that thread I linked to. The bottom line is that if the Ubuntu installer fails at 94% with the grub-installer error, then you can circumvent that bug by formatting your Ubuntu partition to ext2 rather than ext3. That should allow you to successfully install Ubuntu, and then once you do that, you can "upgrade" your file system from ext2 to ext3 with the following command:
```
sudo tune2fs -j /dev/sdX
```
Where sdX is your Ubuntu partition. In other words, if your problem is the same as what I described above, there should be no need to delete any partitions. Let me know how it goes or if you need more details/info. :)

---

### Post by SomeIdiot on 2008-09-30
Sorry for the time since my last reply, but I haven't had the time to work on it until now.

The problem was indeed solved by selecting ext2 rather than ext3, so thank you very much for the input. I wouldn't have been able to figure that out myself.

I'll try the command to convert the partition later today.

Edit: Before I do though, I was wondering what the advantage of ext3 is over ext2. What I have read is that it is a journaling FS but what will that actually mean for me?

---

