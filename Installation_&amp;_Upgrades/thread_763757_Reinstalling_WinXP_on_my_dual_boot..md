---
title: "Reinstalling WinXP on my dual boot."
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by tengobotas on 2008-04-23
Hello

Will GRUB be overwritten if I reinstall WinXP on my dual boot machine? Are there any tricks to reinstalling WinXP with Ubuntu already on the computer?

My partitions are layed out as such

| WinXP | | Ext3 | | Swap | | NTFS |

Thanks in advance

---

### Post by Partyboi2 on 2008-04-23
You will need to restore grub after you have reinstalled windows. Here is some info on howto
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by kbless7 on 2008-04-23
So install windows and its boot loader will overwrite the MBR. Then once that is done run the livecd and reinstall grub. Finally once you boot into ubuntu, add Windows to the grub list and all is good.

---

### Post by tengobotas on 2008-04-23
Perfect answers and thanks for the quick responses. I had a feeling this is what id need to do but was unsure and didnt want to end up stuck with a broken boot loader.

Cheers!

---

