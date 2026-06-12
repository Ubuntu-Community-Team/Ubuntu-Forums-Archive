---
title: "64 and 32 bit installs sharing a home partition?"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by dislocated on 2008-07-23
Perhaps this has been dealt with here already, but I didn't find it.

Can I take my laptop, and install (for example) the 32 bit and 64 bit versions of Ubuntu on separate partitions and have then share a single /home partition?

That would give me the choice of bit depth and still have just one copy of all my personal files.

---

### Post by dislocated on 2008-07-27
Having done some research, I'll answer this one myself. If anyone has any other tips, please feel free to add them.

It seems that certain partitions can easily be shared between distros. Namely /tmp and the swap partition.

/home can be shared as well, but you could run into conflicts with different distro's trying to modify the same config files for the same user name.

A solution would be to share the /home partition, but use different log-in names for each distro. name_hardy32, name_hardy64, name_suse, etc.

---

### Post by sdennie on 2008-07-27
Right, if you are sharing /home across distros you might run into problems but, I've gone from 64bit to 32bit Ubuntu with the same /home and I don't recall having any problems.

---

