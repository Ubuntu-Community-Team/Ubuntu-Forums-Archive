---
title: "Dual boot with Win 8.1 and U 14.04 on SSD, question mark error"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by joe132 on 2014-09-04
Had a search of the forums but haven't found any threads satisfying my particular issue.

Not my first time installing ubuntu, but apparently the rules have all been changed in regards to it being Win 8.1 and U 14.04 so...

_What I did:_

Created a 20GB partition in my SSD on the Win 8.1 side.
Disabled Fast Boot.
Checked to see that it boots in UEFI (personally have no idea what this means but it seemed to be a common thing in other issue threads I browsed), but couldn't find secure boot to disable.

Booted from my USB with the U iso, started installation process.
In the partition window, the SSD it split into loads of /dev/mapper/etc's, never seen this before (is this something unique to SSD's?).
I was told that there is no need to create a swap because it's unneeded for an SSD and also it would shorten its life (the laptop is also 16GB RAM).
Find the free space and create a ext 4, logical with mount point of /.

Select /dev/sda, hit install and get the ??...?? error.
Re-tried, selecting the /dev/mapper, same error.

EDIT: Figured out the boot diagnostic. [http://paste.ubuntu.com/8242331/](http://paste.ubuntu.com/8242331/)

Thank you for your patience and help.

---

