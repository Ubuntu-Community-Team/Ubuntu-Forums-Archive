---
title: "Ubuntu 18.04 Server LVM Initial Install Greyed Out"
date: 2019-01-13
forum: Installation &amp; Upgrades
---

### Post by hat4hatsforhats on 2019-01-13
Hello,

I am trying to install Ubuntu 18.04 Server.

When installing 16.04, or any other linux distro, you install /boot and /boot/EFI separately as ext4 and below in filesystem generations.

Afterwards, you are supposed to initialize the volume groups and proceed from there.

However, Ubuntu 18.04's installer will not let me select the LVM option after I have already created a partition (e.g. boot).

I can only select the LVM option as long as I haven't done anything with the disk. And when I do select the LVM setup option, I can only choose the entire disk that I'm using, not a fraction.

Thank you.

---

### Post by hat4hatsforhats on 2019-01-13
Alright, because Google didn't show this and I couldn't find this directly from Ubuntu:

Create the lvm partition you need as unformatted. Then go through with LVM.

---

