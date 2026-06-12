---
title: "Weird dual-boot issue"
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by scottpledger on 2012-07-08
Hey all,
I just installed kubuntu 11.10 (x64) side-by-side with Windows 7 64-bit on a friend's laptop. However, every couple of days she calls me saying that when she starts up her computer she has only a flashing cursor (an underscore, to be precise) in the upper left-hand corner of an all-black screen. I can fix the issue by just re-installing GRUB from the boot USB, but the downtime for her is unacceptable.

This only ever happens after she has booted into Windows, so I'm assuming there's something in her Windows install that is writing over GRUB, but I can't figure out what it is since it doesn't do it every time she boots into Windows.

I've been dual-booting for years and the only time this has ever happened to me was when trying to install Win7 SP1, but she hasn't installed any Windows upgrades recently. Any help that anyone can give me is greatly appreciated!

More Info:
[LIST]
[*]I reinstalled GRUB by running the following as root:
```

mount /dev/sda5 /mnt
grub-install --boot-directory=/mnt/boot /dev/sda
umount /mnt

```
[*]I did some research on Windows programs that overwrite GRUB and found that Mcafee would sometimes do this, so I removed the only Mcafee product that was on her computer: Mcafee Security Scan (or something like that - it wasn't the full Mcafee suite or anything).
[*]If you just let it sit after one of these failed boot-ups, it will give you nothing more than the flashing cursor for hours, although the machine gets really warm really quickly when it does this, so I presume the processor is doing some work but I'm not sure what.
[/LIST]

---

