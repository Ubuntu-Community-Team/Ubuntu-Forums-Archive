---
title: "Gusty update-notifier update problem"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by windstory on 2007-08-16
I am new in Ubuntu. My laptop is installed with Gusty tribe 3 via USB disk (had dvd drive problem at installation time). It has been updated for several times following the notification of update-notifier.

This morning when it prompt me to update, I clicked yes. update-notifier is also on the list of update. But in updating update-notifier, error info. displayed:

Unpacking update-notifier (from .../update-notifier_0.59.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/update-notifier_0.59.2_i386.deb (--unpack):
 trying to overwrite `/usr/share/update-notifier/notify-reboot-required', which is also in package update-notifier-common
Errors were encountered while processing:
 /var/cache/apt/archives/update-notifier_0.59.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried "sudo apt-get install -f", the same error. I tried removing ubuntu-desktop, update-notifier, update-notifier-common; then "sudo apt-get update"; then install them again. The same error. I guess it is not a serious problem (notify-reboot-requried just touches a file in /var), but caused dependency problems b/w update-notifier and update-notifier-common.

Any of you encountered this error?

Thanks.

---

### Post by Seisen on 2007-08-16
A fix has been applied according to this post 
[http://ubuntuforums.org/forumdisplay.php?f=238]("http://ubuntuforums.org/forumdisplay.php?f=238")

and for future reference until Gutsy is released post all your problem and questions here

[http://ubuntuforums.org/forumdisplay.php?f=238](http://ubuntuforums.org/forumdisplay.php?f=238)

---

### Post by windstory on 2007-08-16
Will do. Thanks!

---

### Post by erdalronahi on 2007-10-09
I have the same problem after the latest update. The link to the other thread is broken, so what was the solution?

---

