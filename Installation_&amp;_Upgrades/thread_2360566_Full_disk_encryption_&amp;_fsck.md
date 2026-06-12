---
title: "Full disk encryption &amp; fsck"
date: 2017-05-05
forum: Installation &amp; Upgrades
---

### Post by voluntary on 2017-05-05
I recently did a fresh install (brand new ssd) of Ubuntu 17.04 and I opted for full disk encryption.  Twice in the last week or so I've noticed the system become a little unstable so I've either shut down or powered off only to have my following session fail to get to the login screen.  Instead, after inputting the full disk pass phrase, I'm dumped into a very limited, text-only command line that does not even allow me to shutdown.  I've only managed to salvage the situation by following rather dated instructions such as these - [https://ubuntuforums.org/showthread.php?t=708291&p=4524774#post4524774](https://ubuntuforums.org/showthread.php?t=708291&p=4524774#post4524774)

Why isn't a full disk encrypted system capable to doing a file system check automatically like what would be performed on a normal ext4 partition and then carry on booting and allow me to log in to the desktop?

---

### Post by TheFu on 2017-05-06
You can use tunefs (or the equiv for your file system) to force an fsck to occur more often.
For /, you can **sudo touch /forcefsck** and that will run an fsck next boot.

IME, the encrypted stuff is inside that container and behaves exactly like it should.  On my 16.04 laptop, that means the partition is encrypted, then inside that container is a PV, VG, and a few LVs (since LVM is used). Each behaves like I would expect. It is possible to boot from alternate media, decrypt the partition, then open the LVs and run whatever tools are desired.

I find the **lsblk** tool handy to see this layout.

---

