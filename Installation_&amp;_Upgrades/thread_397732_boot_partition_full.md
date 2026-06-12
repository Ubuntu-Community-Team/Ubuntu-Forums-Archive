---
title: "/boot partition full"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by jacksonz123z on 2007-03-31
I upgraded from edgy to Fiesty.  Now I get a warning that my 94MB /boot partition is full.  I tried removing old kernel images etc from /boot but this made only a small difference.  Apt-get clean did not help.  Because the disc partition is 100% in use further upgrades are not possible.  Any help would be appreciated!:confused:

---

### Post by jacksonz123z on 2007-03-31
It was the "old old hidden file trick".  By showing all files I discovered the .Trash.root file.  Once I deleted the contents all was well!  However before I worked this out I resized /boot with Gparted.  BTW Gparted is fantastic.  I hope this helps somebody else.:lolflag:

---

