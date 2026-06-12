---
title: "Avoid boot problem with last updates 10.04"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by Francis 24/24 on 2010-09-08
In order to avoid boot to stop with "udevadm trigger is not permitted ..."
after installing the last recommended updates for 10.04, as many
people have suffered, I suggest :

- install updates with Update Manager as usual

- DO NOT accept to reboot right now 

- as root :

# cd /boot
# sudo update-initramfs -u -k 2.6.32-24-386
# sudo update-initramfs -u -k 2.6.32-24-generic

- reboot

Worked fine for me.

Cheers !

---

