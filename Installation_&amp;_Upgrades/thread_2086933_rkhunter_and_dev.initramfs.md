---
title: "rkhunter and /dev/.initramfs"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by funkyhead on 2012-11-22
**Problem : **
Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'

**Solution :**
On Unbuntu 12.04 with Rootkit Hunter 1.3.8 :
*Edit *: /etc/rkhunter.conf
*Add *: ALLOWHIDDENFILE=/dev/.initramfs
*Edit *: /usr/bin/rkhunter
*Add before line 847* between [then] and [case "${OPT_NAME}" in] : **test "${OPT_NAME}" = "ALLOWHIDDENFILE" -a -h "${FNAME}" && continue**

*Execute *: rkhunter --propupd

**Result :**
No false positive on the next run.

---

### Post by storm-coder on 2013-10-01
Thanks, it works fine !

But knowing a few things about scripting I still dont really understand the :
 **test "${OPT_NAME}" = "ALLOWHIDDENFILE" -a -h "${FNAME}" && continue**

Could you please explain a little more ?

Edit :

Sorry, with a "man test" it's ok :s

Let's explain for other peopple :
-a is for both conditions true
1st one is the option is "**ALLOWHIDDENFILE"**
2nd one, -h = the filename exists an is a symbolic link (same as -L)

---

