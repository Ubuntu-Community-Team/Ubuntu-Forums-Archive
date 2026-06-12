---
title: "I can`t format or create partition table when trying to install system"
date: 2022-02-25
forum: Installation &amp; Upgrades
---

### Post by gerchik10094 on 2022-02-25
I have 2 hard drives. On drive 1 i have [SIZE=1]Windows[/SIZE], on drive 2 i want to install Ubuntu Mate. Both drives work perfectly under Windows. But when i`m trying to install Ubuntu installer tells me that partition creation fails. When i`m using Gparted, it tells me that i don`t even have a partition table. Tried searching for bad sectors, under Windows everything is ok and under Ubuntu...
[IMG]https://i.imgur.com/e9rYuA9.png[/IMG]

---

### Post by MAFoElffen on 2022-02-25
What is that the output of?

Nevermind... From an Ubuntu LiveCD, use "Try", then... From a terminal, show the output of
```

sudo fdisk -l | grep -v 'snap\|loop'
sudo lsblk | grep -v 'snap'

```
Then got to Activities > Start to type in "Disks" > Select the Disks Icon. Press <Cntrl><S>. Select the "Start Test" button. Select "Short Test"... See how it does.

If Linux has a problem seeing that disk, go the BIOS Firmware Settings menu and check what the SATA mode is set at. Should be to AHCI.

---

### Post by ubfan1 on 2022-02-25
In gparted, did you first create a new partition table?  Then new partitions may be created. The disk might just be totally blank.

---

### Post by MAFoElffen on 2022-02-25
> **ubfan1 said:**
> In gparted, did you first create a new partition table?  Then new partitions may be created. The disk might just be totally blank.
I'm thinking the same. Especially if new. But he might have mentioned it was new, if it was... Wouldn't have he?

---

