---
title: "NTFS-&gt;ext3 conversion"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by fa2k on 2005-10-29
Hi, I just "discovered" VMWare, and thus i can now switch my main computer to Linux and have windows in a vm:) I have some hard drives that are formatted in NTFS. Can I do an "in place"-conversion to ext3, or to FAT and then ext3, with some tool in Ubuntu? Some files are about 8GB, so I guess FAT will have some problems. I have little free space, and I hate DVDR's so I'd like to just replace the FS structures and not copy the data. ext2 and reiserfs are also acceptable, of course, but FAT is not very efficient with large volumes, so that is not good for other than a temporary solution. If there is write access for NTFS, please tell me, then no conversion is necessary :)

---

### Post by GTvulse on 2005-10-29
No such thing as in-place conversion from one filesystem to another; moving from EXT2 to EXT3 and back is a very special exception. You will have to back up your data first, which in always a bight idea, anyway. ;-) Of course, you can juggle data among partitions with the help of rsync, if you have the space...

---

