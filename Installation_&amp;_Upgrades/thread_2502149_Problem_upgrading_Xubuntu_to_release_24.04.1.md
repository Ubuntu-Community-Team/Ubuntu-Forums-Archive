---
title: "Problem upgrading Xubuntu to release 24.04.1"
date: 2024-11-03
forum: Installation &amp; Upgrades
---

### Post by alepron on 2024-11-03
Good day!

When upgrading Xubuntu 22.04.05 to release 24.04.01, I have the following problem:

root@comp:/home/user# do-release-upgrade

...

Cannot upgrade system with unmerged /usr

Please install the usrmerge package to fix this, and then try the
upgrade again.

...

but:

root@comp:/home/user# apt install usrmerge

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
usrmerge is already the newest version (25ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@comp:/home/user#/usr/lib/usrmerge/convert-usrmerge

Smartmatch is experimental at /usr/lib/usrmerge/convert-usrmerge line 172.
The system has been successfully converted.

but:

root@comp:/home/user# do-release-upgrade

...

Cannot upgrade system with unmerged /usr

Please install the usrmerge package to fix this, and then try the
upgrade again.

...

I understand that the people, creating the concept of usermerge, wanted the best. But it doesn't work normally! And how can I update to release 24.04.1 now?!

---

### Post by 1fallen on 2024-11-03
Now I don't know if this will work on your end but it did on mine, 
You should be able do perform the upgrade if you replace the /lib symlink with a relative one:
 ```
sudo ln -sfn usr/lib /lib
```
I filed a bug against it but no action was ever taken.
Good Luck

EDIT: Rubi1200 has an excellent spot on root, don't do that. See post below#3
"root@comp:/home/user#" not a good idea.

---

### Post by Rubi1200 on 2024-11-03
I don't have anything to add to what **1fallen2 **suggested.

However, I would caution against running as root in the shell.

You can achieve the same thing with sudo, but more safely.

---

