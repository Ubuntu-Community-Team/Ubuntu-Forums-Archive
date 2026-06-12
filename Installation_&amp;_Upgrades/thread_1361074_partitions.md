---
title: "partitions"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by Xog on 2009-12-21
i plan on installing 9.10 on my main rig. I have a 1.5TB hard drive split into 4 partitions. One of these partitions recently became useless because my mother finally moved out of my house (it was her partition).

Is there a way to install ubuntu on JUST that partition (400GB, plenty of space) without it affecting my other partitions?

---

### Post by bumanie on 2009-12-21
At the partitioning stage choose 'manual' and then direct ubuntu to install to the 400gb partition - you may have to make it into a logical partition so that you can make the /swap partition too. Hard drives cannot be partitioned into more than 4 primary partitions. By default, ubuntu will want to make a /swap partition also, hence the need for a logical partition, which is seen as one primary partition, but can be formatted in to many 'sub' partitions. Technically you can run ubuntu without a /swap, but it will send up an error message at boot about not having a /swap.

---

### Post by Xog on 2009-12-21
awesome, thanks

---

### Post by coffeecat on 2009-12-21
Are all 4 partitions primary partitions? As the last poster said, you need to create both a swap and a root (/) partition for Ubuntu. There's two ways to do what you want. Boot into the live CD and open Gparted (System > Administration). Use Gparted to delete the partition your mother was using. Then create an **extended** partition in the freed space. You can't create logical partitions directly. Instead you can create one (and one only) extended partition instead of a primary partition, and then create a number of logical partitions in the extended. The only purpose of an extended partition is to act as a "container" for a number of logicals.

But much easier would be to use Gparted to delete the unused partition, then close Gparted and start the installer. When you get to the partitioning page of the installer, choose the guided option "use continuous free space" (or words to that effect). The installer will then create the extended/logical partitions for you, including an optimally-sized swap.

---

### Post by phillw on 2009-12-21
contiguous ... yeah, not a common word ;-)

Phill.

---

