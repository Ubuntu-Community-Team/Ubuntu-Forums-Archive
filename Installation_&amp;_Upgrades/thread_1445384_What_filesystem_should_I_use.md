---
title: "What filesystem should I use?"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by olly600 on 2010-04-02
I currently dual boot one of my systems with Windows XP and fedora 12.

After having problems with fedora 12 where the wireless wouldn't work yet again when I upgraded, I just want to wipe it completely and replace it with Ubuntu. 


Currently my harddisk is divided into:

  Windows XP 32GB  (NFTS) /dev/sda1

  Grub 200MB (EXT4) /dev/sda2

  Fedora 32GB (RAW) /dev/sda5

  Data 42GB (NTFS) /dev/sda4

  (Recovery space 6GB Unusable)

After I have doing some reading I noticed that Ubuntu doesn't use the RAW filesystem format and EXT4 filesystem is new so as I manually need to format my disk for Ubuntu I have one question. As the other has been answered.

. Do I need reformat my GRUB partition as well. If, so what format should that be in?

Thanks.

---

### Post by srs5694 on 2010-04-02
First off, there is no "RAW" filesystem for Linux. Whatever you're using to identify those filesystems probably just means that it doesn't know what format is currently being used on that partition.

Second, for a /boot partition (what you probably mean by "Grub"), I recommend ext2fs. The reason is that ext2fs lacks a journal, whereas all the other common Linux filesystems have journals. A journal is normally a good thing because it reduces disk-check times after a power failure or crash, but on a very small partition (such as a 200MB /boot partition), this effect will be very small, but a journal will consume a lot of space relative to the partition's small size.

Third, my own recommendation is to split your current /dev/sda5 into two partitions, one for root (/) and one for /home. Make the root (/) partition 5-20GB, depending on how much software you intend to install, and give the rest of the space to /home. This will enable you to more easily do a complete re-install without damaging your user files, which can remain untouched in /home.

Fourth, it's hard to go very badly wrong with any of the common Linux journaling filesystems (ext3fs, ext4fs, ReiserFS, JFS, and XFS), at least for typical uses. My personal preference is to use ReiserFS for filesystems with normal-sized files (which would include / and possibly /home in the layout I've specified) and XFS for partitions that predominantly hold very large files (such as the recordings on a MythTV DVR). Most people here use ext3fs or ext4fs, though. Ext4fs is very new and there are still reports of occasional problems with it, so it would be last on my own personal list, although Ubuntu has already switched to ext4fs as the default filesystem.

---

### Post by olly600 on 2010-04-02
Thanks I'm happily logged in.

---

