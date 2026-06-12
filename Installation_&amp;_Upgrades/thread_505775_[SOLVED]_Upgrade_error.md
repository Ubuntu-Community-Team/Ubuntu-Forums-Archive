---
title: "[SOLVED] Upgrade error"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by upthelum on 2007-07-20
I ran "apt-get upgrade" and got this error which was the only package that had any problem:

Setting up backuppc (2.1.2-2ubuntu5) ...
 * Starting backuppc... 2007-07-20 23:40:59 $Conf{SendmailPath} = '/usr/sbin/sendmail' is not a valid executable program
invoke-rc.d: initscript backuppc, action "start" failed.
dpkg: error processing backuppc (--configure):
 subprocess post-installation script returned error exit status 1

Then at the end of the process it displayed this message:

Errors were encountered while processing:
 backuppc
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anyone help, i have been trying to resolve this problem for a few days and apt-get upgrade was the latest suggestion i have found trawling the boards, trying to fix it.

---

### Post by upthelum on 2007-07-20
Hey guys any takers with this it's really gonna bug me and i'm not sure where to go with it now. Anyway thanks...

---

