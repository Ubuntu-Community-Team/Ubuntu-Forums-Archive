---
title: "Moving the swap, /tmp and /var  back to main drive"
date: 2017-01-24
forum: Installation &amp; Upgrades
---

### Post by user_of_gnomes on 2017-01-24
I installed Ubuntu 16.10 on an SSD (sda) drive and moved the /var, /tmp and swap to a hard drive (sdd) but would like for them to reside on the SSD (sda) again.

I am unsure how to get started, previous attempts at moving these partitions have failed and I ended up having to reinstall Ubuntu. I'd like to prevent that this time around and learn something in the process.

Will simply removing the mount points from fstab cause Ubuntu to automatically mount these folders on the SSD (sda) again after restarting?

[ATTACH=CONFIG]273352[/ATTACH]
[ATTACH=CONFIG]273351[/ATTACH]

---

### Post by vanadium on 2017-01-24
/var and /tmp indeed will automatically reside on sda again. Swap is not a file, but a partition. If you want to move swap back to the ssd, you need to have a swap partition on that drive, and then fill out the UUID of that drive in fstab so that the system can pick than one up on the next boot.

---

### Post by igdfpm on 2017-01-24
To avoid a re-installation you should copy the contents of your existing /var, /tmp et al to your root partition (the folders should already be in place) using a live USB/CD which will preserve permissions ;)

```

# cp -rp /dev/sd_OLD_PART/{var,tmp}/* /dev/sda_ROOT_PART/{var,tmp}/*

```

Not copying the existing contents, and their permissions, of the moved folders would have been the cause of your previous issues.

---

### Post by user_of_gnomes on 2017-01-25
I successfully moved the swap partition but I am having trouble copying the contents of the /var and /tmp folder. It says that /dev/sdb5 and /dev/sdb6 are not folders when I execute the copy command.

Would mounting these partitions as folders first and then copying their contents achieve my goal?

---

### Post by Impavidus on 2017-01-25
/dev/whatever is not the thing you want to copy. Those contain the raw bytes as present on the hard drive, not the directories and files when these bytes are interpreted as a file system. So boot from a live disk, mount the old /var partition and the root partition of the installed system and copy the files:```
sudo rsync -aXS /mnt/oldvar/. /mnt/root/var/.
```assuming you mounted them at /mnt/oldvar and /mnt/root.

Then edit the fstab of your installed system and delete the line mounting /var. You can do the same for /tmp, but on most systems /tmp is wiped on every boot, so there may not be anything worth saving there.

---

### Post by user_of_gnomes on 2017-02-01
> **Impavidus said:**
> /dev/whatever is not the thing you want to copy. Those contain the raw bytes as present on the hard drive, not the directories and files when these bytes are interpreted as a file system. So boot from a live disk, mount the old /var partition and the root partition of the installed system and copy the files:```
sudo rsync -aXS /mnt/oldvar/. /mnt/root/var/.
```assuming you mounted them at /mnt/oldvar and /mnt/root.

Then edit the fstab of your installed system and delete the line mounting /var. You can do the same for /tmp, but on most systems /tmp is wiped on every boot, so there may not be anything worth saving there.

That did the trick, thank you very much!

---

