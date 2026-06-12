---
title: "Messed-up partition"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by don_eros on 2010-06-20
Hi everyone,

I made a *HUGE* mistake while reorganizing the partitions on my HD.

I wanted to extend a NTFS partition to the left by about a hundred MB using GParted (I had formatted the Windows 7 partition and filled  it with data, but I had forgotten the partition Windows 7 puts at the beginning of the disk and wanted to remove it and use the space).

I assumed GParted would just expand the partition and leave a blank space at the beginning, but when I realized it was going to move *all the data* on the disk to the left I tried to stop it (since it was still performing the "read-only" test I thought it was safe).

I cunningly ignored the warning that said that major data corruption might occur if I stopped the process (I assumed it was just a warning for noobs, and since I'm obviously such a big expert I could safely ignore it).

Now Gparted says "$MFT has invalid magic. ntfs_mft_load(): Failed" and that I should run chkdsk /f on Windows, but Windows refuses to run chkdsk on the unit because it can't mount the partition.

Is there a way of fixing this? Where do I start?

Thanks,
DE

---

### Post by bumanie on 2010-06-20
> Now Gparted says "$MFT has invalid magic. ntfs_mft_load(): Failed" and that I should run chkdsk /f on Windows, but Windows refuses to run chkdsk on the unit because it can't mount the partition.Can you explain a bit more what you mean by this. Do you mean, that windows no longer boots? Do you have a windows installation disk or only a restore partition? A corrupted ntfs filesystem is best fixed from within windows. At worst, you may have to try and copy data off the ntfs partition from a live ubuntu cd, but some of the files may be corrupted due to the stopping gparted part way through its function.

---

### Post by ronnielsen1 on 2010-06-20
Been there and done that. You'll have to redo. Whatever files you can't get from a live cd, you could try photorec and testdisk available from hirens boot cd or puppy unlimited

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

[http://sourceforge.jp/projects/toplinux/downloads/43860/TOP-unlimited-4.2.1.iso/](http://sourceforge.jp/projects/toplinux/downloads/43860/TOP-unlimited-4.2.1.iso/)

---

### Post by darkod on 2010-06-20
I know it's too late now, but I'm still wondering, was the 100MB space really that important to you to do all this?

Besides, even if it worked, it would break windows booting because the 100MB partition has the win7 boot files on it. You would have to restore boot files after that, which not always works even with the win7 dvd.

I'm not sure what to try at this moment and not risk your data. You can try forcing chkdsk from ubuntu live mode. If your windows partition is /dev/sda2 now, try to run ntfsfix on it, and then restart and select windows to boot, it will sometimes continue with chkdsk.

sudo ntfsfix /dev/sda2

Plus, your current win7 grub entry is probably showing the loader files on /dev/sda1 still, and you already deleted that partition.

---

### Post by don_eros on 2010-06-20
Thanks for the feedback guys!

@bumanie: I moved my system to another disk, so I have a perfectly working installation of Ubuntu + Windows. I ran into trouble while moving around the partitions of the old system disk.

@darkod: it was definitely *not* worth it, but what can I do? I'm obsessive compulsive ;-)

@ronnielsen1: thanks, I'll try the packages you recommend after Italy's game!

---

### Post by don_eros on 2010-06-20
OK, final update: I was able to recover something using testdisk, the rest was lost (but I did have a backup of the really important stuff on that disk, so it wasn't a total disaster).

Thanks again to everyone for the help, I guess I won't do it again... :oops:

---

