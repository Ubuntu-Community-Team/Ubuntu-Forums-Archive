---
title: "[SOLVED] bazaar upgrade error"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by EarlGrey on 2007-08-30
Hello, please do you know what to do with this?  I have the bazaar repo, but the upgrade failed and now I can't even uninstall it to try to install it again. Please any suggestions? Thanks!

```

Nastavuji balík bzr (0.90-1) ...
error in control file: `Files' value not specified at /usr/sbin/install-docs line 804, </usr/share/doc-base/bzr> line 10.
dpkg: an error during proccessing bzr (--configure):
 subproces post-installation script returned error status 255
Errors occured during proccesing:
 bzr
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

(I translated some parts from Czech)

---

### Post by trick on 2007-08-30
I just got the same problem. It comes from people using the bzr packages from [http://bazaar-vcs.org/releases/debs/feisty](http://bazaar-vcs.org/releases/debs/feisty)

One solution is to stop using that repository, then just remove bzr and reinstall it and you'll end up with version 0.15.

Another solution (what I did) is to add the line

```
Files: /usr/share/doc/bzr/html/*.html
```

to end of /usr/share/doc-base/bzr. Then run

```
sudo apt-get upgrade
```

and it should finish installing bzr for you. It seems to be working for me, YMMV.

---

### Post by EarlGrey on 2007-08-31
Thanks alot for reply! 

Today, before I even tryed your solution,  they posted a patch, so after todays upgrade, all works fine.

Cheers, Martin

---

