---
title: "Nvidia trouble"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by SpongeBob SquarePants on 2006-07-16
Evening chaps and chapettes,

I've just switched to Ubuntu after a fairly long stint with FC4 and am having a few problems with installing my nvidia drivers. I basically followed the information in this link.....[https://help.ubuntu.com/community/BinaryDriverHowto/Nvid](https://help.ubuntu.com/community/BinaryDriverHowto/Nvid), but when it came to the "sudo nvidia-glx-config enable" command I got the message back......

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

I tried executing the first suggested command, which basically resulted in a reinstall.....lol. Anyway, I'm interested in knowing how to proceed without wrecking anything.

The only thing I can think of that may be on any interest was that I installed the nvidia-glx drivers no problem, but when it came to installing the linux-restricted-modules corresponding to my kernel, I noticed in synaptic that they were already installed. I'm assuming that they automatically installed themselves as part of the update proceedure.

That's it. Any help would be appreciated.

---

### Post by bluecherry on 2006-07-16
Try this:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

This will also update the MD5 checksum so nvidia-glx-config won't complain about that.

If you want to make changes to your xorg.conf file, do this after nvidia-glx-setup had it's way with it ;).

---

### Post by SpongeBob SquarePants on 2006-07-16
Thanks very much. Worked a treat. After a bit of tinkering I managed to get rid of that awful Nvidia splash too :D

---

