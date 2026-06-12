---
title: "Restoring ubuntu from back up tar, without breaking the install."
date: 2019-08-26
forum: Installation &amp; Upgrades
---

### Post by re-42 on 2019-08-26
I wanted to erase ubuntu and reinstall it on a partition with more space. I followed [https://ubuntuforums.org/showthread.php?t=35087](https://ubuntuforums.org/showthread.php?t=35087) to create a back up. I have the back up tar and a working ubuntu, however if I unpack the tar onto root, it breaks many system settings, including grub in `/boot/..`

Is there a way for me to unpack to only non-system critical paths.

---

### Post by yancek on 2019-08-26
Did you notice the tutorial you linked to was written 14 years ago?  Did you use the instructions in the 2nd link near the top of the page on the Ubuntu Wiki?  There are a number of steps involved and without knowing exactly what you did it would be extremely difficult to suggest a solution.  As far as non-system critical paths, you can use the exclude option and only back up /home or your data partitions.  Not sure exactly what you want.

---

### Post by TheFu on 2019-08-26
You can extract specific files from tar. The tar manpage is fairly clear.
If you don't want files overwritten, use the --keep-old-files option. There are many other options.  Many are there to deal with sequential nature of a TAPE drive.

Tar is a terrible way to backup anything larger than about 250MB.  These forums are full of people asking about backups and getting help. Many will have scripts. Some will have GUI programs. 

Often increasing the size of a partition can be difficult and having a backup would be the best idea, but regardless, you'll probably need to manually fix the /etc/fstab file for UUID changes.  Every if you use ddrescue or fsarchiver to make partition images, the UUIDs will almost certainly change.  Fixing the fstab would be the minimal requirement.  Image-based tools are good for moving from disk A to disk B in 1 day, but not so great for long term backups that run daily or weekly.  Images waste too much storage that doesn't  need to be wasted.  A fresh Ubuntu install will solve all sorts of migration issues and usually saves about 4G from every backup.  It also decouples the underlying storage from the rest of the restore process and probably decouples many normal hardware parts too.

---

