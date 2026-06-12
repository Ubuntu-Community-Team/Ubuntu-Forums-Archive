---
title: "Windows 7 won't start after dual boot ubuntu 12.10 installation"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by Nuclear Mosquito on 2013-02-07
Hey guys.

I recently installed Ubuntu 12.10 next to a Windows 7 Home Premium 64-bit installation. I only have one 1.5TB HD in my pc. The HD had three partitions before the installs. I took some space from the partition that I use for media and created a new partition for the Ubuntu installation (using the Ubuntu installer). The grub loader displays both operating systems, but when I boot windows it only displays a black screen for a second and then reverts to the grub loader. Ubuntu works fine.

I've tried running the Windows startup repair utility from the windows disc, but to no avail. I have noticed that my system drive moved from c to f.

Any help with getting my windows to boot again would be appreciated.

Sincerely
Nuclear Mosquito

---

### Post by darkod on 2013-02-07
Install boot-repair and run it but only to create the bootinfo. Post the link so we can see more details.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Nuclear Mosquito on 2013-02-07
[http://paste.ubuntu.com/1621214/](http://paste.ubuntu.com/1621214/)

Hope this is what you need. :)

---

### Post by darkod on 2013-02-07
OK, few things are wrong.

1. You have grub2 in the boot sector of sda1. That partition needs to have a windows boot sector. Also, you need to delete the /grldr files from that partition, they should not be there. I have no idea how they got there.
You can use this testdisk procedure to restore the windows boot sector of sda1:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

2. You have windows bootloader on /dev/sda instead of grub2. I guess you installed it on /dev/sda1 instead of /dev7sda, and that's how it ended up there.
Once you sort out the boot sector of sda1, boot the ubuntu cd in live mode and put grub2 on /dev7sda with:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot without the cd and that should be it.

---

### Post by Mark Phelps on 2013-02-07
From what I read, "grldr" is part of a Wubi installation -- so that implies that the OP tried installing via Wubi, first.

---

### Post by Nuclear Mosquito on 2013-02-07
> **darkod said:**
> OK, few things are wrong.

1. You have grub2 in the boot sector of sda1. That partition needs to have a windows boot sector. Also, you need to delete the /grldr files from that partition, they should not be there. I have no idea how they got there.
You can use this testdisk procedure to restore the windows boot sector of sda1:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

2. You have windows bootloader on /dev/sda instead of grub2. I guess you installed it on /dev/sda1 instead of /dev7sda, and that's how it ended up there.
Once you sort out the boot sector of sda1, boot the ubuntu cd in live mode and put grub2 on /dev7sda with:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot without the cd and that should be it.

Thanks a lot! Worked perfectly the first time. Also thanks for your rapid response. Its people like you who make open source the way to go.:D

---

### Post by theatrosteza on 2013-06-03
[h=2]Windows 7 won't start after dual boot ubuntu 12.10 installation[/h]sorry for my bad english.i have this problem,i cant boot windows 7.i hope with this link you would b able to help me!
[http://paste.ubuntu.com/5728795/](http://paste.ubuntu.com/5728795/)

---

