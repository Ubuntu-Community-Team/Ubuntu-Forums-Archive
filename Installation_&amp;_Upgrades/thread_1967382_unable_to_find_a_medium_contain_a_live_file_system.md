---
title: "unable to find a medium contain a live file system"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by svennson on 2012-04-28
Hello, 

I tried to install ubuntu 12.04 (ubuntu-12.04-desktop-i386.iso) on my acer aspire M1641, but failed with this error :
```
unable to find a medium contain a live file system
``` (in busybox)

I attempted to change my hard drive to "RAID" as I found this in some topics to be a solution, it din't work. I use a USB flash drive to get ubuntu to install. Nor live, not direct install works. The hard drive connected is 250GB and formatted in windows. (so its empty)

Any thoughts ?

---

### Post by svennson on 2012-04-28
partially solved, it seemed bios had an option to select "bootloader" it was on automatically detect OS, this should load windows aswell as linux, but seems this stopped linux from loading. Putting it on "other" did let me load ubuntu :)

i'm putting it solved if i get it installed :)

// edit

installer just crashed.

// edit
I have another issue, but the problem indicated is solved switching to "other" in BIOS.

---

### Post by oldfred on 2012-04-28
Is this a new UEFI system? And are you booting Window in UEFI or BIOS mode?

If you turned RAID on it writes meta-data to drives and then Linux will not do a normal install as it sees that meta-data and knows not to destroy a RAID install.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

