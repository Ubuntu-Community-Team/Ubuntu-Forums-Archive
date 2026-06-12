---
title: "Kernel won't boot after fresh install of ubuntu-server  6.06 LTS"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by llamahunter on 2007-05-02
The installation appeared to go fine, and when the machine boots up, the grub loader finds the correct kernel.  However, the last lines printed are 

"Uncompressing Linux... Ok, booting the kernel."

and then nothing more.  I booted using Knoppix and looked at the installed files.  Everything seems in place and fine.  I tried removing 'quiet' from the boot params but no additional info was forthcoming.

Anyone have any idea what this could be?  I tried tricks like putting the /boot partition in the first cylinders, making the / partition < 128 GB, letting ubuntu reformat the whole disk whatever way it liked... all installations behaved the same.  No linux.

Any ideas?

---

### Post by llamahunter on 2007-05-02
anyone have any ideas?  i'm fairly linux savvy, and can usually debug problems with the boot loader or post kernel bringup, but i have a gap around the actual kernel boot process.  help would be appreciated!

---

### Post by confused57 on 2007-05-02
You might try going into bios and disabling ACPI, or you might just be able to add an entry to your kernel line:
acpi=off.

If you're getting a grub menu at boot, highlight your Ubuntu entry, press "e" then add the above(acpi=off) to your kernel line, then press "b" to boot.

---

### Post by r-senior on 2007-05-03
I had a similar issue:

[http://ubuntuforums.org/showthread.php?t=430863](http://ubuntuforums.org/showthread.php?t=430863)

Richard

---

### Post by llamahunter on 2007-05-05
Thanks r-senior, that did the trick.  Too bad the default installation of ubuntu-server doesn't work out of the box.

---

