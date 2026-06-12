---
title: "Inconsequential Hardy problem"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by jalirious on 2008-05-06
Installed Hardy to tri-boot with Xp & Gutsy, on my inspiron 630m. Despite the horror stories everything worked a treat...


- that is apart from on Gutsy I'm able to access the other partitions (either click on the top left icon, or through /media/sdx)

- No show on hardy. Not much of a problem (compiz spinning round, no lockups as yet), but it was handy before.

Is there a way to get it to recognise the other partitions?

Cheers, Ben.

---

### Post by jalirious on 2008-09-22
gksudo emacs /etc/fstab&
(put this line in at end, check urs is "sda1", if not modify)
/dev/sda1   /media/sda1   ntfs   user,fmask=0111,dmask=0000   0   0

'Done'

---

