---
title: "[solved] Dual boot issue"
date: 2017-01-25
forum: Installation &amp; Upgrades
---

### Post by shawn-m72 on 2017-01-25
Just installed Ubuntu on my older Windows Vista machine.  Dual boot screen loads fine.  I can boot Ubuntu fine, but Windows Vista instantly locks.  Link to the boot-repair is paste2.org/VEZDHtKh.  Thanks for any help you can give me.

Shawn

---

### Post by gdesilva on 2017-01-25
Not an expert in deciphering bootrepair but noticed that secureboot may be enabled.

=================== UEFI/Legacy mode:
 	This live-session is not in EFI-mode.
 	SecureBoot maybe enabled.


Perhaps nothing to do with it but worth turning it off.

---

### Post by ubfan1 on 2017-01-25
Please fix the typo in the link, paste2.org/VEZDHtKh
Don't see anything wrong,but maybe add the drivemap line below to just before the chainloader+1 line
drivemap -s (hd0) ${root}
You can type "e" at the grub menu to edit the Windows boot, and just try typing in the line, then boot crtl X (instructions bottom of screen).

---

### Post by shawn-m72 on 2017-01-25
Turning off the secure boot fixed it.  Thanks for the fast response and suggestions!

Shawn

---

