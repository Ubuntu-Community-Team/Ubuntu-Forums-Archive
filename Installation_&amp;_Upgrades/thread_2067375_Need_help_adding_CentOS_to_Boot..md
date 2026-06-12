---
title: "Need help adding CentOS to Boot."
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by RedBolt on 2012-10-06
I've installed CentOS after Ubuntu and ran boot-repair to try to get Ubuntu back, now i only have ubuntu.

Here is the boot-repair info: [http://paste.ubuntu.com/1264529/](http://paste.ubuntu.com/1264529/)

I appreciate any help.
Thanks.

---

### Post by darkod on 2012-10-06
As you can see, you installed CentOS as LVM. Ubuntu does not include the LVM package by default so it can't look into the LVM. You should be able to install the package, activate the LVM and then run update-grub. Something like:
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo update-grub
```

---

### Post by RedBolt on 2012-10-07
Thank you, it is now working :)

---

