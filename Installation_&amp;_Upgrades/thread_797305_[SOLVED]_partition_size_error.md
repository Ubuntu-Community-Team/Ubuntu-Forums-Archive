---
title: "[SOLVED] partition size error"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by scradock on 2008-05-17
Hi all! I just used a partimage backup of my Hardy install to set up another partition to upgrade to Intrepid. It all worked fine, except that the new partition (19GB) is listed as having the size of the original Hardy partition (10GB).

Even more weird, GParted sees the new partition as having its correct total size (19GB), but calculates the amount used from that and the incorrect free space size obtained by subtracting the true space used (3GB) from the 10GB false total. So now I have 3GB of files listed as occupying 13GB of a 19GB partition.....

Is there a way I can get the incorrect partition size re-set? Where would the incorrect number be stored?

tune2fs doesn't seem to address this, as far as I can see...

---

### Post by scradock on 2008-05-17
OK, since no-one has anything to offer, here's what I have found:

the confused state of the partition sizes is deep-rooted - df /dev/hda4 reports the incorrect size for the new partition, so that is presumably where Nautilus and Properties get their info from. df reports a smaller used size, but it's in the right ball-park (3.4GB rather than 3.9GB). Could be that df is not counting the "file-system" size, about 500MB. All three then have _incorrect_ TOTAL SIZE, _correct_ USED SIZE, and hence incorrect FREE SPACE values.

GParted, on the other hand, gets the correct total size, but then uses that and the incorrect FREE SPACE size to calculate the used size, and comes out with 13.8 GiB used.

The solution was to resize the partition with GParted, first down to 18.5 GiB and then back up to 19.5 GiB. After the first step GParted was reporting the correct total, used and free sizes, and so was df.

Is this a bug? If so, in which package? Partimage, GParted, nautilus, df???

---

