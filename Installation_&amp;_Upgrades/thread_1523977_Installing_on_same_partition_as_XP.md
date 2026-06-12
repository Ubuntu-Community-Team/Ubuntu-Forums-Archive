---
title: "Installing on same partition as XP"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by Synyster06Gates on 2010-07-04
I have an older desktop that I would like to install Ubuntu on as well, while still having XP to play my games on... How do I go about installing Ubuntu on the same hard drive as XP, as I don't have another partition to use. Specs for the system are

Compaq SR2039X
250gb hard drive
Windows XP Media center edition
2gb RAM
Nvidia 8500GT gfx
AMD Athlon 3700+ processor

---

### Post by darkod on 2010-07-04
You will have to defragment XP, then boot with the ubuntu cd in live mode and use Gparted to shrink the XP partition for as much as you want. They can't exist on the same partition.

After that boot XP few times to do its disk checks.

Then boot with the ubuntu cd and start the installer. You can use the Use Largest Available Free space or manual partitioning as you wish. That will install ubuntu into the unallocated space you left. Don't create any partitions for it from XP, windows can't create partitions for linux.

PS. Of course, back up XP before starting this, just in case anything goes wrong.

---

### Post by Synyster06Gates on 2010-07-04
> **darkod said:**
> You will have to defragment XP, then boot with the ubuntu cd in live mode and use Gparted to shrink the XP partition for as much as you want. They can't exist on the same partition.

After that boot XP few times to do its disk checks.

Then boot with the ubuntu cd and start the installer. You can use the Use Largest Available Free space or manual partitioning as you wish. That will install ubuntu into the unallocated space you left. Don't create any partitions for it from XP, windows can't create partitions for linux.

PS. Of course, back up XP before starting this, just in case anything goes wrong.

How do I shrink the partition for XP, I've never done anything like this before, haha

---

### Post by Rubi1200 on 2010-07-04
+1 to everything darkod just said.

You might also find the following links helpful:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by darkod on 2010-07-04
> **Synyster06Gates said:**
> How do I shrink the partition for XP, I've never done anything like this before, haha

From the top of my head, when you open Gparted, right-click the partition and select Resize. There will be smaller window to set the size you want to shrink at, and also graphical bar showing the partition and you can simply drag the right border to the left. The numbers should start changing as you drag. Once happy with the choice, accept it and then click the green button in Gparted. Nothing gets executed until you hit the green button.

---

### Post by Rubi1200 on 2010-07-04
This might help:

[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by Synyster06Gates on 2010-07-04
When I open Gparted and try and edit the size with the arrows, it doesn't move. I edit the numbers myself, and it won't change, it goes back to the original. What do I do here?

---

### Post by darkod on 2010-07-04
> **Synyster06Gates said:**
> When I open Gparted and try and edit the size with the arrows, it doesn't move. I edit the numbers myself, and it won't change, it goes back to the original. What do I do here?

Hmmm... not sure. It is usually rounding the numbers to cylinders, so if you are trying to move it for small values it might be putting them back.
Try with larger values, not with the arrows (or you will need to be doing loads of clicking). You need at least 15GB for ubuntu, and you have to have that much free unused space on the XP partition. It can't shrink if there is no unused space because it can't delete data for you. And you wouldn't want it to anyway. :)

---

### Post by Synyster06Gates on 2010-07-04
I've only used 79GB of the 250gb, so I have plenty of space. I was going to allocate 80gb for Ubuntu. Nothing will move the arrows at all, though.

It says:

Free space preceding (MiB): 7 (wtf?)
New size (MiB): 229687
Free space following (MiB): 0
Round to cylinders is checked

---

### Post by darkod on 2010-07-04
Strange. And you can't drag the right border to the left, right?

When looking in Gparted, sda1 doesn't have any warning mark like triangle next to it? Or keys symbol?

---

### Post by Synyster06Gates on 2010-07-04
Nope, nothing like that

---

