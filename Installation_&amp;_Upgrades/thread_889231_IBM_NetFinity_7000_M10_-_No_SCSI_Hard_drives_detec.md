---
title: "IBM NetFinity 7000 M10 - No SCSI Hard drives detected during Server 8.04 LTS install"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by asphodeli on 2008-08-13
Hi all,

I am unable to detect any SCSI hard drives during installation. It's running on a ServeRAID SCSCI card. Does anyone know where I can find a driver disk?

EDIT: Solved - Update ServeRAID-3H BIOS to latest version.

---

### Post by asphodeli on 2008-08-14
OK, something new just happened. Installation was successful, but upon reboot, it gives me the error ```
kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

Going into recovery mode shows more lines, and gives me the same error, ,but with more info a few lines above it, one of it was ```
Please append a correct "root=" boot option; here are the available partitions:
```

No partitions were listed, and the immediate line after that was the Kernel Panic message as above.

I'm trying to use the Desktop LiveCD to edit the GRUB menu options to see if that helps now.

---

