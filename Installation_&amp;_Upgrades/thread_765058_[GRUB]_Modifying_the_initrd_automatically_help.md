---
title: "[GRUB] Modifying the initrd automatically help"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Serpreme on 2008-04-24
I'm trying to setup a system where a script gets run. It accesses a FTP server, pulls a script that in turns does whatever i want it to do. 
But since the initrd gets pulled each time from the menu.lst, it just overwrites my changes each bootup and restores the files.

What i want is to know if there is a way to modify my initrd, repackage it via  
> find ./ | cpio -o -H newc > ./initrd
Then replace the current session changed initrd with the one menu.lst pulls.

---

### Post by Serpreme on 2008-04-28
Bump de bump.

---

