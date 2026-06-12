---
title: "Side-by-side, not inside"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by mlhudson on 2013-03-30
So I'm a former user who loved ubuntu and then ended up back on Windows for a season. I want to come back, but have some needs for Win apps with work. There used to be an option to install "side-by-side" from the installer. Now it says "install inside windows". I don't want it inside windows, though. I will likely end up getting rid of my windows partitions in time, so I don't want data co-mingled.

How do I do the old "side-by-side" installation now?

---

### Post by ManamiVixen on 2013-03-30
Wubi no longer installs side-by-side with Windows due to numerous complaints about bricked installs. To install side-by-side, you will have to do a normal Ubuntu install and install alongside Windows.

---

### Post by darkod on 2013-03-30
Did you boot the machine from the ubuntu cd, or you put the cd in while running windows? You need to boot the machine with the cd for a proper installation.

---

### Post by mlhudson on 2013-03-30
Thanks for a response! I actually have been looking at the normal install, not Wubi. But, there used to be an automated option in the normal installer to do "side-by-side". I no longer see that option. Now there is one that says "inside", which I'm not after. I guess it is more manual now to dual boot? I'm not sure exactly how to set that up. Any links appreciated.

---

### Post by darkod on 2013-03-30
There should be side-by-side. Did you make unallocated space first? If windows is taking the whole disk, you need to shrink it first and it's best to do that with windows Disk Management.

Then, if you have all 4 primary partitions used, it can't make new partitions for ubuntu because 4 is the limit.
If the disk in windows is Dynamic, it will not be able to install since dynamic is MS proprietary format.

There is something not allowing the side by side option. I recommend the manual option anyway, but probably the issue will be the same, especially if you have 4 primary partitions.

Did you check the partitions in Disk Management? Don't forget that not all appear in Computer. Windows thinks it's amusing to hide your partitions from you. :)

---

### Post by mlhudson on 2013-03-30
Thank you @darkrod! That is the issue. HP made a backup partition, Win8 made one, Win8 uses one (it's an upgrade from Win7, not UEFI), and theres an HP junkware partition...ugh. SO grateful for all the JUNK that Win requires. Well, looks like like I'll either be going "inside" or I'll just have to wait.

---

### Post by darkod on 2013-03-30
Delete the HP_TOOLS partition, it's useless anyway. And you can download the same toold from HP.

Another option, make a set of restore DVDs and after that you can delete the restore partition. That way you can use that space instead of being wasted, and also by deleting one partition the ubuntu installer can create the ubuntu logical partitions it needs.

No need to go with wubi, since that's not really a solution.

---

### Post by mlhudson on 2013-04-01
@darkod THANKS for the help. I went back to Win8, resized the partition there using disk management. Then went back to the Live DVD and the install options were as expected. I appreciate your help!

---

