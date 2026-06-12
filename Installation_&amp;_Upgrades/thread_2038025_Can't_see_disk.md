---
title: "Can't see disk"
date: 2012-08-05
forum: Installation &amp; Upgrades
---

### Post by lift_test on 2012-08-05
I'm trying to do an install on a Win 7 computer that has a 2 disk raid array (1 TB) and a 120 MB Western Digital disk.  I want to install to the WD disk but the installer can only see the 2 samsung raid disks, any ideas why?  I've tried normal installer and alternate installer.  The disk shows up as D: in Win 7.

---

### Post by darkod on 2012-08-05
If the disk has been used in raid before, you have to remove the meta data. Just be VERY CAREFUL to select the correct disk, because the other two disks are in raid and if you remove the meta data on one of them you will break the array.

To remove meta data from live mode, do:
```
sudo dmraid -E -r /dev/sdX
```

replacing X with the correct disk letter, like a, b or c, etc.

This is usually the reason why a disk is not showing in the partitioner but it can be another reason too. Try this first.

---

### Post by lift_test on 2012-08-06
Sorry, I didn't make myself clear.  There are 2 Samsung disks as a raid array that is dedicated to Win 7, I want to leave these as is.  I also have a Western Digital disk (presently formatted NFTS) which I want to load Ubuntu on.  The raid works fine for Win 7 which can also see the WD disk.  However when I try to load Ubuntu it only shows the raid disks, it does not offer or show the WD disk as an option.  The WD disk was never part of the raid.
My question was why is the WD disk not showing?

---

### Post by darkod on 2012-08-06
I understand all of this, but are you 100% sure the third disk was never used in any raid (not in the present one)?

Since fakeraid (bios raid) became common many people started playing with it, and the meta data stays there even after format. Windows doesn't care about that because it works in a different way, and will see the disk OK.

But the ubuntu installer ignores disks that have meta data on them.

So, it's good to double check whether you do have raid meta data on it, unaware. Just be careful not to "touch" the samsungs, as I already said.

If you boot the ubuntu cd in live mode and list the disks with:
```
sudo fdisk -l
sudo parted -l
```

Does it list all three of them or not?

Sometimes there can be partition table error or corruption and the disk might not be recognized OK.

---

### Post by lift_test on 2012-08-06
I see what you're saying, it's possible the WD disk was once part of a raid.  I'll try booting from live CD and see what can be seen.
EDIT
Live CD fell over before I could do anything, tried booting with a very old Gentoo Linux that boots straight into parted.  This worked and could only see the WD disk.  I tried formatting it but it failed and now can't be seen in Win 7.  Will try later to load Ubuntu and see what happens.  Thanks for your help.
EDIT
Tried alternate install which showed all 3 disks (and manufacturers names) so was confident choosing correct disk.  Install went OK including detecting Win 7 and installing grub but will only boot into Win 7.  Will try looking in BIOS to see if boot order of disks can be changed.
EDIT
That worked, can now choose Ubuntu or Win 7 but unfortunately Ubuntu falls over.  It runs for a short while but then screen goes blank and then says "no signal".  There is still disk activity but I can't see what is happening.

---

