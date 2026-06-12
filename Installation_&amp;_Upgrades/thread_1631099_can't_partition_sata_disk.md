---
title: "can't partition sata disk"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by hvn on 2010-11-26
Hi,

I'm trying to install 10.10 on a sata disk. In terminal, dmesg recognizes the disk at /dev/sda. The installer recognizes it as well, but the partition area is blank and the option are greyed out. How can I go on?
BTW, on the disk currently Fedora 14 is (fresh) installed and working fine, but a software install script is written specifically for Ubuntu. That's why I need to change to Ubuntu and it's no hardware problem.

Thank you.

---

### Post by carl4926 on 2010-11-26
Post the output of

```
fdisk -l
```

---

### Post by hvn on 2010-11-26
> **carl4926 said:**
> Post the output of

```
fdisk -l
```

From terminal, this gives no (visible) output.

---

### Post by carl4926 on 2010-11-26
[http://www.youtube.com/watch?v=h191KrDK-I0](http://www.youtube.com/watch?v=h191KrDK-I0)

---

### Post by hvn on 2010-11-26
> **carl4926 said:**
> [http://www.youtube.com/watch?v=h191KrDK-I0](http://www.youtube.com/watch?v=h191KrDK-I0)
OK, forgot the su(do). Oops. Here's the output:

$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022194

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          64      512000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              64        9730    77637632   8e  Linux LVM
$

---

### Post by sikander3786 on 2010-11-26
There is a bit of problem regarding sda1 and the cylinder boundaries.

Apart from that, where do you plan to install Ubuntu now? Do you want to wipe your Fedora install and put Ubuntu instead? Or you intend to dual boot between Fedora and Ubuntu?

---

### Post by hvn on 2010-11-26
> **sikander3786 said:**
> There is a bit of problem regarding sda1 and the cylinder boundaries.

Apart from that, where do you plan to install Ubuntu now? Do you want to wipe your Fedora install and put Ubuntu instead? Or you intend to dual boot between Fedora and Ubuntu?

I noticed that boundary problem, but Fedora works.

My intention is to wipe the Fedora install and put Ubuntu instead.

---

### Post by sikander3786 on 2010-11-26
> **hvn said:**
> I noticed that boundary problem, but Fedora works.

My intention is to wipe the Fedora install and put Ubuntu instead.
During the installer's partitioning page, if you select "Use entire disk", does that seem to proceed with the installation?

---

### Post by hvn on 2010-11-26
> **sikander3786 said:**
> During the installer's partitioning page, if you select "Use entire disk", does that seem to proceed with the installation?

See attachment what I get to see. This is as far as I get.

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by sikander3786 on 2010-11-26
Seems to have some raid configuration left on the drive as sdb states LVM.

That can be removed but I don't remember how. Wait, some other mate might jump in for that and in the mean while I am searching for that info.

---

### Post by dino99 on 2010-11-26
set your bios to "ahci" or better on "compatible" if it exist

sudo dmraid -rE

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by hvn on 2010-11-26
> **dino99 said:**
> set your bios to "ahci" or better on "compatible" if it exist

sudo dmraid -rE

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

dmraid did the job. Installing now. Thank you for your help.

---

