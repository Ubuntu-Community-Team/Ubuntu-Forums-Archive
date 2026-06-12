---
title: "After upgrading Windows 10 (2004) on Ubuntu dual boot, ext3 partitions mountable"
date: 2020-06-13
forum: Installation &amp; Upgrades
---

### Post by wb0gaz on 2020-06-13
I had my Windows/Ubuntu (dual boot) machine upgrade it's windows 10 (home) installation to the recently available "feature release 2004", and was then curious to find that Windows had mounted (given drive letters to) the machine's USB-attached drive's two ext3 partitions. I then found I could add a drive letter to my Ubuntu boot partition (on the main hard drive), which I had not been able to do before. These are writable mounts. I do not have WSL (Windows Subsystem for Linux) installed or any other specialized configuration along these lines, just a routine consumer configuration. Windows shows these filesystems as "ext2" (even though they were creaed as ext3), which I had not seen previously in this machine.

I've not been able find any reference to Microsoft adding ext2 (3? 4?) support to Windows 10 feature release 2004. The machine most certainly does not have ext2fsd installed at this point, so the support for ext2 does appear to be native part of this Windows installation. In light of my recent failure to get ext2fsd working on Windows 10 (64 bit), this was helpful, if unexpected, turn of events.

---

### Post by dragonfly41 on 2020-06-13
I have a dormant Windows 10 (I use Ubuntu from external SSD) but I did install RLinux (from RStudio site) into Windows to view ext partitions from within Windows. Rarely do I find a use for this.

---

### Post by robhill19652 on 2020-06-13
I always stick to the ext4 for linux because it's the newest. I keep a separate partition or drive for my docs, music, videos etc, but do not create it as "home". I format that one to ntfs. This way I can access from linux or windows, and reinstalling either operating system doesn't affect that ntfs drive.

---

