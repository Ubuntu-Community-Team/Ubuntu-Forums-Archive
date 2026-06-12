---
title: "Restore lost partition?"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by p10 on 2010-10-04
When trying to create a bootable USB the other day I accidentaly wiped my backup-harddrive containing all my important files. Using Photorec I was able to recover most of my files. However they are now in a random order, with filenames that give no information about the content. I am not looking forward to going through close to 20 000 files just to find out what file it is...

Is there a way to restore the files and partitions the way they were before I f*cked up? The disk in question is a 250GB usb-drive. It was formated as one large partition using NTFS filesystem. It now reads as a FAT32 LBA drive. No data har been writen to the disk after I accidentaly formated it.

When searching the harddrive with Testdisk, it only shows the FAT32 LBA partition.

---

### Post by Mark Phelps on 2010-10-04
Through painful personal experience, I have learned that the best utilities for recovering data from NTFS filesystems are MS Windows-based utilities.

And the best of them, in my experience, is GetDataBack for NTFS from Runtime Software.  You can download a free trial from them but you will need an MS Windows box on which to install it.  The free version will not do the actual recovery, but it will show you what it found and what your chances of full recovery will be.

Oh and BTW, it preserves previous filenames and directory structures.

But ... you have to purchase it to do the actual recovery.

It's your files ... and it's your money.

---

