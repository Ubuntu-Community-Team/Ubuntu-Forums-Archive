---
title: "Fresh Install"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by olddave on 2007-05-03
Hi all just wondering if this is agood set up for duel booting.
hda1 window o/s
hda2 programe files (windows)
hda6 fat 32 (multi media files)
hda7 linux (ubuntu 6.10)
There is a swap file in there as well i can not give the size of the drives as i am running a live disc of simply mepis and get this message when i try to run it,(Unable to copy the user's Xauthorization file.)
Thanks in advance
Olddave

---

### Post by KIAaze on 2007-05-03
You could also format the multimedia partition as ext3 and use the ext2ifs driver for windows to access it. (but then Linux partition also accessible from windows :/ )
Or as ntfs and use the ntfs3g driver on Linux. (but not sure about its reliability for writing)

---

### Post by olddave on 2007-05-03
I am having to do a fresh install because of the NTFS-3G driver so i do not want to go down that road again. But Thanks for the advice.
olddave

---

