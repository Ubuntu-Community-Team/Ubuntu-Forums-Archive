---
title: "Raid issues on install"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by tracemyers on 2008-06-22
On installing 8.04, ubuntu erroniously recognized all of the drives attached to my raid card as ide drives and began formatting one of them during a guided install using the largest contiguous empty space which should have been the 60 plus gb free on my primary drive as my raid array is actually full. I saw that it was beginning to format the drive and stopped it asap. unplugged the entire array, re accomplished the install which installed correctly this time and booted to ubuntu. I then booted back into xp after re-attaching the raid array. xp recognized the drive fine, and most of the data is fine except for in one of my folders....of course, the largest folder full of my av files. Any idea how to recover from this? the data should still be there correct? only marked for deletion? I have unplugged all the drives and am waiting until I know what is going on before I try again to hopefully increase my chances of recovery. Any help would be greatly appreciated. 

ASUS Stryker Extreme
2xGigabyte 8800GT
4x250GB WD on Highpoint Rocketraid card

---

### Post by bsmith1051 on 2008-06-23
what kind of array was it, i.e., RAID-0 (stripe) RAID-1 (mirror) or RAID-5 ?  Unless you spell-out exactly how the drives were arranged, and partitioned, there's no way anyone can answer your question.

P.S.  Does your Highpoint card include Linux drivers?  If not then it's probably a 'fake RAID' card and you'd be better-off letting Ubuntu do the RAID via software (at least for RAID-1).

---

### Post by tracemyers on 2008-06-23
raid 5 and yes, it would be what you call "fake raid" or rather software raid as the card does not include it's own processor and host controller. There are linux drivers available and I will install them once the raid array is fixed although next week I will be purchasing a single 1tb hdd to replace the raid set anyway and adding additional drives to again make a 4tb raid set.

---

### Post by tracemyers on 2008-06-23
I have reconnected the drives and booted back into xp, windows still sees the drive fine and I can access it except for one folder which showed as corrupted, then after reboot, is not there at all but the space it occupies is not listed as free space when looking at the drive properties.

---

