---
title: "Dualboot doesn't work. Won't let you choose OS on startup."
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by oliverb4ss on 2007-05-13
My friend and I installed Ubuntu and XP on his PC.

First, we made a partition of 60 GB (of 117 GB in total) for Windows, formated it as NTFS and installed the OS.

Then we ran Feisty from the live CD and made a 40 GB (and 2GB swap partition) partition for Ubuntu in the installers partition manager and formated it as ext3. The OS install was successful.

Then we tested and the the dualboot went fine, and everything worked.

But my friend requested and extra partition for documents and it would have to be NTFS so that XP could read/see it.
As the Ubuntu partition manager didn't support formating to NTFS, I decided to do it with the XP setup CD.

After the remaining 15 GB was formated as NTFS, I rebooted and I could no more choose the OS, it would automatically boot to XP.

And I can only see the 60 GB and 15 GB NTFS partitions, so I'm assuming XP can't recognize ext3 drives.

Is there any way to repair the dualboot?
I think the extra docs drive made things too complicated.

Thanks.

---

### Post by bscbrit on 2007-05-13
The problem is that MS Windows refuses to believe that any other operating systems exist, and it always replaces the boot loader with its own and throws away what was in Grub.

This thread should help you to get your dual boot working again:

[http://ubuntuforums.org/showthread.php?t=440874&highlight=repair+grub](http://ubuntuforums.org/showthread.php?t=440874&highlight=repair+grub)

---

