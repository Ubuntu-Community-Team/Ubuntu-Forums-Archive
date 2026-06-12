---
title: "Reimaged system U1404 on separate drive"
date: 2016-05-24
forum: Installation &amp; Upgrades
---

### Post by hawaii243 on 2016-05-24
Had to reimage my windows system, so U1404 is no longer displaying on the boot prompt. U1404 is on a separate drive and works fine. Now, trying to get U1404 to display / boot not sure which partition to utilize from it's installed location. I'm using EasyBCD to manage boot. 

[IMG]http://s33.postimg.org/4zg5k4n3z/Clipboard_20160524.png[/IMG]

---

### Post by grahammechanical on 2016-05-24
When we have two drives and have Windows on one drive and Ubuntu on the other we can keep the Window's bootloader on its drive and the Ubuntu bootloader (Grub) on the Ubuntu drive. Then we use the BIOS utility to select which drive to boot from. Selecting the Ubuntu drive will give us the option to load both Ubuntu & Windows.

What partitions did you set up when you installed Ubuntu? /boot partition + Ubuntu ( / ) partition + /home partition + swap? If so then my guess is
```

partition 1 = /boot
partition 2 = /
partition 3 = /home
partition 4 = swap
```

Regards

---

### Post by oldfred on 2016-05-24
Boot your Ubuntu live installer in live mode and add Boot-Repair.

 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

