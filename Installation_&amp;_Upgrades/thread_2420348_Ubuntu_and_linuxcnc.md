---
title: "Ubuntu and linuxcnc"
date: 2019-06-03
forum: Installation &amp; Upgrades
---

### Post by electros6 on 2019-06-03
Hi guys,
    I installed Ubuntu 18 lts in my pc. After I install linuxcnc in the same hard disk. When I reboot the pc it enters into linuxcnc without grub menu, even after I updated the grub nothing happens. Please guide me since I need to linux.
              Regards
        N.Baskaran

---

### Post by TheFu on 2019-06-05
I haven't a clue, but it is possible that the linuxcnc installer wiped the Ubuntu install, yes?
To check that, boot from the Ubuntu 18 install media, choose "Try Ubuntu".  Then you can look at the partitions to see what are there.

```
sudo fdisk -l
```
will show the partitions.
So will ```
lsblk -f
```

---

