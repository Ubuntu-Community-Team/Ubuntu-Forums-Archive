---
title: "Re-installing Ubuntu: Partitions unrecognized..."
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by sbjaved on 2006-11-21
Here's my story:

My windows crashed after a power failure and i had to reinstall it. It totally nuked the grub loader so i tried to recover Ubuntu using LiveCD. But it starts giving weird messages...a bunch of numbers ending with a phrase 'Kernel panic', which i have no idea about. So with LiveCD not booting...i went into windows and formatted the root partition thinking of doing a clean install (was it stupid?)...now the LiveCD loads fine but it does NOT recognize any partitions when it loads gparted during installation process. 

The disk manager in LiveCD does show partitions but labels them "inaccessible"...And they are not mounted even after pressing 'enable'.

I've got a valuable data on the disk, so i can't format the whole disk...how do i get back ubuntu without losing windows and stuff?

Thanks...and sorry for the long post.

---

### Post by groggyboy on 2006-11-21
*wince*

i had a similar problem recently, with gParted and the Ubuntu LiveCD not recognizing the partitions on my hard drive even tho i knew they were there.

you may hate me for saying this, but the only way i got it fixed was by wiping my harddrive and reinstalling both operating systems.

interestingly enough, this happened to me after a windows reinstall as well.

you might consider installing an ext2 driver for windows and burning all your valuable data onto cds/dvds.  i never tried that option when i had this problem, so i can't guarantee they'll be able to read your linux partitions if gParted can't.  they are ext2 drivers, but can read ext3 just fine (sans journalling).  I use ext2IFS currently.  The links: [ext2Fsd]("http://sourceforge.net/projects/ext2fsd") & [ext2 IFS]("http://www.fs-driver.org/")

I'm guessing this problem has something to do with the windows installer making linux filesystems unreadable.  grr... dirty, underhanded microsoft!

hopefully someone else will have a better solution for you.

---

