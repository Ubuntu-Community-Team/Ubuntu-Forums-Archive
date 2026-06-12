---
title: "some error while installing anything"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by roni21 on 2010-07-26
whenever i install something from terminal or run update then i get these errors

E: linux-image-2.6.32-24-generic-pae: subprocess installed post-installation script returned error exit status 2
E: grub-pc: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic-pae: dependency problems - leaving unconfigured
E: linux-generic-pae: dependency problems - leaving unconfigured

i tried 

$ sudo apt-get install -f
$ sudo dpkg --configure -a
$ sudo update-grub

no change:(

can someone help me out here?

---

### Post by P4man on 2010-07-26
You manually installed the PAE kernel? Are you *sure *you want it?
If you arent really sure; then remove it again.

```
sudo apt-get remove linux-image-2.6.32-24-generic-pae
```

---

### Post by roni21 on 2010-07-26
thnx, but still having grub-pc error :(

---

