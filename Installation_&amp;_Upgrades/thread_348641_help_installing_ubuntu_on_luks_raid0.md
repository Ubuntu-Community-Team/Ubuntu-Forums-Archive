---
title: "help installing ubuntu on luks raid0"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by brandt on 2007-01-29
Hey,
I'm trying to install edgy with an encrypted filesystem on a software raid0.  I followed this Howto ([https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)) where applicable, but the system is unbootable.  The problem seems to be that the initramfs script that asks for the password runs before the raid array is assembled and activated.  I tried throwing in a "/sbin/mdadm --assemble --scan" into the script, but no luck.  I'm not too familiar with writing/modifying boot scripts so I'm not sure what to do.  Is there any way I can activate the arrays before the system attempts to unlock the encrypted root?
-brandt

---

