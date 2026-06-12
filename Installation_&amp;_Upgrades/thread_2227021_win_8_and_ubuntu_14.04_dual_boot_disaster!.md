---
title: "win 8 and ubuntu 14.04 dual boot: disaster!"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by tubunter on 2014-05-30
Hello,

I'm coming across an ubuntu failed installation on a UEFI machine with win 8 already installed.
The ubuntu installer didn't see existing win os on machine, so to avoid problems I aborted installation...but something gone wrong anyway, so now I have an unbootable machine...
I followed some fixing guides focused on that issue, and tried to use bootrepair utility as reccomended, but per example, I get no "separate EFI partition" option as suggested, seems because efi partition was not present...instead it is there, as stated in this is a bootrepair complete report:
[http://paste.ubuntu.com/7550108/](http://paste.ubuntu.com/7550108/)

if someone is able to help me would be greatly appreciated

Thanks

Dan

---

### Post by mikewhatever on 2014-05-30
It looks like you've overwritten W8 with Ubuntu, because there arn't any Windows ntfs partitions. That more or less means there is nothing to fix, and you'll just have to reinstall W8.

---

