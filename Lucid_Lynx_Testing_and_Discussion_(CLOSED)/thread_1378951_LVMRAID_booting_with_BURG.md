---
title: "LVM/RAID booting with BURG"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bean123 on 2010-01-12
I'm about to make some improvement on LVM/RAID setup, here are some issue I know of:

Only support version 0.9 metadata
Can't write to LVM/RAID, as a result, save default doesn't work.

Is there other open issue ?

---

### Post by phillw on 2010-01-12
Hi, you might want to take a wander over onto the 9.10 area - it will let you know the issues with grub 1.97beta - I've a couple of heartfelt pleas to keep my eye on grub2 - at present the work-around seems to be going back to grub legacy and keeping 9.10, or going back to 8.04.3  with the expectation that 8.04.4 will be okay for them as they await 10.04 -- I don't have facility to test raid setups out, but there will be a couple on there who may volunteer.

That's not just for burg, I'm not in the camp of burg Vs grub ( Section #8 of Dave's post [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)) - within the community we are entitled to our differences - but should pull together when there is a problem like RAID that is a complete show-stopper for those using it who want to come over to the next LTS.

Do you take the grub engine, and then add in the theming ?

Regards,

Phill.

---

### Post by bean123 on 2010-01-12
Just upload a package 1.97+burg.20100112-1~ppa6 for karmic, corresponds to bzr r1806.

Support new version metadata 1.0, 1.1 and 1.2 (grub only supports 0.9), use the -e option in mdadm to specify version number, for example:

mdadm -C /dev/md0 -e 1.0 ...
mdadm -C /dev/md0 -e 1.1 ...
mdadm -C /dev/md0 -e 1.2 ...

---

### Post by bean123 on 2010-01-12
> **phillw said:**
> 
Do you take the grub engine, and then add in the theming ?


Besides themes, I also make improvement in other area, for example:

Use new object format. It's much compact than the current format, and save up to 2-3K in a lzma compressed image about 63 sectors. This is important when we need to embed it in mbr, which normally has no more than 63 sectors. For example, lvm + raid + raid5rec + raid6rec + reiserfs couldn't fit in 63 sectors using grub2, but it's ok for burg. BURG also make it possible to embed fs like zfs.

Remove nested function. Nested function need to execute code on stack, which causes issue on OSs like OSX. And due to a bug in gcc, it needs to use a macro NESTED_FUNC_ATTR in some situation, which is quite ugly.

---

### Post by ranch hand on 2010-01-12
> **bean123 said:**
> Besides themes, I also make improvement in other area, for example:

Use new object format. It's much compact than the current format, and save up to 2-3K in a lzma compressed image about 63 sectors. This is important when we need to embed it in mbr, which normally has no more than 63 sectors. For example, lvm + raid + raid5rec + raid6rec + reiserfs couldn't fit in 63 sectors using grub2, but it's ok for burg. BURG also make it possible to embed fs like zfs.

Remove nested function. Nested function need to execute code on stack, which causes issue on OSs like OSX. And due to a bug in gcc, it needs to use a macro NESTED_FUNC_ATTR in some situation, which is quite ugly.
That is very nice.  I can't stand raid, myself, and I, so far, have not used encryption, but these things need to be supported.

Assuming your fixes work (good track record), great work.  Thank you for your efforts.

---

### Post by Qboy61 on 2010-01-27
I have been using Ubuntu since 7.04 but I only use it on my laptop machines.  My desktop machines (4 of them) have Intel RAID in various configs.  2 Machines are configured as 2 drives (40+40=80) in RAID 0 with system and programs, and 2 drives (large ones) in RAID 1 with the home directories (or Documents and Settings for that other OS).  The other 2 are multi-partitioned RAID 1.  All of these RAID machines are to important to lose due to an error in Ubuntu RAID.  I hope that Lucid will fix the Ubuntu/RAID issue so that I can use this OS on those machines.

Thanks, keep up the good work!

---

### Post by phillw on 2010-01-27
> **Qboy61 said:**
> I have been using Ubuntu since 7.04 but I only use it on my laptop machines.  My desktop machines (4 of them) have Intel RAID in various configs.  2 Machines are configured as 2 drives (40+40=80) in RAID 0 with system and programs, and 2 drives (large ones) in RAID 1 with the home directories (or Documents and Settings for that other OS).  The other 2 are multi-partitioned RAID 1.  All of these RAID machines are to important to lose due to an error in Ubuntu RAID.  I hope that Lucid will fix the Ubuntu/RAID issue so that I can use this OS on those machines.

Thanks, keep up the good work!

Grub 1.98 which we are on with Lucid has had a lot of RAID work done. [http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)  is the dev area for it.

I know bean123 has also added a lot of extra RAID support into burg, so fears of no RAID for Lucid can be pretty much allayed :D

Regards,

Phill.

---

### Post by nanog on 2010-01-27
> I can't stand raid, myself, 

!

Whats not to like about raid? I have not run ~/ on anything other than raid volumes for years. Even my home media system runs off of raid6 nfs shares (gotta do something with all those 80-320 gb hard drives i accumulate). 

> BURG also make it possible to embed fs like zfs.


ZFS using fuse? If so, performance is terrible.

---

### Post by bean123 on 2010-01-27
> **nanog said:**
> 
ZFS using fuse? If so, performance is terrible.

Not fuse, phcoder has imported the zfs fs reader from solaris's grub, but it's too large to be embedded in mbr.

---

### Post by imkqm6 on 2010-02-05
I was directed here to ask for help.  I have raid and cannot install anything linux due to it's various boot loaders. I was hoping someone could help me figure out what is going wrong. My info:
P4C800-E motherboard
2 Seagate 250Gb Hard drives, RAID controlled by Fasttrak 
I have Ubuntu 9.10, regular and alternate, and 10.04 Alpha 2 , alternate.
I can tell you the steps I have taken if you want, but nothing I have tried has worked. I was told burg might be the fix I need, but I don't know how to get a copy of 10.04 with burg. 

here are the steps I have taken on the 10.04 alternate disk...you can skip this if you want, I tried to be very detailed on my actions. 

starting bios, settings at near default, open fasttrak, and set raid to raid(0) for performance

skip boring parts
activate serial Raid? yes
Partition? Guided partition and set-up LVM
selected Serial ATA Raid 500Gb
Volume Group amount? 50%
following format
  partition #5 ast ext2
  LVM VG ######, LV root as ext4
  LVM VG ######, LV swap_1 as swap
write? yes
install base system
name and passwords
encrypt home dir? no
http proxy? none
then it says say i chose not to install grub, (which I never said not to?) continue? yes
install grub fail.
it won't let me install it, even though I chose not to continue, so eventually I chose continue w/o installing grub.
Install LILO? yes, all fail
cannot finish install



I tried everything under advanced setup, So i guess my questions are:
1. Do I need to set up raid using FastTrak or have no raid set?
2. Does BIOS need to be configured a certain way?
3. I am installing 10.04 even though its in Alpha  because I hear it has better raid properties than 9.10, is there something I am doing wrong during install?
4. How can I get this to work?

Sorry for the long post, I am determined to get this to work...
thank you for your help, I am not the best with linux

---

