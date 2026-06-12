---
title: "upgrading 12.04 to 14.04. (no talloc stackframe at ... 4864, leaking memory)"
date: 2014-12-29
forum: Installation &amp; Upgrades
---

### Post by RikardSvenningsen on 2014-12-29
Error:
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

I got this problem when I tried to login with ftp user
I have SAMBA install, according to this treat:

[http://ubuntuforums.org/showthread.php?t=2214042](http://ubuntuforums.org/showthread.php?t=2214042)

it could bee necessary to remove this:
sudo apt-get remove libpam-smbpass

After doing that, it works fine again.

---

