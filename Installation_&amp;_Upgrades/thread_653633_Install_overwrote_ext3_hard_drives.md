---
title: "Install overwrote ext3 hard drives"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Lord C on 2007-12-30
I just re-installed Ubuntu, using the Manual partiton option.

I chose a partition name for my 2 NTFS drives and my 2 EX3 SATA drives. I chose one of my SATA drives to be /home (as it was before).

After installing Ubuntu on the IDE drive (I chose to format that one), I see all the drives okay, the NTFS drives still have all the data, but the SATAs aren't.

One SATA drive is completely blank, except for lost+found, and the drive I set to /home only contains all the default home files (Examples, Documents etc.) It is as though Ubuntu install formatted the two ext3 drives, even though I didn't tick the box to format them?

I have done a lot of searching and it seems that recovering formatted drives is not an easy or painless task. These are both 500gb hard drives, so as you can imagine I have lost a lot  of data.

If this is a mistake, and the drives are not formatted, simply being read wrong or something fixable - then that's great.

If they are indeed formatted, and I'm royally f#cked, could anyone point me in the right direction to recover all my .mp3 files!
If I could recover my text documents and .mp3s I would be happy.

---

### Post by Pumalite on 2007-12-30
Get Gparted Live CD:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn image to disk, boot from it and take a look.

---

