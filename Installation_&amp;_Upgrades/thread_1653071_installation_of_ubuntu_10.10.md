---
title: "installation of ubuntu 10.10"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by hamed140m on 2010-12-26
hi
I want to install ubuntu 10.10 alongside win7 and during the installation my partitions do not recognized and sum of my hard is shown and already i made a 45G free space for ubuntu installation and i can not see this free space to create a new partition.
thanks for any reply.

---

### Post by Quackers on 2010-12-26
Welcome to UF.
Please boot into Windows and post a screenshot of your disk management screen (Start > right-click Computer > select Manage > disk management)

---

### Post by hamed140m on 2010-12-27
thanks. this is my disk management screenshot.

---

### Post by Quackers on 2010-12-27
Hi, thanks for the screenshot.
Your setup is unusual for a modern Win 7 system in that you have 1 primary partition and 1 extended partition with 4 logical drives within that extended partition, which takes up the rest of the disc. Did you set it up that way?
I suspect that the installer cannot see any free space because that free space is within the extended partition. As a result of this I think the installer just sees a full disc.
Waiting for a second opinion would be a wise move, but I suspect that you will need to move D:, E:, F: and G: as far to the left of the extended partition as you can. Then reduce the size of the extended partition so that it just includes those logical drives. This will leave free space at the end of the disc which I believe the installer will see.
If this is the route you take, you should backup any important data first.

---

### Post by Quackers on 2010-12-27
I've been thinking :-)
If you run the installer again and select "specify manually" in the partitioning stage you may be able to install Ubuntu into the free space within the extended partition by clicking on it and selecting "add" and then creating new root and swap partitions there.
I haven't tried it that way, but it may work.

---

### Post by oldfred on 2010-12-27
+1 on Quackers suggestions. 

Ubuntu will only install in Linux partitions as NTFS does not support ownership & permissions.

I thought the installer would offer to shrink one NTFS partition and then create its partitions.

You need to create partitions with gparted or as part of the install using manual install.

---

