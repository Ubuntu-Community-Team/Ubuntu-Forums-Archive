---
title: "Need help with grub."
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by dtree46 on 2014-09-25
My PC dual boots with Ubuntu 14.04 and W7.
Installed W7 on flash drive. Now to get rid of W7 on PC.
W7 is on /dev/sda a 80gb hd. Ubuntu is on /dev/hdb a 1tb hd.

How do I change grub so it boots up to Ubuntu on /dev/sdb when W7 is gone?

dlw

---

### Post by Bashing-om on 2014-09-25
dtree46; Hello;

Are you Presently able to boot ubuntu ? Is ubuntu to remain on 'sdb' ?
Then if booting:
terminal command:
```

sudo grub-install /dev/sdb

``` and in bios change the boot priority to that 2nd hard drive as the 1st priority.
Reboot and verify still able to boot.


Edit; Once Win7 is removed update grub:
```

sudo update-grub

``` to update the boot menu.
[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by dtree46 on 2014-09-25
How is W7 properly removed?
Use gparted?
Just delete everything?

Suggestion please.

---

### Post by Bashing-om on 2014-09-25
dtree46; umm..

What are you going to do with sda once Win7 is removed ?
If I were just going to wipe the disk, I would use the 'dd' tool to do so, then I might partition the drive with Gparted, depending on the use case.

[INDENT][INDENT]depends, depends
[/INDENT][/INDENT]

---

### Post by dtree46 on 2014-09-25
Not sure what to do with it. Just wanted to get W7 off.
I very seldom use W7 but ... I need it for cell phone use.

Thanks for your help.
dlw

---

### Post by Bashing-om on 2014-09-25
dtree46; Welp;

Do use the disk, even for "cell phone" use, the disk will have to be formatted to some file file system.

[INDENT][INDENT]can't write when there is nothing to write to
[/INDENT][/INDENT]

---

