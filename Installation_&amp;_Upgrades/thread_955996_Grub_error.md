---
title: "Grub error"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by motomandd on 2008-10-22
My windows system has failed miserably with a bad trojan, and ive lost everything, and i am way too sick of windows now, anyway, ive thought of trying ubuntu agin, and now i get to install, then it stops at grub-install , about 97% and it says grub error (cant remember error) , this is a fatal error.

this happens on ALL x86-64 varients of ubuntu and 32 doesnt work on my pc

can any1 help?

---

### Post by motomandd on 2008-10-22
quick update, its not called grub error, its running grub-install hd0,0 failed, this is a fatal error

sorry for any mix up

---

### Post by caljohnsmith on 2008-10-22
Sounds like you may have the same problem as here:

[http://ubuntuforums.org/showthread.php?t=893156](http://ubuntuforums.org/showthread.php?t=893156)

Let me know if that works for you. :)

---

### Post by Pumalite on 2008-10-22
Use TestDisk to check your drive:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Another thing would be to DBan it and then use Gparted Live CD and format it ext3
[http://www.dban.org/](http://www.dban.org/)
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it

---

### Post by motomandd on 2008-10-22
caljohnsmith ill try that, thanks, and purma lite i dot want to wipe out all of the disk, since ive got a partition that i have to keep, (got a 30 gig backup thats important)

---

### Post by motomandd on 2008-10-23
ok, trying ext2 doesnt work either, still get the same error, and i cant try the other one, ive got nothing installed onb the PC, im typing this by a live CD.... any other ideas?

---

