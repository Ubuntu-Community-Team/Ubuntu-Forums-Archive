---
title: "Update Manager Missed New Version of Firefox, What Else?"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by arcticool on 2008-11-17
Having some trouble getting upgraded past 7.10, in the mean time I've installed all of the updates found in the update manager except 8.04. I noticed that Firefox has had a few updates since the version installed with 7.10 (2,0,0,17)so it begs the question, what other updates do I need that update manager has not found? Can anyone speak to the general reliability of update manager or are there other methods regular Ubuntu users employ to keep their systems up to date and secure?
Thanks,

Jack

---

### Post by Pumalite on 2008-11-17
One thing is to keep your OS updated. Another is to upgrade from one system to the next. This is the official method of upgrading:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by arcticool on 2008-11-17
> **Pumalite said:**
> One thing is to keep your OS updated. Another is to upgrade from one system to the next. This is the official method of upgrading:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Yep, this is what I tried. 
Update Manager all updates applied until the next Check showed 8.04. I clicked upgrade, it installed, machine rebooted to new desktop all looked good until I logged in with my user/pw and it just hung there forever, right after showing the solid orange screen but before the desktop background image or taskbars or anything appeared. Is there some way to see what exactly it is hanging on? An event log of some kind. As there were no errors during the upgrade process itself it seemed that it went OK. I'm happy to do some legwork on my end if you can help point me in the right direction. 
Thanks,

Jack

---

### Post by Pumalite on 2008-11-17
Edit /boot/grub/menu.lst and remove 'quiet splash' from the boot line so you can see the boot process.

---

### Post by arcticool on 2008-11-19
> **Pumalite said:**
> Edit /boot/grub/menu.lst and remove 'quiet splash' from the boot line so you can see the boot process.

OK, done. The messages flew by at boot time but after a few reboots I could see two red 'fail' items, the first 'checking file system', and the second 'vm.mmap_min_addr is an unknown key'.

---

