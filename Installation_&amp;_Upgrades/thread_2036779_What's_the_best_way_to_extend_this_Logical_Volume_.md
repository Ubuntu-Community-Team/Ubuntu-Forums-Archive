---
title: "What's the best way to extend this Logical Volume? LVM"
date: 2012-08-02
forum: Installation &amp; Upgrades
---

### Post by El Potro on 2012-08-02
Hello people,

I need an advice here from experienced users.

The layout of this 2 TB disk (GPT) would be

```

sda1 1    MiB Bios_boot
sda2 1024 GB LVM --- vg1 1024 GB --- lv1 24   GB ext4
                                     lv2 1000 GB ext4
     800  GB unallocated
sda3 200  GB ext4

```

Now let's say I want to extend **lv1** to 1536 GB. What is the best alternative to use?

1. Resize (extend) the sda2 partition with parted or gdisk, to be 1536 GB.
2. Create a new partition in the unallocated space, 512 GB big, and add it to **vg1**.

The objective is to extend **lv2** to take up the extra 512 GB.

Thank you for your help in advance

---

