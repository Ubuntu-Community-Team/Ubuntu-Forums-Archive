---
title: "Install on SATA &amp; PATA problem"
date: 2005-03-25
forum: Installation &amp; Upgrades
---

### Post by drummer on 2005-03-25
Hi,

I'm not sure if this is the right place to post this, but here we go...
The following could be a problem with the grub setup in the hoary installation, or just a prob with my setup.. please tell me if it's my problem and how it can be fixed.

I had a dual boot with win2k and hoary preview on an 80g sata drive which was booting fine. I wanted to reinstall with XP and hoary on the sata with a 4g pata as a fat32 share for both OSs. I tried that but recieved "grub error 22" upon reboot. I tried multiple reinstalls of hoary on each hard drive and grub to hd0 and /dev/sda but with the same error.

I think I know what grub is doing but i'm not sure why. I install grub to "/dev/sda" but the menu directs the boot to partitions on the pata drive, ie "root (hd0,5)". I would have thought that "hd0" should direct to the sata, since that's where hoary and grub were installed.

It's not such a problem for me since i worked around by installing without the pata and connecting it later, but i imagine it would pose a problem if one wanted a dual boot using different hard drives and a sata as primary boot (which is what I originally had in mind).

I'm not very experienced with grub and setting it up, so the answer could be blatently obvious, but don't flame me for asking.

My partitions are as follows (currently):
hdc (secondary IDE channel, master)
hdc1    fat32     primary     /winshare

sda (first SATA channel)
sda1    ntfs       primary     win2k     bootableflag
sda6    ext3      logical       /
sda7    swap     logical       swap
sda5    fat32     logical       /wind  (this partition will eventually be removed)

Thanks

---

