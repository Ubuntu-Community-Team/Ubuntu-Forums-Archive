---
title: "Samba install fails"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Seadap on 2007-03-02
Hello all,

I've been having trouble getting samba to install.  sudo apt-get install samba returns:

* Starting Samba daemons...
invoke-rc.d: initscript samba, action "start" failed.
dpkg: erro processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned and error code (1)

Where can I begin sorting this out?

*edit*
Should have mentioned I'm running Edgy fully updated too.

*edit*
Thought this might be useful information from the samba.log
[2007/03/02 16:00:29, 0] smbd/server.c:main(829)
  ERROR: failed to setup guest info.
[2007/03/02 16:08:57, 1] auth/auth_util.c:make_server_info_sam(876)
  User smbguest in passdb, but getpwnam() fails!

---

### Post by ffxr on 2007-03-02
has samba ever been installed on this machine before?

---

### Post by Seadap on 2007-03-03
Never successfully.  At least not that I can recall.

---

### Post by krokodil on 2007-03-10
Having similar problems over here:

[http://www.ubuntuforums.org/showthread.php?t=374254](http://www.ubuntuforums.org/showthread.php?t=374254)

---

### Post by mbert on 2007-03-14
I ran into the same problem after trying to use gsambad....I found the solution for me here:

[http://www.ubuntuforums.org/showthread.php?t=349133](http://www.ubuntuforums.org/showthread.php?t=349133)

---

