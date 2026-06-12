---
title: "mailman help"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by Milambar on 2006-10-16
Can anyone help me fix this issue, I'm trying to get mailman uninstalled.

> root@dan:~# apt-get -f remove mailman
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  mailman
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 78443 files and directories currently installed.)
Removing mailman ...
Traceback (most recent call last):
  File "/usr/lib/mailman/bin/mailmanctl", line 105, in ?
    from Mailman import mm_cfg
ImportError: No module named Mailman
invoke-rc.d: initscript mailman, action "stop" failed.
dpkg: error processing mailman (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/lib/mailman/bin/update", line 49, in ?
    from Mailman import mm_cfg
ImportError: No module named Mailman
/etc/init.d/mailman: line 35: /var/lib/mailman/bin/list_lists: No such file or directory
Site list for mailman (usually named mailman) missing
Please create it; until then, mailman will refuse to start
Errors were encountered while processing:
 mailman
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any assistance will be welcomed.

---

### Post by Milambar on 2006-10-16
Okay, it seems to be due to a corrupt .deb file. I managed to uninstall it eventually, and when I ran dpkg on the actual .deb file...

> dpkg: error processing ./mailman_2.1.5-9ubuntu4.1_i386.deb (--install):
corrupted filesystem tarfile - corrupted package archive

Any chance of getting the .deb file fixed in the repo's?

---

