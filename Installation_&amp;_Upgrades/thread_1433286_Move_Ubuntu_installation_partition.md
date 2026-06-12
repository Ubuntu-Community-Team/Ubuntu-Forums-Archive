---
title: "Move Ubuntu installation partition"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by whoopy_whale on 2010-03-18
Hi,

I'm new to Ubuntu and after installing it, found really interesting.

I use mainly Windows Vista and installed Ubuntu in a small partition. After using Ubuntu for a while, the partition is nearly full. I need to try out building Android in my machine and the repo sync failed in between due to lack of space. 

Please see the attached screen shot of GParted.

I had installed Ubuntu in sda7 and how can I move these contents to another drive with more space, say for example sda3 or sda4?

I just need to move my Ubuntu installation to a drive with more space and it should boot from that drive next time and my Vista installation should be intact.

Please help :D

---

### Post by srs5694 on 2010-03-19
There are several ways to do this. You'll find it easiest to do most of them if you first reboot into a Linux emergency disc. (Your Ubuntu install disc may do, or you could use [PartedMagic](http://partedmagic.com) or [System Rescue Cd.](http://www.sysresccd.org))

If you say you're willing to completely sacrifice either /dev/sda3 or /dev/sda4 (copying all files off them or losing all their files), then I recommend this:


[list=1]
[*]Launch GParted from an emergency disc (this procedure won't work from a boot of your hard disk-based Ubuntu installation)
[*]Delete /dev/sda3
[*]Expand /dev/sda2 (the extended partition) to cover the space formerly used by /dev/sda3
[*]Expand /dev/sda7 into the extra space that's now available in the extended partition
[*]Apply your changes
[*]Reboot
[/list]


In theory, the system should now boot up and work normally with no additional changes. Of course, Murphy's Law says that theory and practice may not agree.

There are some variants of this that you may want to consider:


[list]
[*]Instead of deleting /dev/sda3, you could shrink it and move it to the right. This will give you less expansion space for Linux, but if you want to save files on this partition, it should work.
[*]Instead of deleting /dev/sda3, you could delete /dev/sda4, move /dev/sda3 to the right, and then expand /dev/sda2 and /dev/sda7.
[*]Instead of or in addition to expanding /dev/sda7, you can create one or more new partitions for use in Linux. You could use it as a separate /home partition, for instance. This sort of use might require moving part of your current Linux installation to the new partition(s) and editing /etc/fstab to mount them at appropriate mount points. Attempt this only if you already understand such things or want to learn about it now.
[/list]

---

### Post by gadolinio on 2010-03-19
> **srs5694 said:**
> there are several ways to do this. You'll find it easiest to do most of them if you first reboot into a linux emergency disc. (your ubuntu install disc may do, or you could use [partedmagic]("http://partedmagic.com") or [system rescue cd.]("http://www.sysresccd.org"))

if you say you're willing to completely sacrifice either /dev/sda3 or /dev/sda4 (copying all files off them or losing all their files), then i recommend this:


[list=1]
[*]launch gparted from an emergency disc (this procedure won't work from a boot of your hard disk-based ubuntu installation)
[*]delete /dev/sda3
[*]expand /dev/sda2 (the extended partition) to cover the space formerly used by /dev/sda3
[*]expand /dev/sda7 into the extra space that's now available in the extended partition
[*]apply your changes
[*]reboot
[/list]


in theory, the system should now boot up and work normally with no additional changes. Of course, murphy's law says that theory and practice may not agree.

There are some variants of this that you may want to consider:


[list]
[*]instead of deleting /dev/sda3, you could shrink it and move it to the right. This will give you less expansion space for linux, but if you want to save files on this partition, it should work.
[*]instead of deleting /dev/sda3, you could delete /dev/sda4, move /dev/sda3 to the right, and then expand /dev/sda2 and /dev/sda7.
[*]instead of or in addition to expanding /dev/sda7, you can create one or more new partitions for use in linux. You could use it as a separate /home partition, for instance. This sort of use might require moving part of your current linux installation to the new partition(s) and editing /etc/fstab to mount them at appropriate mount points. Attempt this only if you already understand such things or want to learn about it now.
[/list]


+1

---

### Post by whoopy_whale on 2010-03-20
> **srs5694 said:**
> There are several ways to do this. You'll find it easiest to do most of them if you first reboot into a Linux emergency disc. (Your Ubuntu install disc may do, or you could use [PartedMagic](http://partedmagic.com) or [System Rescue Cd.](http://www.sysresccd.org))

If you say you're willing to completely sacrifice either /dev/sda3 or /dev/sda4 (copying all files off them or losing all their files), then I recommend this:


[list=1]
[*]Launch GParted from an emergency disc (this procedure won't work from a boot of your hard disk-based Ubuntu installation)
[*]Delete /dev/sda3
[*]Expand /dev/sda2 (the extended partition) to cover the space formerly used by /dev/sda3
[*]Expand /dev/sda7 into the extra space that's now available in the extended partition
[*]Apply your changes
[*]Reboot
[/list]


In theory, the system should now boot up and work normally with no additional changes. Of course, Murphy's Law says that theory and practice may not agree.

There are some variants of this that you may want to consider:


[list]
[*]Instead of deleting /dev/sda3, you could shrink it and move it to the right. This will give you less expansion space for Linux, but if you want to save files on this partition, it should work.
[*]Instead of deleting /dev/sda3, you could delete /dev/sda4, move /dev/sda3 to the right, and then expand /dev/sda2 and /dev/sda7.
[*]Instead of or in addition to expanding /dev/sda7, you can create one or more new partitions for use in Linux. You could use it as a separate /home partition, for instance. This sort of use might require moving part of your current Linux installation to the new partition(s) and editing /etc/fstab to mount them at appropriate mount points. Attempt this only if you already understand such things or want to learn about it now.
[/list]

Thanks a lot!

It worked :popcorn:
I deleted sda3 and expanded sda7

---

### Post by gadolinio on 2010-03-20
> **whoopy_whale said:**
> Thanks a lot!

It worked :popcorn:
I deleted sda3 and expanded sda7

Well done! 
Don't forget to mark the thread as "solved", so that users willing to help know that no further help is needed, and users with the same question know that there's an answer here.

---

