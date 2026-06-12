---
title: "Partition Question"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Keldek on 2007-12-02
I'm currently following this guide: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) to set up my *fake*RAID 0 dual boot setup.

I'm in the process of configuring grub and I'm not sure how the partitions are being ordered.

Here's my partition layout:
```
/dev/mapper/nvidia_ciaejcff1      HPFS/NTFS
/dev/mapper/nvidia_ciaejcff2      Extended
/dev/mapper/nvidia_ciaejcff5      Linux
/dev/mapper/nvidia_ciaejcff6      Linux
/dev/mapper/nvidia_ciaejcff7      Linux
```

My question is, does *nix/grub read this as follows?
```

/dev/mapper/nvidia_ciaejcff1  ==  Partition 0
/dev/mapper/nvidia_ciaejcff2  ==  Partition 1
/dev/mapper/nvidia_ciaejcff5  ==  Partition 2
/dev/mapper/nvidia_ciaejcff6  ==  Partition 3
/dev/mapper/nvidia_ciaejcff7  ==  Partition 4

```

I'm assuming this is correct but when I try setting grubs groot & root (where applicable in menu.lst) to (hd0,2) (/dev/mapper/nvidia_ciaejcff5) I get an error saying the partition doesn't exist. So it got me thinking... would *nix/grub read my partitions as such?

```

/dev/mapper/nvidia_ciaejcff1  ==  Partition 0
/dev/mapper/nvidia_ciaejcff2  ==  Partition 1
/dev/mapper/nvidia_ciaejcff5  ==  Partition 4
/dev/mapper/nvidia_ciaejcff6  ==  Partition 5
/dev/mapper/nvidia_ciaejcff7  ==  Partition 6

```

---

### Post by Pumalite on 2007-12-02
Yes

---

