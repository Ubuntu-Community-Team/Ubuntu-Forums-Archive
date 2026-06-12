---
title: "grub2 update has broken my luks?"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by Orestez on 2010-12-09
Yesterday evening I was dumb enough not to pay attention when the grub2 update asked me where I wanted to install grub2 or so. I had to check a few boxes, and checked all of them.

This seems to have broken the header of my luks device/partition. When I try opening it:

> cryptsetup luksOpen /dev/sdb crypto --debug
# cryptsetup 1.1.0-rc2 processing "cryptsetup luksOpen /dev/sdb crypto --debug"
# Locking memory.
# Allocating crypt device /dev/sdb context.
# Trying to open and read device /dev/sdb.
# Initialising device-mapper backend.
# Timeout set to 0 miliseconds.
# Password retry count set to 3.
# Iteration time set to 1000 miliseconds.
# Password verification disabled.
# Trying to load LUKS1 crypt type from device /dev/sdb.
# Reading LUKS header of size 1024 from device /dev/sdb
# LUKS header not detected.
# Releasing crypt device /dev/sdb context.
# Releasing device-mapper backend.
# Unlocking memory.
Command failed with code 22: /dev/sdb is not a LUKS device.

Note the "header not detected". Is there any way to fix a luks header?

Thanks for reading,
Orestez

---

### Post by oldfred on 2010-12-10
When you install grub to a windows partition we use this to fix it. Do not know about LUKS partitions. You may want to wait to see if someone knows for sure with LUKS problems.
It uses testdisk to restore the backup of the boot sector, if it is different.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Orestez on 2010-12-11
Thanks a lot for taking the time to reply, but apparently if the header of the LUKS partition gets overwritten, pretty much all hope is lost because it contains all the relevant information needed to decode the (encrypted) partition. 

Teaches me to make a backup of the header next time... that should be advertised in all tutorials and is a pretty big flaw of luks imo.

Regards,
Orestez

---

### Post by wilee-nilee on 2010-12-11
For all of our sakes, so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

maybe lost without the header the script may help you in the future at the least.

---

### Post by Orestez on 2010-12-11
Unfortunately I've already reformated, as my research turned out that without the header (and I checked with a hexeditor that it was actually broken/overwritten) it cannot be restored, I know what was wrong. I'll keep the script in mind though, thank you.

Regards,
Orestez

---

