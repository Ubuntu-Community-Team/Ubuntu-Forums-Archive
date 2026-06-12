---
title: "Upgrading without space in root"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by silvano.jorge on 2010-05-03
Hi all!
I would like to upgrade my ubuntu to 10.04. My root partition has only 1GB free but I have plenty space in my home partition. The last time I upgraded I expanded my root partition for the upgrading, but I am not really happy with this solution. I would like to create a link from the directory where the installation files are downloaded to another place in my home partition.
I don't know where are downloaded.
It is sufficient with a symbolic link?
Must I mount a partition or a usb memory?

Thanks!!

---

### Post by coffeecat on 2010-05-03
A symbolic link will work fine. I've done just that for a different reason.

The downloaded .deb package files are stored in /var/cache/apt/archives/ . What you need to do is to create a suitable folder for the archive cache in your home partition - ideally, this should be owned by root, so chown as necessary. In /var/cache/apt/archives/ you'll find a folder called 'partial' and a lockfile called 'lock'. These need to be copied (with sudo) to the cache folder in your home partition. You can copy the .deb files if you want, but as these are mostly old package files and unlikely to be used again, you might as well discard them. Now delete the /var/cache/apt/archives/ folder and contents.

Lastly, create a symlink called /var/cache/apt/archives/ linked to the folder in your home. Again, use sudo so that it is root owned. Now you should be OK to upgrade.

If you need help with the terminal commands to do all this, post back.

**Edit:** another thought. Depending on the size of your root partition, you might want to rethink the resize option. Despite all myths to the contrary, ext3 partitions can get seriously fragmented when more than about 90% full. I'm not sure how much ext4 suffers from this, but all filesystems can fragment. So - if your root partition is 10GB or more, it might be better to enlarge it anyway. You could still do the above as well if you want.

---

### Post by silvano.jorge on 2010-05-03
Thank you very much coffeecat, all works great!
Thank you also about the note on the free space. I am using just the 90% of the partition but I think I will remain the partitions without any change.

---

