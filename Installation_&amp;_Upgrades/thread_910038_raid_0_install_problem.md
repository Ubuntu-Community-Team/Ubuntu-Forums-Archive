---
title: "raid 0 install problem"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by hoodlikegaza on 2008-09-04
hi, I am using Kubuntu 8.02 with KDE 4. I followed the tutorial on installing fakeraid, but I just can't get it right after about 5 hours straight. This is what fdisk is telling me:

```
Disk /dev/mapper/nvidia_ccabbajc: 74.3 GB, 74355703808 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa44b9c2d

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_ccabbajc1   *           1       13055   104864256    7  HPFS/NTFS
/dev/mapper/nvidia_ccabbajc2           13056       17886    38805007+  83  Linux
/dev/mapper/nvidia_ccabbajc3           17887       18079     1550272+  82  Linux swap / Solaris
```

When I try to install after installing dmraid, only each separate drive shows up in the partitions list (no trace of the raid). But as this shows, the partitions are there, but it's still being identified as a single 74 gig drive? I really don't understand what I'm doing wrong. If anyone that's more experienced can easily see the problem, I'd appreciate some help trying to get this right.

---

### Post by hoodlikegaza on 2008-09-04
anyone?

---

### Post by hoodlikegaza on 2008-09-04
wow... no one?

---

### Post by hoodlikegaza on 2008-09-06
Um, right, thanks

---

### Post by hoodlikegaza on 2008-09-08
Does anyone at least know if it's possible to dual boot vista and kubuntu on a software raid 0 (specifically an nvidia 780i chipset)? I don't want to loose my vista partition.

---

### Post by hoodlikegaza on 2008-09-09
considering I'm the only one responding to my own thread, I guess the answer is no.

Thanks

---

### Post by hoodlikegaza on 2008-09-10
Just read that it should have better implementation in 8.10. Hopefully it works, I was really hoping this wouldn't have been so complicated, but I can confirm that attempting to dual boot vista and 8.04 is nearly impossible, unless you are very familiar with linux command lines (even then, it's not clear that it's possible).

---

### Post by hoodlikegaza on 2008-09-19
Would anyone care to share weather or not dmraid is working properly in Alpha six, dual booting vista? Someone posted that it still wasn't working in Alpha 5.

---

### Post by hoodlikegaza on 2008-10-06
I just tried it. While it will install using the fakeraid method, I am having a problem getting it to boot. It's dropping to a busy box at boot, and I don't know what to do.

---

### Post by hoodlikegaza on 2009-05-29
I'm thinking about trying again with the 9.04. Does anyone know if it's still necessary to use the alternate cd to install?

---

### Post by raymondh on 2009-05-29
Hello,

Another forum member and I were trying to figure out GRUB with raid 0.  He's now trying to force GRUB to load.  Googling Raid and GRUB,  it seems that GRUB is RAID-aware but limited to RAID 1 mirror.

See this links for reference.

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)
[http://ubuntuforums.org/archive/index.php/t-846629.html](http://ubuntuforums.org/archive/index.php/t-846629.html)

This is the thread we were working on.

[http://ubuntuforums.org/showthread.php?t=1173263](http://ubuntuforums.org/showthread.php?t=1173263)

He might post back results that can help you.

I have not played enough with RAID to know its' runnings with Ubuntu.

Good luck,

---

### Post by ronparent on 2009-05-29
One of the current problem with fakeraid is lack of up to date documentation. This site - **[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)** - for instance gives clear instruction for installing 8.10 to a raid partition. With 9.04 I believe I have experienced a dmraid failure to activate on boot, more serious with raid0 than raid1. Since I don't boot to a raid this is not fatal for me. If experience by anyone attempting to boot 9.04 from a raid0 array, the boot files will not be found! This behavior is different from what I had been experiencing with 8.10. In that case my raid array was always active and automatically mounted by fstab during  boot. With 9.04 I now have to manually activate and mount my raid partitions. In sum it is unclear to me if 9.04 can be sucessfuly booted if installed to a raid0 partition. I for one will be watching to see how you make out.

---

### Post by LaughingBubba on 2009-05-30
I'm in a similar position. 9.04 live won't see raid0 partion but does see the inidividual drives. The alternate CD sees the raid0 partitiion and the one drive that isnt raided my problem is the at the raid0 partitiion is formatted as ntfs with about 8mb unallocated) WinXP so I suspect I need to resize it. 

The prevously mentioned how to 'fake raid' advises against tools such as Gparted but that is based on 7.10 i think.

I'm sure I could do it from a command line but the one raid  controller manufacturer that keeps comming up is [http://www.3ware.com/]("http://www.3ware.com/") who have Linux drivers for their products.

I agree with most of the commentary that software raid is a waste of time and when I asked my pc supplier to provide RAID on my new PC I assumed it would be via a proper raid card not the cheapie solution on board. Had I know that I would have been more explicit about it. 

The problem is the controlers are a bit exy $$$ so I'm looking at a 2nd hand one. I'm not interested in wasting my time on this anymore as I'm nore interested in setting up Kubuntu and Ubuntu Studio.

Worst case I'll clone the partition and remove raid and have separate drives for each OS and be happy with that.

To be honest I was more interested in RAID5 than RAID0 because I didn't want to lose my data (hot swap has it's merits).

Who knows if the next release will solve it? Who cares?

Time and life is short.

---

