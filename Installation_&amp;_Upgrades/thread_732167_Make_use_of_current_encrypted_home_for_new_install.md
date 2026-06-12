---
title: "Make use of current encrypted /home for new installation"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by Meson on 2008-03-22
How can I tell the ubuntu installer (hardy) that one of my current encrypted partitions contains my /home?  Do I have to do this manually after the install?  My current layout:
```
sda1 - /boot
sda2 - encrypted /home
sda3 - empty
sda4 - encrypted lvm (gutsy)
      - /root
      - /swap
```

I want to install hardy in the free space now and come up with something like this:```
sda1 - /boot
sda2 - encrypted /home
sda3 - encrypted lvm (hardy)
      - /root
      - swap
sda4 - encrypted lvm (gutsy)
      - /root
      - swap
```

But I want to know if there is a way during the install to tell hardy that my home directory will be in sda2

---

