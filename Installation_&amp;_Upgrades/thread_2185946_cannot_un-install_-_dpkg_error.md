---
title: "cannot un-install - dpkg error"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by hako1 on 2013-11-05
13.04 32bit desktop Trying to remove usbb2k-api-mod, I get the following dpkg error:  "/etc/rc.d/" no such file or directory.   All subsequent attempts to install or update fail.   /var/lib/dpkg/status has "deinstall ok half-installed" for the package usbb2k-api-mod.    How to repair the system? I have read in some post that it would be enough to edit /var/lib/dpkg/status, deleting the complete entry for the problem package. Before I try that, can anyone confirm?

---

### Post by ian-weisser on 2013-11-05
Generally, if a missing file is the problem, I check that it's *really* missing, then I create a dummy file for the script to remove.
In this case, /etc/rc.d is not a directory on my system (though many similarly-named dirs do exist)

So a **sudo mkdir /etc/rc.d  **and a **sudo touch /etc/rc.d/whatever-the-filename-is** will allow the broken script to proceed with removal.
Remember to **sudo rmdir /etc/rc.d** after a successful uninstall.

Deleting the dpkg status entry for a problem package does work, but leaves software on your system (possibly still running!). It's an unclean way to remove the record of a package, and not preferred.

---

### Post by hako1 on 2013-11-05
Thank you very much. Creating a dummy worked for me, the removal went through, and installation/update is working again.  However, there are a couple of files with the name of the removed package left in /etc/rc6.d and var/lib/dpkg. Do I need to delete them by hand?

---

### Post by ian-weisser on 2013-11-05
> **hako1 said:**
> However, there are a couple of files with the name of the removed package left in /etc/rc6.d and var/lib/dpkg. Do I need to delete them by hand?

In rc6.d, yes. Go ahead and remove.
Where exactly in /var/lib/dpkg? Maybe not there.

---

### Post by hako1 on 2013-11-05
Leftover files:
  /etc/rc0.d...rc6.d: one link file "usbb2k-api-mod" in each rcX.d folder
  /etc/init.d/usbb2k-api-mod
  /var/lib/dpkg/info: usbb2k-api-mod.list and ~.postrm

  I deleted them all and restarted. No issues.
 Thanks again.
:D

---

