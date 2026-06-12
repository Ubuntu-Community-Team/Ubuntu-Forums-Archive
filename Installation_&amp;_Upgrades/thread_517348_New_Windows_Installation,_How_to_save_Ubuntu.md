---
title: "New Windows Installation, How to save Ubuntu"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by pigbig842001 on 2007-08-04
:popcorn: Hi,

I have a dual boot system. It has Windows XP and Ubuntu 7.04.

Windows is corrupted and I have been advised to do a new installation. But I have heard that Windows Installation wipes out the **MBR**. If so, I would lose Ubuntu, which I don't want to (Such is the affection towards Ubuntu :lolflag:).

Is there any way I can install windows without affecting Ubuntu??? :confused: 

Installing Ubuntu again would fail the very purpose of this thread.

---

### Post by phidia on 2007-08-04
As long as you re-install windows to the correct partition, and not the one the ubuntu install is on all that will happen is that windows will overwrite the mbr.
You can re-install grub to the mbr by using the alternate ubuntu cd or even from the CLI in the live cd.

Read [this]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+install") thread for a grub re-install how-to.

---

### Post by pigbig842001 on 2007-08-04
> **phidia said:**
> As long as you re-install windows to the correct partition, and not the one the ubuntu install is on all that will happen is that windows will overwrite the mbr.
You can re-install grub to the mbr by using the alternate ubuntu cd or even from the CLI in the live cd.

Read [this]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+install") thread for a grub re-install how-to.
thanx, I think it will do.

---

