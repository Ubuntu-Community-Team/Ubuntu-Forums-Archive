---
title: "Error exit status 102"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by sunspots on 2007-02-21
Hi
I was running the routine job to update Ubuntu and during the installation I received the error message 

Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

When I originally was updating through the Update Manager I got the 102 error and it suggested running Synaptic or "sudo apt-get install -f".

I then ran the apt-get command and received the above detailed error.

My system is
- Dell C400
- Ubuntu Dapper

Any suggestions on what the error is about and how to rectify?

Thanks for any suggestions

---

### Post by sunspots on 2007-02-21
When I did a search in the forum I found nothing, when I went through the search engine I found this link.

[http://ubuntuforums.org/showthread.php?t=240699](http://ubuntuforums.org/showthread.php?t=240699)

Hopefully this will help my problem. Will post an update.

---

### Post by sunspots on 2007-02-21
Yep. That did work.

---

