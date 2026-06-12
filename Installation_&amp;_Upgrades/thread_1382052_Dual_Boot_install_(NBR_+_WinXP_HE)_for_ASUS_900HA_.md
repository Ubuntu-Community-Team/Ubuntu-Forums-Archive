---
title: "Dual Boot install (NBR + WinXP HE) for ASUS 900HA netbook"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by bigalbig on 2010-01-15
Hi everyone,

I've been had great luck with running the NBR of Ubuntu on my netbook by itself, and want to setup my new hard drive as a dual boot:  (1) The factory install of WinXP Home Edition, and (2) Ubuntu Netbook Remix 9.10.

I've explored and tried several approaches, with little luck.  As best I gather from reading the forums and how-tos, it seems loading the Win install first is the best approach, which I do from the ASUS recovery disk, and the WinXP HE install comes up fine, spread across the entire hard drive (320GB) into a handful of partitions:
/dev/sda1 Win XP Home Edition (~170GB), NTFS ("C:")
/dev/sda2 (~135GB), NTFS ("D:")
/dev/sda3 WinNT/2000/XP (~16GB), NTFS (not sure what this one does, actually)
/dev/sda4 (~40MB), (also not really sure what this one's for)

When I load up the NBR install from my USB, and get to the partioning section (page 4/6), I resize the two largest partitions to try to create room for my Ubuntu install.  The resize appears to work ok, and upon rebooting, Win seems OK, but, the Ubuntu installer won't let me modify the two chunks of disk I've got spare.  In fact, they're both labeled "unusable", I can't specify a mount point, format them... nothing.

I'm hoping to get Ubuntu running on this drive in one open space and setup a small (~2-4GB? swap space) that I've read is needed.

Ideally, I'd like to try to setup a FAT32 partition and experiment with passing stuff between the two OSs, if that's even possible.

Any ideas or pointers on what I'm doing wrong?

Apologies if I'm posting in the wrong place, I'm still a bit of a newb.

---

### Post by tachuela on 2010-01-15
You have to make a space usable FROM Windows; then install Ubuntu

---

### Post by bigalbig on 2010-01-15
Alrighty... lemme give that a shot... 

I hope XP Home lets me manage my partitions... be just my luck they sliced that out making it a Home Edition...

---

### Post by snowpine on 2010-01-15
I have a 900ha as well. Asus foolishly set it up with 4 primary partitions. Because a hard drive can only have 4 primary partitions total, the Ubuntu installer won't work in this situation.

My solution was to delete the D: partition (after backing up all the data on it of course) so that there were only 3 primary partitions. Ubuntu was then able to install itself no problem. 

Good luck!

---

### Post by bigalbig on 2010-01-15
Awesome help, guys, I think this is going to happen!

I'm still plugging away at the XP disk manager, I've deleted my "D:" partition (no data was on it - fresh drive), AND my "PE" partition that the ASUS recovery DVD planted for me last night onto the drive...  Currently my setup stands at 100GB primary NTFS "C:" drive for the XP Home Edition OS, and some piddly little 39MB partition used for some "Boot Booster" from ASUS.  I think I'm gonna leave that alone.

So by my math, I've got two primary partitions left to play with.

By deleting the "D:" partition in XP, it's automatically consolidated all of my Unallocated space together, too, which seems a bit more logical...

Keep you posted.  And THANKS!

---

### Post by bigalbig on 2010-01-21
Success!!!

As did as you said, snowpine, I deleted the entire "D:" drive partition setup automatically by the Asus Recovery CD.  I bumped up the size of the "C:" drive partition it had setup for me that had XP loaded into it.

Then, created another partition using the Ubuntu NBR flash drive setup and voila!  All good.

Pretty damn cool!

Thanks everyone!

---

### Post by BikeMike on 2010-05-21
> **snowpine said:**
> I have a 900ha as well. Asus foolishly set it up with 4 primary partitions. Because a hard drive can only have 4 primary partitions total, the Ubuntu installer won't work in this situation.

My solution was to delete the D: partition (after backing up all the data on it of course) so that there were only 3 primary partitions. Ubuntu was then able to install itself no problem. 

Good luck!
Thank You sooooo much 8-)

I just purchased a Samsung NB30 netbook and couldn't install NBR 10.04 as a dual boot with winblows 7 starter until I found this post. Samsung installs 4 primary partitions as well and until I deleted the (still empty) D partition I had no option to install next to another OS (tick box not there)  in the Ubuntu installer. Once I installed the Ubuntu NBR it took two boots before I could boot back into windows again as others have mentioned.

Learn something new every day ;)

---

