---
title: "Installing dual-boot on Fakeraid 5"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by phazonmutant on 2010-05-30
Hey, I'm having trouble getting Ubuntu 10.4 installed on my system.  This is the first time installing linux on my desktop, but fairly experienced otherwise.  

I have a Intel X38 chipset mobo and a 3 hard drive raid 5 array running through the southbridge (ICH9R or something like that).

I have a Windows partition, some empty space, and a media partition and I need to put in an extended partition in the empty space then put in a Ext4 fs and swap space.  Gparted only shows the actual hard drives and after configuring partitions manually with the installer (which seems to recognize raid correctly) it stops with the error that it can't create the Ext4 file system in the partition.

So how do I create the partitions?  Is there any tutorial for using parted directly (the man page didn't help much) - if that'll work at all.

Thanks in advance for any help!

---

