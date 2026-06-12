---
title: "Koffice 2 fails to install"
date: 2009-02-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by caryb on 2009-02-05
Before I rebuilt my laptop (pre alpha3) I had this problem & I put it down to over upgrading & all the idiosyncrasy's but now I have rebuilt my machine with alpha3 & have all the current updates I decided to look at koffice 3 & I'm still getting this...
Is anyone else having this problem?

The following NEW packages will be installed:
  koffice-data-kde4
0 upgraded, 1 newly installed, 0 to remove 
10 not fully installed or removed.
Need to get 0B/1370kB of archives.
After this operation, 4776kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 141043 files and directories currently installed.)
Unpacking koffice-data-kde4 (from .../koffice-data-kde4_1%3a1.9.98.5-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/koffice-data-kde4_1%3a1.9.98.5-0ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/oxygen/16x16/actions/object-order-back.png', which is also in package kde-icons-oxygen
Errors were encountered while processing:
 /var/cache/apt/archives/koffice-data-kde4_1%3a1.9.98.5-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@stinkpad:/usr/share/icons/oxygen/16x16/actions#

Cary

---

### Post by taavikko on 2009-02-06
I'm certain that issue will be fixed in a few days.
If you must have the upgrade you can always use the 
--force-overwrite to get it done.
In some cases it might break something, but I've had to do it few times and no breakage.

```
sudo dpkg --force-overwrite -i /var/cache/apt/archives/koffice-data-kde4_1%3a1.9.98.5-0ubuntu1_all.deb
```

---

### Post by caryb on 2009-02-06
I found where the bug was marked as fixed today, I've uninstalled koffice for a few days then I'll have a look.


Thanks Cary

---

### Post by Tom Mann on 2009-02-07
This installed first time for me :)

---

