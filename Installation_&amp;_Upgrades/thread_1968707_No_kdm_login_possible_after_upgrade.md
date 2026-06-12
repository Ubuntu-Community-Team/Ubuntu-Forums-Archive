---
title: "No kdm login possible after upgrade"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by QNo on 2012-04-29
Hi,

After upgrading kubuntu from 11.10 to 12.04, i cannot login by kdm, which has been possible before. I still can login into console. I purged and installed kdm, no result. Any further hints?

TIA
Chris

---

### Post by snfuchs on 2012-04-29
Hi,

the root partition on your harddisk might be full. Please check with df. You may recover some space with sudo apt-get clean.

Hope this helps,

Stefan

---

### Post by QNo on 2012-04-29
> **snfuchs said:**
> Hi,

the root partition on your harddisk might be full. Please check with df. 

I never had given any thought to disk space :-)

But:



root@station:~# df -h
Dateisystem    Größe Benutzt Verf. Verw% Eingehängt auf
/dev/md1        1,8T    918G  807G   54% /
udev            7,8G    4,0K  7,8G    1% /dev
tmpfs           3,2G    1,3M  3,2G    1% /run
none            5,0M       0  5,0M    0% /run/lock
none            7,9G       0  7,9G    0% /run/shm
/dev/md0         23G    556M   22G    3% /boot

---

