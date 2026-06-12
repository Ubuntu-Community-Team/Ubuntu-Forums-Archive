---
title: "[SOLVED] Can't find HD"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by tajreed on 2008-03-31
I reformatted a second internal HD and copied my Home directory to the reformatted HD using Gpartedlive.
 
Reboot and script says cannot find second drive. Must restart with Control-d.

The drive shows up in etc/fstab but not in /dev/disk/by-uuid. Is this the problem? If so, how can I get the uuid of the missing drive into /dev/disk. It doesn't seem editable.

J
Thanks

---

### Post by forestpixie on 2008-03-31
you need to edit fstab, assuming you run ubuntu, back it up first

```
sudo cp /etc/fstab /etc/fstab.3103
gksudo gedit /etc/fstab
```

get the UUID for the drives from terminal - you might need to use sudo and chnage the UUID in fstab to suit

```
blkid
```

---

### Post by tajreed on 2008-03-31
Hey, that fixed the problem. Second HD now shows. I thought I had checked all of these possibilities. Live and learn from the forums.

Thanks

---

