---
title: "Dapper to Edgy Sever Upgrade Gone Horribly Wrong"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by CharlieM on 2007-01-17
I used apt-get to upgrade from Dapper Server to Edgy Server unfortunately now my server won't boot. It fails to mount the root partition during boot. Luckily the upgrade left the dapper initd image option in the Grub menu, so  I can at least get access to a full console.

The problem appears to be its unable to find the root partition to boot from. It says

```
Alert! /dev/disk/by-uuid/xxxxxxxxxx/ does not exist
```

*Where xxxxxxxxxx is my root hd's uuid. *

I looked at the actual uuid and it is the same in the grub menu.lst file as the original dapper entries that do worked. I tried changing it in menu.lst to /dev/hda1 which had the same effect.

I then used the basic console that booting edgy's initd image leaves you at. It turns out that /dev/disk does not exist. The rest of /dev looks normal. 

Does anyone have any ideas what's gone wrong and better still how to solve it.

Charlie

---

### Post by CharlieM on 2007-01-17
Would you bleave it, after hours of sarching and not finding anything I decide to post. Then with in 30 secs of posting the first post I found the solotion.

```

cd /boot
dpkg-reconfigure linux-image-2.6.17-10-server
```

It basicly forces the system to build a new boot image. Not sure why it didnt build a valid one first time around. I still have a few problem but I will try to fix them first my self before posting again :).

One things for sure booting is a lot quicker under Edgy server.

Charlie

---

