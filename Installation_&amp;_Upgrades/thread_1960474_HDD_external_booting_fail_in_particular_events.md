---
title: "HDD external booting fail in particular events"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by vittynoz@yahoo.es on 2012-04-17
Hi I install Ubuntu 11.1 in my external HDD and save the bootloader correctly. In my Dell inspiron it boots and work perfectly. But in my office, I have a desktop LenovoPC and a laptop HPEliteBook and the boot doesn't wok.
It appears:
no such device h0,0
grub rescue>

I don't know how to fix that. It's so strange that in my home it works and in the office's computers don't.
Can anyone help me?

---

### Post by oldfred on 2012-04-17
On your home computer are you directly booting from external or boot from internal drive's MBR and loading system from external?

May be best to run bootinfoscript from one or more of the systems.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

May be best to run script and post it before trying repairs.

Device hd0,0 sounds like grub legacy not grub2. But grub rescue is only part of grub2.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

