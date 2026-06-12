---
title: "Windows 2000/Linux harmony"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by WMCoolmon on 2005-09-11
**The Hardware:**
One 250 GB SATA drive, already partitioned, with ~35 GB of data on it.

**The Goal:**
Install Windows 2000 on one partition, Ubuntu Linux on the other. Leave a couple partitions for LFS or other distros/OSes I try out.

Finally, the harder part: one integrated data drive, that I can use as my user's /home directory under Linux, and use the same data files for programs like firefox/tunderbird that work under both Linux and Windows.

**The Question:**
Is this at all possible to do?

---

### Post by lol on 2005-09-11
it is possible... to some extent.

You will need a FAT32 partition to share data between Linux and Windows, but DO NOT use it for your /home directory. /home should be on a ext2 (or ext3) partition.

So, in order to achieve what you want, the best thing to do is to use symlinks. For example:
Documents -> /media/windows/Documents and Settings/yourlogin/... (My Documents folder)
.opera -> /media/windows/... (the Opera settings folder on windows)
and so on...

Sharing the configuration files may not be possible for all applications though. I guess it possible with firefox/thunderbird, but I never tried. On the other hand, I know it's possible to do it with Opera, aMule or Azureus for example.

Don't forget, you can only write on FAT32 partition from Linux, so to achieve this, you will need to install Windows on a FAT32 partition as well!

---

### Post by trash on 2005-09-11
Just recently I did the same setup, partitions for win2000, linux and a fat32 to be storage/shared... works really nicely to. I didn't think of sharing program files but i did export firefox bookmarks from win2000 and import to linux firefox.

Off topic here but I am really stuck in 2000.. ever since installing it and doing the windows update I am getting virus alert popups every few minutes... how can this be on a fresh install that was updated immediately after the install? and how can I dissable the popups and has anybody else experienced this?

---

### Post by WMCoolmon on 2005-09-11
What about mounting the FAT32 partition at /mount/<user>, or symlinking it in a similar way?

---

### Post by chippy57 on 2005-09-12
[QUOTE=trash]Off topic here but I am really stuck in 2000.. ever since installing it and doing the windows update I am getting virus alert popups every few minutes... how can this be on a fresh install that was updated immediately after the install? and how can I dissable the popups and has anybody else experienced this?[/QUOTE]
Are you using IE6 or firefox 1.06? If you are using IE6 i suggest you dump it and use Firefox instead.

chip

---

