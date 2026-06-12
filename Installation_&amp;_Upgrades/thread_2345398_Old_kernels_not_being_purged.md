---
title: "Old kernels not being purged"
date: 2016-12-03
forum: Installation &amp; Upgrades
---

### Post by fr33z0n3r on 2016-12-03
I know that there is some awareness of issues related to old kernels hanging around in /boot.  I'm curious if my config has an explanation for this.  Ubuntu 16.04 

```
Linux hostname 4.4.0-51-generic #72-Ubuntu SMP Thu Nov 24 18:29:54 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```


I discovered today that /boot was over half full with about 10 kernels.  So I ran 

```
sudo apt autoremove --purge
```

Since then now I only have the following remaining.  But I wonder about that oldest version.  Why is it hanging around?  Is this old kernel causing the lack of autoremoval?


```
/boot/vmlinuz-4.4.0-51-generic
/boot/initrd.img-4.4.0-51-generic
/boot/vmlinuz-4.4.0-47-generic
/boot/initrd.img-4.4.0-47-generic
/boot/vmlinuz-3.19.0-43-generic
/boot/initrd.img-3.19.0-43-generic
```

---

### Post by ian-weisser on 2016-12-03
Autoremoval is deliberately fragile; designed to fail rather than autoremove large slabs of your system - it may fail due to a manually-installed header package, or a half-configured package, or a dozen other causes.

One check is to look for manually-installed packages. Anything apt-marked as 'manual' is inegible for autoremoval.
```
apt-mark showmanual | grep linux
```

Another check is to look for obsolete release-specific metapackages that were not removed:
```
dpkg -l | grep linux | grep vivid
```

Another check is to look for obsolete kernel header packages. Those sometimes prevent the associated kernel image from autoremoving:
```
dpkg -l | grep linux-headers
```

Another check is to look for unconfigured or half-configured kernel packages. These usually happen during an out-of-space condition.
```
dpkg -l | grep linux-image-generic
```

---

