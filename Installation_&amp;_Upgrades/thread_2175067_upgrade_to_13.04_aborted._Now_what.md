---
title: "upgrade to 13.04 aborted. Now what?"
date: 2013-09-17
forum: Installation &amp; Upgrades
---

### Post by elj4176 on 2013-09-17
I waited until now to try the update to 13.04 so that hopefully all the bugs were worked out. After running: 'sudo do-release-upgrade' I get the error listed below in the terminal. Not sure how to proceed so that I have a usable system. Where/how do I report the bug? The terminal doesn't give any info on that.

Running mktexlsr /var/lib/texmf ... done.
Errors were encountered while processing:
 linux-image-extra-3.8.0-30-generic
 linux-image-generic
 linux-generic
 initramfs-tools
Error in function: 


A fatal error occurred 

Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade has aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by oldos2er on 2013-09-17
> **elj4176 said:**
> Where/how do I report the bug? The terminal doesn't give any info on that. 

```
ubuntu-bug
``` and [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by elj4176 on 2013-09-17
found it and reported. I need to reboot but I'm not confident that it will come back up and I can't have that.

---

### Post by oldos2er on 2013-09-17
Backup any data you can't afford to lose (hopefully you've done that already). A reboot is required for the upgrade to complete.

---

