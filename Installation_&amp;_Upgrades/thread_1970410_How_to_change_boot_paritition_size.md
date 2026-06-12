---
title: "How to change boot paritition size"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by DanDennison84 on 2012-05-01
Hi,

I have Ubuntu 11.10 installed on a 1 TB USB HD.  In gparted it looks like this:

/dev/sdb1 - ext2 - 235 MiB - /boot
/dev/sdb2 - unk - 5 GiB
/dev/sdb3 - extended 925 GiB
  __ /dev/sdb5 - ext4 - 28 GiB
     __ /dev/sdb6 - ext4 - 897 GiB - /home
unallocated - unallocated 1.16 MiB

How can I move some of the /dev/sdb6 space to /dev/sdb1?  I need a larger /boot section since update manager says I need more space (16% free).  /home has a lot of extra space.  If I simply resizes /dev/sdb6 it creates a new unallocated under /dev/sdb3.  I don't have an option for resizing /dev/sdb1 past 235 MiB.

Thanks,
Dan

---

### Post by darkod on 2012-05-01
If you are doing upgrades version after version, the system can leave many old kernels taking up space in /boot. Remove all older kernels and that should help a little. Usually 230MB is plenty for /boot.

Resizing is not that easy, you have to be able to make unallocated space NEXT to /boot, not at the end of the disk. So that would mean shrinking sda2 from the start (not from its end). That is the only way to make unallocated space for expanding sda1. It has to be next to it physically on the disk.

I would go with removing the kernels first. You can check how many you've got with:
ls /boot/grub

That should list all kernels from the /boot/grub folder, they should be there.

---

### Post by DanDennison84 on 2012-05-02
I've only installed 11.10, nothing else.  The only thing in /boot/grub is a bunch of *.mod files.  I did follow the recommendations for partitioning when I created my partitions so I thought as well that 250 would be plenty.  I am going to try running the updates 1 at a time to see if that helps.

---

### Post by mips on 2012-05-02
> **DanDennison84 said:**
> I've only installed 11.10, nothing else.  The only thing in **/boot/grub** is a bunch of *.mod files.

Look at the root of boot.

From a terminal post the output of **ls -l /boot** here.

---

### Post by DanDennison84 on 2012-05-02
Hi, sorry I didn't see your reply.  I basically went through and increased the size of my /boot to 1Gb.  I had to reinstall 11.10, but everything is working now as I had everything else on other partitions.  I close this as fixed.

---

