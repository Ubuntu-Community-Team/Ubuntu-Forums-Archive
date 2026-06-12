---
title: "Installed xubuntu...grub error 21"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by gareth41 on 2007-02-27
i installed xubuntu onto a 40gb hdd, i have windows on a 250gb hdd (both sata), when i tried to restart after installation, i get this:

> GRUB Loading stage1.5
GRUB Loading, Please Wait...
Error 21

So now i cant boot into anything.

please help.

---

### Post by taurus on 2007-02-27
Boot with the LiveCD and post the output of this command here.

```
sudo fdisk -l
```

---

### Post by gareth41 on 2007-02-27
turns out the drive wasnt enabled in the bios (googled), that just seems strange beacuse on winxp it was working fine (ntfs).

---

