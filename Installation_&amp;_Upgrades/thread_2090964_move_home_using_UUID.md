---
title: "move /home using UUID"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2012-12-04
Theres plenty of help on how to move /home, but they all involve moving /home to something line /home.old

I've got two software raids. 

array1, which is RAID5 and currently has /home
array2, which is RAID1 and currently has /home-new

Rather than renaming anything, I was thinking of using the UUID to mount the array.

The steps would be to 

1) boot into save mode
2) umount /home
3) umount /home-new
4) mount the RAID1 via UUID as /home and test
5) put changes in fstab (if everything works)

That way the RAID5 doesn't get touched at all.

Does anybody see a problem with this approach?

---

### Post by darkod on 2012-12-04
More or less, moving a /home partition always goes like that. /home-old or /home-new are only temporary mount point so that you can copy the files (you have to have a mount point to work with).
After that you simply edit /etc/fstab and replace the UUID of the old partition with the new one. So, yes, it should work.

Just make sure when you say /home-new you don't actually mean a folder called like that. When you open /dev/md2 it should immideately have the users folders inside, not first a folder called home-new.

PS. I'm not sure you can test mounting the new array at /home while the system is running. I have never tried to unmount /home when running. The test will be after you edit fstab and reboot. It will boot using the new device as /home and you will see whether it works or not. If it doesn't, you have to be ready to undo the fstab change from live session if it doesn't boot correctly after the change.

---

### Post by lister171254 on 2012-12-04
have already rsynced /home and /mnt/home-new

will let you know how I go

---

