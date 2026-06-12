---
title: "Windows XP + Ubuntu problem"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by Sockerdrickan on 2008-03-20
Hello i made an ntfs partition and installed Windows XP on it. Now I cant access the GRUB menu. What do I do? I tried going in the administrative manager stuff in XP but I couldn't set the partitions to active.

---

### Post by sub2007 on 2008-03-20
Windows XP will have taken over your bootloader. This guide tells you how to restore Grub as your bootloader: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I would use the Super Grub Disk. I've used it before, it's very simple and it works very well (instructions on that page).

---

### Post by gambrjl on 2008-03-20
windows overwrote the MBR where grub was

here's an article on how to recover

[Recover](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

edit:. lol sub2007 beat me to it.. same article

---

### Post by Sockerdrickan on 2008-03-20
Thanks for helping a Windows noob, guys :)

---

