---
title: "XP Killed my Ubuntu!"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by Corgana on 2007-02-04
OK, so I thought I was clever and knew how to install two OSs at the same time, I formatted my HD, Installed Ubuntu, Partitioned off a section NTFS with a gparted live cd, installed windows on that partition, and now the computer boots right into windows!

All the tutorials I can find are how to install ubuntu on a system with windows on it, I can't find one for how to install windows on an ubuntu system.

I only wanted windows for games, and here I am, posting this in IE. it feels dirty.

I appreciate any help anyone can offer.

---

### Post by ajmorris on 2007-02-04
What you need to do is re-write GRUB to the MBR.

To do this go to you ubuntu live cd and make sure you linux partition is mounted with write privilages.

Then open a command line and type "sudo grub"

Then when in the grub command line type "root hd*"your hard disk number"*,*"your partition number"* I.E: mine is root hd0,0.

then type "setup grub" Reboot and grub should start. You should have windows and ubuntu to choose from but if not you must add the windows line manually to /boot/grub/menu.lst. If you need help doing this just ask. :)

---

### Post by Kateikyoushi on 2007-02-04
No need to worry, it happens.

Take a look at this thread how to be able to boot both of them. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by Corgana on 2007-02-04
Ah! thanks for the quick responses as usual guys. While I think Ubuntu has a few steps to go before it's ready for mainstream usage, it's support community is way better than anything Microsoft could put out.

Thanks again.:)

---

