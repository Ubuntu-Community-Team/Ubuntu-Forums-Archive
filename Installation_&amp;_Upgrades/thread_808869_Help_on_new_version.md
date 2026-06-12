---
title: "Help on new version"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2008-05-26
Folks,
Not being a guru, I had ubuntu send me a disk for the 8.04 version. I already have the 7.10 version so all that I wanted to do was update to the new version. However, when I put in the new disk the only option was to install so that's what I opted for. It seems that was incorrect so now I have version 7.10 and version 8.04 installed. Is there any way of removing the new version and simply updating it over the older version?

My hardware is an ASUS laptop, Intel Premium M processor 735 (M6B00R) and I've also got Windows XP on it.

Please note that I am not a guru so don't know very much about command line stuff.

Any information will be gratefully received

Bob

---

### Post by iaculallad on 2008-05-26
> **bobmac said:**
> Folks,
Not being a guru, I had ubuntu send me a disk for the 8.04 version. I already have the 7.10 version so all that I wanted to do was update to the new version. However, when I put in the new disk the only option was to install so that's what I opted for. It seems that was incorrect so now I have version 7.10 and version 8.04 installed. Is there any way of removing the new version and simply updating it over the older version?

My hardware is an ASUS laptop, Intel Premium M processor 735 (M6B00R) and I've also got Windows XP on it.

Please note that I am not a guru so don't know very much about command line stuff.

Any information will be gratefully received

Bob

Assuming that you installed 8.04 on another partition (and it's 7.10 that's loading the GRUB menu), you could use your LiveCD to delete 8.04's installation/partition. Be sure to edit your /boot/grub/menu.lst and remove all entries that points to your 8.04 OS.
When upgrading 7.10, use the Alternate CD instead and not the Desktop CD.

---

### Post by bobmac on 2008-05-26
Many thanks for your very quick response. I'll do the delete and edit the menu.lst. However, can you tell me what an Alternate CD is and where I can get it?

Bob

---

### Post by iaculallad on 2008-05-26
> **bobmac said:**
> Many thanks for your very quick response. I'll do the delete and edit the menu.lst. However, can you tell me what an Alternate CD is and where I can get it?

Bob

You can download the Alternate CD from [here]("http://www.ubuntu.com/getubuntu/download"). Be sure to check the check box which says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

Alternate CD contains packages that can be compiled to upgrade an OS, say from 7.10 to 8.04. While Desktop CD ONLY copies itself to the HDD.

Check this for doing the [Alternate CD]("https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d") upgrade.

---

