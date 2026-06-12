---
title: "Installed 9.10 64, now delete 9.10 32"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by JodiSte on 2010-01-19
I had previously installed 9.10 32 bit and yesterday installed on another partition 9.10 64 bit.

Now I have got it all working and want to delete the 32 bit version.
I had bad experiences previously with messing up the grub loader and re-assigning the freed-up space to the other partition.

Is there a guideline anywhere how to delete one partition, assign it to another and to re-write the grub loader?

Any help very much appreciated.

Cheers

---

### Post by darkod on 2010-01-19
As long as grub2 is concerned, it will make a difference whether you are using grub2 from the older 32bit install, or from the new 64bit install.
The grub2 config files are in the /boot/grub folder on the / partition. If you are using the grub2 from 32bit, deleting/formatting that partition will make it unusable, yes. Because its config files will be gone.
If you are using grub2 from the 64bit install, its config files are on the 64bit / partition so deleting the 32bit partition doesn't matter. After deleting it you will just do update-grub and the menu will be adjusted accordingly.
But for reallocating the space it can be more complicated. First of all, to expand the existing 64bit / partition (if that's what you want), the unallocated space has to be next to it. You will have to boot with ubuntu cd, Try Ubuntu option, because that way / is not mounted. Expand / with the new free space. After that you will have to expand the actual filesystem because linux works in different way to windows for example.
You can expand the partition but the ext4 filesystem will stay the same initial size.
There is a command to expand the filesystem to use all of the newly expanded partition but I can't remember it right now. :(

---

### Post by tommcd on 2010-01-19
A Parted Magic live CD will be able to resize or reformat your partitions very easily:
[http://partedmagic.com/](http://partedmagic.com/)
To grow the 64bit partition into the former 32bit partition the partitions will still need to be next to each other though.

---

