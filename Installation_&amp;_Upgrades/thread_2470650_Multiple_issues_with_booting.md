---
title: "Multiple issues with booting"
date: 2022-01-06
forum: Installation &amp; Upgrades
---

### Post by vespertial on 2022-01-06
Hello!

I run Ubuntu only on a laptop.

So I installed the following packages with apt-get: 
```
libdbus-1-dev libudev-dev libical-dev libreadline-dev
```

And as they installed various things started to shut down, and at the end nothing worked, so I restarted. 

This led me to being stuck on the splash screen, where I discovered from the kernel logs that /boot/efi was failing to mount. Some googling led me to check the /etc/fstab file, but as far as I could tell everything matched up. I was also able to run ```
mount /dev/nvme0n1p1 /boot/efi
``` with no issues, was able to continue, though wasn't able to get to a graphical interface. Rebooting just led me to the same issue, though. I also checked the /boot/efi contents, and it *seemed* fine.

So I booted up to a live usb, installed boot-repair, ran that, and now I am stuck on a new issue, where booting leads me to a grub rescue shell, with the error message ```
file /boot/grub/x86_64-efi/normal.mod not found
```

I've got a boot-repair pastebin here: [https://paste.ubuntu.com/p/dhN5H5GKBw/](https://paste.ubuntu.com/p/dhN5H5GKBw/)

All of my files are still there and fine, so I'm very much considering just reinstalling completely, but it would be lovely to actually fix this.

---

