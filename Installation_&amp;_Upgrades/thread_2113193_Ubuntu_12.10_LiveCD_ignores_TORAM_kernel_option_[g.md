---
title: "Ubuntu 12.10 LiveCD ignores TORAM kernel option [grml-rescueboot]"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by Wug on 2013-02-06
I have installed grml-rescueboot and changed the config to the following:

```

ISO_LOCATION="/home/me/iso"
CUSTOM_BOOTOPTIONS="toram"

```

/home/me/iso contains a freshly torrented Ubuntu 12.10 iso, and grub has been updated to include an entry for it.

I can successfully boot to the iso image, but for some reason the kernel is ignoring the 'toram' option (which is supposed to load the ISO into ram, allowing me to unmount the filesystem where the ISO is located).

Utilities report significantly less than expected memory usage for an 800MB iso to reside in memory, and I am unable to unmount the hard disk (device busy).

I have 3GB of RAM in this laptop (of which anywhere between about 400 and about 700 is listed as used), is this not enough?

Let me know if you need any supplementary information, and please be sure to specify if you need it from inside the LiveCD environment or the installed environment.

---

