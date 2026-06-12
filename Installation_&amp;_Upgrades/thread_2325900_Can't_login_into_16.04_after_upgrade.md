---
title: "Can't login into 16.04 after upgrade"
date: 2016-05-26
forum: Installation &amp; Upgrades
---

### Post by pyrophorus2 on 2016-05-26
Upgraded from 15.10 to 16.04, and now I can get to the login screen.
Typed in my password, and it flickers and go back to the login screen.
Same thing with my other accounts on it.

I've seen posts where things were changed in the BIOS, but I don't have those same options.

Any ideas?

---

### Post by ptn107 on 2016-05-26
nvidia card?

---

### Post by ubfan1 on 2016-05-26
Does the guest session allow login to work?  If so, then the problem is probably in the "hidden" dot files in your home directory.  They configure things like video and may be wrong under the upgrade, particularly if they are set up for proprietary video drivers, and you are running under the defaults in the new system.  Try and install the necessary drivers from a virtual terminal in that case, try "nomodeset" on grub's kernel boot line next to "splash quiet".

---

