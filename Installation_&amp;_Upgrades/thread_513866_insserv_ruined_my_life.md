---
title: "insserv ruined my life"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by jdeisenberg on 2007-07-31
I  wrote a script for startup, put it into /etc/init.d, and ran insserv.  OMG. All the numbering of the Snn files in rc2.d through rc5.d is screwed up, and I have a *raft* of error messages. Is there any way to get back to the way things were without doing a complete re-install?

---

### Post by PaulFr on 2007-07-31
If you have ever run **update-bootsystem-insserv**, you should have a backup in **/var/lib/insserv/bootscripts-*.tar.gz**. Otherwise, you can manually (or through a script of your own) rename the symbolic links appropriately. I've attached my list as a starting point - good luck !

---

### Post by jdeisenberg on 2007-07-31
Thank you. That was the conclusion I reached also; I have a laptop with pretty much the same installation as the desktop machine, so I can write a Perl script to reconstruct the symlinks given the list you gave me (or a similar one that I produce).

Another method, much harder: use dpkg-deb --control to extract the control scripts from all the relevant packages and look at the postinst script.

---

