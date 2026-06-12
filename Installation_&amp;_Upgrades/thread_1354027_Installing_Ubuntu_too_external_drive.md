---
title: "Installing Ubuntu too external drive"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by maeniel on 2009-12-13
I just bought a dell studio laptop, and I absolutely despise the windows operating system.
While I despise it, It's all anyone uses where I work, and some of the applications I use there are only available for windows.

What I want to do is install Ubuntu too the external drive and be able too run it from the external, but be able too run windows with the external unplugged.

The external drive is a 1TB usb MyBook.

 Can this be done? If so How?: Thank you in advanced to anyone who can help.

---

### Post by darkod on 2009-12-13
Yes, it can. It is up to you how you want it. You will have to have empty unallocated space on the ext hdd. Unallocated means not belonging to any partition, especially not NTFS/FAT32.
At the moment your ext hdd is probably all one single partition. You will have to shrink it making unallocated space or delete some partition if you have more of them.
In case you want ubuntu on the whole 1TB drive, it's even easier.
Once you have created the unallocated space, just boot with ubuntu cd, select Install Ubuntu and in step 4 select the ext hdd and the option the installer to use Largest Available Free space (or Whole Disk if that's what you want). Note how the ext hdd is named, probably, /dev/sdb or similar. In the last step, step 7, before clicking the Install button, click on Advanced button and make sure the bootloader is installed on /dev/sdb too (or what ever the disk is called). Note, /dev/sdb, not /dev/sdb1 with a number.
And that should be it.

---

