---
title: "Best way to install Windows on a 4-partition Ubuntu box?"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by Kurtosis on 2012-08-15
Hi all, I have a laptop with Ubuntu 12.04 x64 using 4 primary partitions (gparted screenshot attached):

/dev/sda1 - ext4 - /boot - 190MiB
/dev/sda2 - linux-swap - 14.90MiB
/dev/sda3 - ext4 - / - 78.14MiB
/dev/sda4 - extended - - 372.53MiB
- /dev/sda5 - ext4 - /home - 372.53MiB
unallocated - unallocated - - 1.02MiB

Is it still the case that you can only have 4 primary partitions in a dual boot system?

If so, all I really want is to keep /home on a separate partition from everything.  I don't care how the rest are combined, but not sure it's possible to combine /, swap, and/or /boot.

Is there a way to dual boot Windows while keeping /home on its own partition?  Preferably Windows XP, since it's only Windows I already own, but if this can be done with Windows > XP, I'd appreciate hearing it too.

Thanks!

---

### Post by mwl128340 on 2012-08-15
not saying one way or the other, but i have dual boot with linux/xp and after may formats and partioioning, ive found putting the dows partioion at the front really made everything else easy. both read and experienced that, now i have mint, kubuntu, and xp booting like a charm.

---

### Post by mwl128340 on 2012-08-15
and the lvm's i found that late in the game and would recommend but windows would require a primary

---

### Post by oldfred on 2012-08-16
You do not have to have a separate /boot for most systems. You can move swap to a logical as most default installs make swap a logical or you can convert to a swap file. If you delete your current swap and create a new one, you will have to edit fstab. You can even move /boot back into / (root) but have to reinstall grub & remove entry from fstab.

But the extended partition can only be one partition and all logicals have to be inside that one extended. So you have to plan partitions, sizes and locations on drive. You will have to have good backups as you will probably have to move some partiitons around.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by Kurtosis on 2012-08-16
> **mwl128340 said:**
> not saying one way or the other, but i have dual boot with linux/xp and after may formats and partioioning, ive found putting the dows partioion at the front 

Thanks mw.  Clarification: What's the 'dows' partition?

---

### Post by Kurtosis on 2012-08-16
> **mwl128340 said:**
> and the lvm's i found that late in the game and would recommend but windows would require a primary

Ok, will check out lvm partitioning schemes too, thanks.

---

### Post by Kurtosis on 2012-08-16
> **oldfred said:**
> You do not have to have a separate /boot for most systems. You can move swap to a logical as most default installs make swap a logical or you can convert to a swap file. If you delete your current swap and create a new one, you will have to edit fstab. You can even move /boot back into / (root) but have to reinstall grub & remove entry from fstab.

But the extended partition can only be one partition and all logicals have to be inside that one extended. So you have to plan partitions, sizes and locations on drive. You will have to have good backups as you will probably have to move some partiitons around.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

Awesome, thanks, just what I was hoping for.  Sounds like the most painless way to do this to move /swap to a logical partition in sda4, and reallocate the old /swap primary to windows.

Any idea where on the disk the new /windows partition should go?  Can it go anywhere, or need to go near the front or something?

---

### Post by oldfred on 2012-08-16
Physical location on drive does not matter, partitions do not have to be in any order on drive, although some of the partitioning tools may just tell you they are not in order.

Windows requires a NTFS formated primary partition (sda1 thru sda4) with the boot flag to install. Most minimum suggestions I have seen is XP should be 20GB and Vista/7 30GB. They may install in less and will quickly consume a lot more if you install lots of stuff. 

If dual booting I often suggest a separate shared data NTFS partition. The Linux NTFS driver shows all the hidden files & folders in the Windows system partition. You then can accidentally damage something or we seem to see users have issues if they write too much from Ubuntu into Windows. Best to set Windows system to read-only and use another NTFS as the read-write shared data partition. Windows system partition  can be a little smaller but it often takes some effort to get Windows to save somewhere else than its system partition. Shared NTFS can be logical also.

---

### Post by Kurtosis on 2012-08-16
Thanks Fred.  So to have separate Windows System and Windows Data partitions, I would need to free up two primaries, which would have to be done by putting both /boot an /swap on logical partitions in sda4 (currently my extended partition)?

---

### Post by oldfred on 2012-08-16
Windows has to boot from a primary, but even second installs of Windows (do not ever delete first install) can be in a logical. Or the data partition does not have to be a primary.

---

### Post by Kurtosis on 2012-08-17
Thanks again fred, all done and working.  Much appreciated!

---

### Post by oldfred on 2012-08-17
Glad it is working. :)

---

