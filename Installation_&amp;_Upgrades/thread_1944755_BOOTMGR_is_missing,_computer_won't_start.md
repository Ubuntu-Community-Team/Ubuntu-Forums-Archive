---
title: "BOOTMGR is missing, computer won't start"
date: 2012-03-21
forum: Installation &amp; Upgrades
---

### Post by kamkam01 on 2012-03-21
Hey everyone! I was just trying to install Linux on a partitioned 1TB hard drive. However, when I installed and restarted I got the message BOOTMGR is missing, and I can't choose which partition to log onto. Is there a way that I can pull some files off of it or even change the default partition to boot off of? Thanks!

---

### Post by oldfred on 2012-03-22
Welcome to the forums.

Bootmgr is the Windows boot loader. Did you install the grub2 boot loader to the MBR of the drive? And did you overwrite the Windows install?

You may just need to reinstall grub to the MBR.

Best to see details, you can run boot info script from this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by kamkam01 on 2012-03-22
Thank you! I'm going to try this tonight, but it seems like this will solve my problem. Thanks again!

---

