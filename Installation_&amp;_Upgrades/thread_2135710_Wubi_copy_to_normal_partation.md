---
title: "Wubi copy to normal partation"
date: 2013-04-15
forum: Installation &amp; Upgrades
---

### Post by whynot on 2013-04-15
Hi everyone,
I have wubi 12.04 ubuntu installed system.Now i would like to move this system to normal partation. I have harddisk with

sda1 100mb NTFS (System Reserved)
sda2 351GB NTFS (im going to use this partation for ubuntu linux.)
sda3 346GB NTFS Windows 7 (i have under ubuntu folder wubi)
How can i move forward?
Thanks.

---

### Post by sudodus on 2013-04-15
There is a good description how to do it in this link
[URL="https://help.ubuntu.com/community/MigrateWubi"][COLOR=#ff0000]
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)[/COLOR][/URL]

Good luck :-)

---

### Post by whynot on 2013-04-15
> **sudodus said:**
> There is a good description how to do it in this link
[URL="https://help.ubuntu.com/community/MigrateWubi"][COLOR=#ff0000]
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)[/COLOR][/URL]

Good luck :-)

Thanks but how do we setup partitions? Is there any easy graphical user interface or step by step guide?

---

### Post by sudodus on 2013-04-15
First ***backup*** at least all your personal data (documents, photos etc) and Windows. Editing partitions is risky.

Next you need to find out what kind of boot system you have,  old-time ***BIOS or UEFI***. If BIOS it is straightforward, just let the  installer do the job. if UEFI other guys at the Ubuntu Forums know better what to do.

You can use ***gparted***, which is part of your Ubuntu 12.04 install CD/DVD/USB drive. Decide how big   ***RAM***   should be and let the rest of the available space be the  ***root partition***  (with the file system ext4).

---

