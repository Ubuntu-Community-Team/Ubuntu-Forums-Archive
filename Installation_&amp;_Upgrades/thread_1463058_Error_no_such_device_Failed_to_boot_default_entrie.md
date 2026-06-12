---
title: "Error: no such device: Failed to boot default entries."
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by jkb609gi8 on 2010-04-26
I have downloaded 9.10, burnt it to a CD, checked it with the program that came with live cd 9.10, formatted the whole hard-drive for 9.10; However when I reboot I get the following message.

**Error: no such device: lbe3d364-8e05-48d8-boo7-c49960676ac9 Failed to boot default entries. **

---

### Post by Charlietje on 2010-04-26
Hi,

When you boot and don't have a grub menu, press esc
If you have a grub menu, edit the default entry

your default entry will show something like

```
linux /boot/vmlinuz-2.6.31-11-generic root=UUID=cb201140-52f8-4449-9a95-749b27b58ce8 ro quiet splash
```

change root=UUID... to root=/dev/sda0 where you fill in the partition where your root system is installen.


when you have succesfully booted,
edit the grub menu and remove the "search" line, example:
```
search --no-floppy --fs-uuid --set cb201140-52f8-4449-9a95-749b27b58ce8
```

and change root uuid again to /dev/xx



regards

---

