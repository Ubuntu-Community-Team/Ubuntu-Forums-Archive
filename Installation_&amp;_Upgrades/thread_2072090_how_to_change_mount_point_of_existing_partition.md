---
title: "how to change mount point of existing partition?"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by edjski on 2012-10-17
I recently installed 12.10. I have a separate home partition. When I installed 12.10, I chose to have the installer replace the old installation (because I knew my files were safe on my home partition) but it didn't occur to me that the new installation wouldn't recognize my existing home partition as /home.
So, now  that 12.10 is installed, how do I change the mount point of the partition so it mounts as /home?

Thanks,
ed

---

### Post by darkod on 2012-10-17
First check the UUID of the partition with:
sudo blkid

Note the string down (and the filesystem too).

Then open /etc/fstab for editing and add a line like:
```
UUID=<string> /home <filesystem, like ext4> defaults 0 1
```

But does the user match so that it can pick up the /home partition since you didn't specify it during installation?

For existing /home you always use the manual partitioning and tell it which partition to use as what. Remember, linux doesn't assume anything for you. It only does what you tell it to. :)

---

### Post by Lars Noodén on 2012-10-17
It is highly recommended to make a copy of /etc/fstab and keep it for later before you start editing.  That way if things go wrong, it is easy to restore.

---

