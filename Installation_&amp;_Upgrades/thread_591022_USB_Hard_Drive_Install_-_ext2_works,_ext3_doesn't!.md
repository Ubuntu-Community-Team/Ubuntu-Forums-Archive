---
title: "USB Hard Drive Install - ext2 works, ext3 doesn't!"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Hero_boy on 2007-10-25
I have a 160GB SATA USB Hard Drive. I have run the Ubuntu 7.10 installation (graphical boot CD & alternate CD) creating default ext3 partitions. However after installation, the Ubuntu loading screen appears but it hangs and does not load. If I switch consols (ctrl+alt+fX) I can see the error message:

**Alert! /dev/hda1 does not exist. Dropping to shell!**

I have a SATA USB Hard Drive so I believe it should be something like **/dev/sdaX**. Anyway I then tried the alternate CD again but this time I selected **ext2** as the file system. The OS now boots perfectly!

Why does this happen? Why can't I use the ext3 file system? When I am attempting the installs I have physically removed my internal laptop hard drive to ensure the boot loader is being installed to the right place.

Also is this the best way to create a portable copy of Ubuntu 7.10, or am I better off doing something like the installation here to make it more portable?: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Thanks!

---

