---
title: "Dell Dimension ignores MBR"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by xurizaemon on 2007-05-04
OK, I installed Feisty on a new machine, gave it all of my primary master drive and moved the XP disk (came with the machine, only an 80GB, might as well keep it for testing) to primary slave.

Boot options in the BIOS say "Drive C:" instead of "Primary Master". This will boot XP from the primary slave rather than going to GRUB. GRR!

If I F12 on reboot, then I can choose "Primary Master" rather than "Drive C:" - both appear as options. But I don't want to have to wait and play snap on reboot (or miss it and have to wait for XP to load so I can reboot, are you sure, yes goddamit, reboot now).

Anyone hit this issue with the DImensions? Is it a BIOS oddity? Is there a bootloader I can install in XP to send the system back to GRUB if it hits XP?

(GRUB boots XP as an option just fine out of the installation.)

Very impressed with Feisty.

---

### Post by xurizaemon on 2007-05-04
I can't find any alternatives for the boot order in the BIOS. It lets me rearrange the options "DVD/CD", "Drive C:" and "Floppy".

Floppy. Hmm, there's a thought. It's a bit 80s, but it would work :)

---

### Post by xurizaemon on 2007-05-04
[Report of same problem with a Dell Dimension 8300 ignoring GRUB]("http://ubuntuforums.org/showthread.php?t=119565").

I will try the method suggested in that post and report success/failure ...

---

