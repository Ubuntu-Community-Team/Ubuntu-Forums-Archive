---
title: "Kernel Panic when upgrading using install disc through packager"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by KevRus on 2005-10-15
I went in the packager, clicked Add/Edit discs, marked all upgrades, and hit apply.  Everything went fine until I restarted my computer and booted Ubuntu, I got this error:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

I hope this is solvable considering I can't get to any command prompt in Ubuntu....Maybe something I can edit in Grub? I think it has to do with the kernel...obviously.:rolleyes:  I'm still pretty newbish to Linux, so you'll have to bear with me.

If I have to completely re-install Breezy over Hoary and wipe the partition, that's fine with me, I haven't even had Hoary very long so I don't have any files important or even worth backing up:p 

Please help, thanks!

---

### Post by KevRus on 2005-10-15
Anything I can do?

---

### Post by filemanager on 2005-10-20
I have the same problem :(

---

### Post by leezer3 on 2005-10-20
Hiya,
From a spot of Googling, I suspect you are using SCSI/ SATA hard disks?
Edit the Linux menu entry in Grub and post what it says please.

A couple of posssible fixes are in these two threads:
[http://www.linuxquestions.org/questions/showthread.php?postid=1818403#post1818403](http://www.linuxquestions.org/questions/showthread.php?postid=1818403#post1818403)

[http://ubuntuforums.org/showthread.php?t=27709&page=2](http://ubuntuforums.org/showthread.php?t=27709&page=2)

Cheers

-Leezer-

---

