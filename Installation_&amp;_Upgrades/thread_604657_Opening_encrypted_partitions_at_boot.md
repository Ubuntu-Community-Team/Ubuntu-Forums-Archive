---
title: "Opening encrypted partitions at boot"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by compu73rg33k on 2007-11-06
So I have 5 partitions. /boot, /, /usr, /swap, and /home. I've encrypted the latter 4 with luks encryption using cryptsetup. I've changed the fstabs to use the device /dev/mapper/device and then setup my /etc/cryptttab to load them. However at boot it immediately asks the password for root. I put it in and then it continues to load up and then it fails when trying to mount /usr and /home complaining that the device /dev/mapper/device isn't found. I then try to open the partition with the command
```

cryptsetup /dev/sda6 usr

```
and it complains about the shared cryptsetup library not being found. This makes sense because it's under /usr/lib, which apparently hasn't been opened and mounted yet. However, why is the root partition opening up but not the rest? How is it working if the library isn't yet available? I think it has something to do with dm-crypt, but I did add dm-crypt to my list in /etc/modules so that is loaded. I confirmed this with lsmod. How can I open up the other partitions into /dev/mapper in addition to /dev/mapper/root ?

---

