---
title: "Update Manager failed"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Art H. on 2007-11-01
Running Update Manager under Feisty fails with the following message:

Preconfiguring packages ...
dpkg: syntax error: unknown user 'postfix' in stateoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

Updates have been fine up to now.  I can't find the stateoverride file and there isn't a user called postfix on the system.

This one's really stopped me.

Is there any way to rebuild the package manager?

---

### Post by Pumalite on 2007-11-01
Try:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
(it might not work, in which case we'll have to find out which package needs to be removed)

---

### Post by Art H. on 2007-11-02
Thank you.  I tried your suggestion but it still fails with the same message.

Art

---

### Post by Pumalite on 2007-11-02
Check /var/lib/dpkg/status and find the package that failed to install.

---

### Post by Art H. on 2007-11-05
I went through the status file and found only one entry that was different from all the others:

Package: openoffice.org-debian-menus
Status: install ok not-installed

However, I don't think this was the problem.

Thank you for directing me to that directory, though, because I found the statoverride file containing the offending entry:

root postdrop 02555 /usr/sbin/postqueue
hplip root 755 /var/run/hplip
postfix postdrop 02710 /var/spool/postfix/public
root postdrop 02555 /usr/sbin/postdrop

Does this help?
Art H.

---

### Post by Pumalite on 2007-11-05
If your apt-get is still not working, you can remove the package with this:

sudo dpkg --remove --force-remove-reinstreq <packagename>
Then reinstall if need be.

---

### Post by Art H. on 2007-11-08
Sorry I've been too busy to try your suggestions right away.  
I tried to remove postfix using your recommendation but was refused because of dependencies upon mailx.

What would happen if I just removed the postfix item from statoverride?

---

### Post by Pumalite on 2007-11-08
[http://en.wikipedia.org/wiki/Postfix_(software](http://en.wikipedia.org/wiki/Postfix_(software))
(I think you can reinstall it after removal)

---

