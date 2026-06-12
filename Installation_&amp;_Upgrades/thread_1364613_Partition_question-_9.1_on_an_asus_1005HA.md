---
title: "Partition question- 9.1 on an asus 1005HA"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by arnicainthemembrane on 2009-12-26
My question regards partitioning my hard drive so I can dual boot WinXP and Ubuntu. The computer's drive is presently partitioned sda1-4, and I'd like to use sda2 for Ubuntu. I understand that this drive now needs to be further partitioned into more segments: root, home, swap.

I proceeded through the installation until I got to the partitioning section, and I was told that in order to change partition size I have to write changes to disc. (see enclosed screenshot).

I stopped at this point because I'm told the operation is not reversible.

I have no idea what this means. Do I need to download gparted and use it to further partition sda2? any advice?

---

### Post by lidex on 2009-12-26
> **arnicainthemembrane said:**
> My question regards partitioning my hard drive so I can dual boot WinXP and Ubuntu. The computer's drive is presently partitioned sda1-4, and I'd like to use sda2 for Ubuntu. I understand that this drive now needs to be further partitioned into more segments: root, home, swap.

I proceeded through the installation until I got to the partitioning section, and I was told that in order to change partition size I have to write changes to disc. (see enclosed screenshot).

I stopped at this point because I'm told the operation is not reversible.

I have no idea what this means. Do I need to download gparted and use it to further partition sda2? any advice?
No. Just continue where you left off. All you've done so far is select the changes you want to make - the next step is the partitioner actually writing those changes to your hard drive. A normal part of the process.

---

