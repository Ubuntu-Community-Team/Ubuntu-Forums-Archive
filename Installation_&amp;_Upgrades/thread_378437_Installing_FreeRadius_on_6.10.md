---
title: "Installing FreeRadius on 6.10"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by daveclayton on 2007-03-07
Found a bug with /etc/init.d/freeradius in Ubuntu Edgy 6.10. Occasionally this gets set without the install permissions, so chmod is necessary. Next, message similar to the following occurs when attempting any action (start/stop/remove/isntall/upgrade), even with --force:

/etc/init.d/freeradius: 15: source: not found
invoke-rc.d: initscript freeradius, action "reload" failed.
dpkg: error processing freeradius-mysql (--configure):
subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
freeradius-mysql
binks@binks-desktop:~$ sudo dpkg --configure -a
Setting up freeradius-mysql (1.1.3-1) ...
/etc/init.d/freeradius: 15: source: not found
invoke-rc.d: initscript freeradius, action "reload" failed.
dpkg: error processing freeradius-mysql (--configure):
subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
freeradius-mysql

Solution I found was to change the first line from #!/bin/sh to #!/bin/bash - it appears that sh/dash doesn't support the "source" command.

Feedback always appreciated.

---

