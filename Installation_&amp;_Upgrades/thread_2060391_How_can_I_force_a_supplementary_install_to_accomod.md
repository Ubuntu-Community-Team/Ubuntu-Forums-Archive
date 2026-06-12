---
title: "How can I force a supplementary install to accomodate new hardware?"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by eehouse on 2012-09-20
I did a network install (from mini.iso) of 12.04 onto a thumb drive while that drive was attached to a desktop machine that had only an ethernet connection.  It succeeded.  I then used the thumb drive to boot a netbook that has both ethernet and wifi, and neither comes up, nor is there any network configuration widget available.  When I run the net installer on the netbook it asks which interface I want, and can query my password for WiFi, so I'm pretty sure it would have correctly configured the thumb drive install to support wireless.  What I want is to re-configure, or re-install, so ubuntu will pick up what it needs to run wireless on the netbook, but without spending the time to re-download everything or losing what I've already done.  Is that possible?

The obvious, 'sudo dpkg-reconfigure --all', didn't help.

Thanks,

--Eric

---

### Post by darkod on 2012-09-20
Did you go into Network Manager and try to create/add new connection?

---

