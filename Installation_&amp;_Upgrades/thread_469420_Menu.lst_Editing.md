---
title: "Menu.lst Editing"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by Pumalite on 2007-06-09
I need help editing Ubuntu menu.lst to boot Mepis. This is what I added and did not work. ( Ubuntu id the 3rd distro in this box, and the one that recognizes the other two ):

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title MEPIS at hda1, newest kernel
root (hd0,0)
kernel /boot/vmlinuz root=/dev/hda1 nomce quiet vga=791
savedefault
boot

Your help will be much appreciated. This is my fdisk -l:

pumalite@pumalite-desktop:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 7269 58388211 83 Linux
/dev/hda2 7270 7709 3534300 83 Linux
/dev/hda3 7710 7984 2208937+ 83 Linux
/dev/hda4 7985 14596 53110890 83 Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 1 262 2104483+ 82 Linux swap / Solaris
/dev/hdb2 263 2179 15398302+ 83 Linux
/dev/hdb3 2180 4998 22643617+ 83 Linux

Disk /dev/hdd: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdd1 1 4870 39118243+ 83 Linux
pumalite@pumalite-desktop:~$

hda has two partitions; Mepis in hda1 and Ubuntu in hda2. Suse in hdb. hdd for storage.

Any suggestions much appreciated. If you need the entire menu.lst, let me know.

---

### Post by confused57 on 2007-06-09
Try a configfile entry to boot Mepis:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

use the example listed, except your root is (hd0,0)

---

### Post by Pumalite on 2007-06-09
> **confused57 said:**
> Try a configfile entry to boot Mepis:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

use the example listed, except your root is (hd0,0)

Thanks a lot. I'll try that.

---

### Post by Pumalite on 2007-06-10
> **confused57 said:**
> Try a configfile entry to boot Mepis:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

use the example listed, except your root is (hd0,0)

Success!!! confused57 you are great. I thank you so very much. In the process I learned a lot.

---

