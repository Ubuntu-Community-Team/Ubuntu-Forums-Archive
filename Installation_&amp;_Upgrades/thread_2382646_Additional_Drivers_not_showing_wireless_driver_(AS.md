---
title: "Additional Drivers not showing wireless driver (ASUS PCE-AC88)"
date: 2018-01-16
forum: Installation &amp; Upgrades
---

### Post by porkchop_001 on 2018-01-16
I've just done a fresh install of Ubuntu 16.04 on my home PC. I plugged in ethernet to do the updates and also check to see if additional drivers were available. Additional CPU and GPU drivers were listed, and I switched to them. However, there was no wireless driver listed.


I have an ASUS PCE-AC88 which is plugged into the bottom PCI-E slot of my Gigabyte AORUS Z270X-Gaming K5 motherboard.


I ran the following:

```
lspci -v
```

And saw what I think is my card being recognised:

```
Network Controller: Broadcom Corporation Device 43c3 (rev 04)
```

Is there somewhere I can get a driver for it? I'd love to be able to use wireless! Any help would be awesome. Thanks :)

---

### Post by westie457 on 2018-01-16
Hi.
    Fortunately for you this wifi chip has been seen with a working solution on these Forums. [https://ubuntuforums.org/showthread.php?t=2337200](https://ubuntuforums.org/showthread.php?t=2337200)

    The original solution was found on Fedora Forums here. [https://forums.fedoraforum.org/showthread.php?310626-Fedora-24-and-ASUS-PCE-AC-88&p=1769999#post1769999](https://forums.fedoraforum.org/showthread.php?310626-Fedora-24-and-ASUS-PCE-AC-88&p=1769999#post1769999)

Hope this helps.

---

