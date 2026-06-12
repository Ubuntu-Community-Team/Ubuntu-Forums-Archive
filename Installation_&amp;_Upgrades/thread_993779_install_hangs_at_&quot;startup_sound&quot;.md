---
title: "install hangs at &quot;startup sound&quot;"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by wcminor on 2008-11-26
trying to install 8.10 and it hangs at "startup sound", this happens when trying to install and the live cd, i have 2 cd's, one is from cannonical and it happens on both. confused and have a good day.

wcminor

---

### Post by lemming465 on 2008-11-28
You could have either a flaky CD drive or bad memory.  Try running memtest86+ for about 20 minutes to rule out the memory, and then try the validate option on the CD before booting it.  If the memory and the CD are both good, try alternate kernel boot options such as "noapic", "nolapic', "noapm" either alone or in combination.  If you are still having problems, try Ctrl-Alt-F1 to switch to a text console, and see if you have any error messages that might pin the symptoms down better.  Good luck with it.

---

### Post by wcminor on 2008-11-29
id did try the alternate kernel boot options and got it to work, thanks and have a good weekend.

wcminor

---

