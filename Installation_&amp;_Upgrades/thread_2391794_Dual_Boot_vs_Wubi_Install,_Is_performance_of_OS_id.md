---
title: "Dual Boot vs Wubi Install, Is performance of OS identical after install?"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2018-05-13
Just curious and looking for a wee bit of background.  I'm aware Dual Boot sets ubuntu directly onto hard drive on a separate partition and Wubi installs ubuntu 'within' Windows.

I understand Wubi is safer, with less chance of losing data as compared to creating a second partition for ubuntu to reside in.

What I'm curious about; is performance identical between these two installations?

I'm not doing games, just web browsing, email, Diaspora.  I don't fear doing a standard Dual Boot as the machine is new and there is tons of space, 1TB hardrive and 16GB memory.  I'm leaning toward Wubi simply as it seems to a much easier install.

---

### Post by Autodave on 2018-05-13
wubi is no longer supported. Other than dual booting, your only other option would be a virtual machine. Unfortunately, I have no knowledge about what it involved in that.

---

### Post by Impavidus on 2018-05-13
Wubi hasn't been supported for a long time and doesn't work with modern UEFI systems, so using wubi now is basically out of the question. But to satisfy your curiosity: Wubi would install Ubuntu to a virtual partition, which is a file (root.disk) on your Windows partition. This file had a limit of 30 GB, so there was no way to make your Ubuntu partition bigger than 30 GB. In principle you could make a separate /home partition and keep just the root partition on root.disk, but that would eleminate the advantage of not having to partition. Wubi was somewhat easier in the sense that it was easier to remove and less likely you would lose or damage your Windows system, but at the same time there was higher risk that Windows damaged your Ubuntu system. Performance would be similar.

---

