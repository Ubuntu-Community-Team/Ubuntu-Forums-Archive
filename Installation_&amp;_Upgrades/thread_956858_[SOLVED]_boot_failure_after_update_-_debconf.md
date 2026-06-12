---
title: "[SOLVED] boot failure after update - debconf?"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by dreaminhere on 2008-10-23
I just installed updates for my computer.  There were a lot of them so I don't know what was updated.  It asked if I wanted to do something with debconf.  Something about keep the original or change to the package managers?  Anyways, I selected package managers and rebooted.  Now it sits with the little bar going across before finally failing to a prompt if initramfs.  I'm using a raid 0 system and 64 bit hardy 8.04 but the boot partition isn't in the raid.  I don't know if the change to debconf made my system unbootable or what happened.  What can I do to boot up my computer?  I've tried both kernels in the grub menu but neither works.  I can't figure out how to get to the boot partition nor do I know where debconf lives.

---

### Post by dreaminhere on 2008-10-23
If I enable debug it seems to fail with this message:

[103.914316] ata5.00 qc timeout (cmd 0x27)
failed to read native max address
failed to recover some devices

Any thoughts?

---

### Post by dreaminhere on 2008-10-23
I found other threads that got me started on the right track.  I ended up changing the sata type from ide to achi in the bios and it booted up and worked!  Must have been some update that broke that, because I didn't mess with the bios.  Oh well, works now.

---

