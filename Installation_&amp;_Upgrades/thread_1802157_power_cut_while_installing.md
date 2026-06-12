---
title: "power cut while installing"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by johnonline on 2011-07-11
Updating to 11.04 -- there was a power cut now I can't boot. I downloaded 11.04 and ( part ?) installed from hard drive. Any ideas what I can do. (computer is an old ibm thinkpad )
Thank you

---

### Post by Herman on 2011-07-11
Where you updating or installing?

If you were upgrading (from one Ubuntu version to the next), chances are it will be faster and better to just delete the damaged operating system and install again fresh rather than face a possible gauntlet of unknown and unpredictable challenges a half-upgraded operating system might present.

If you have already made a backup of your files and settings then you're fine, just delete your partition(s) and re-install in the free space, reformatting the partitions as you do so.

If you have not made a backup, then you will either need to recover your files first or resign yourself to the fact that the files are lost and try to be happy anyway.
If you do need to recover your files, it could be just a matter of running a file system check by clicking on the partition in GParted, and either your file system will be repaired, or else you'll find all your files in lost+found, in which case they'll be renamed with inode numbers. Some files will be intact, others not and making sense out of some files will be like putting humpty dumpty back together again.

If you were completely re- installing with a newer version of Ubuntu, (as opposed to just 'upgrading'), the new operating system will be empty of personal files, so nothing needs to be recovered. Just start again and re-install over the top of the same partitions and be sure to reformat when you do. Otherwise you can delete the partitions first and create them again if you prefer, it won't make any difference.

---

