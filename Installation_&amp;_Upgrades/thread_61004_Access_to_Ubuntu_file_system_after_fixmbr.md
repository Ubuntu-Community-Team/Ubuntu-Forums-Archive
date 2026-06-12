---
title: "Access to Ubuntu file system after fixmbr"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by gordonbp on 2005-08-30
Dual-booting XP and Ubuntu - I had some problems with the BIOS recognising the boot device (and as I am not the only user it needs to be a "seamless" boot-up) and had to use fixmbr to cure them. Now, of course, I can't access my Ubuntu installation at boot up (which I knew would happen). Is there a way to do this (from a floppy for example) or do I need to re-install?

Thanks

---

### Post by heimo on 2005-08-30
Did you have grub (default Ubuntu bootmanager) installed and working? In that case, reinstall it and after it works - add your Windows to grub configuration (if not already done) and make it default (if that's what you mean with "seamless").
[http://www.ubuntuforums.org/showthread.php?t=24113]("http://www.ubuntuforums.org/showthread.php?t=24113")
(see posts #1 AND #2)

---

