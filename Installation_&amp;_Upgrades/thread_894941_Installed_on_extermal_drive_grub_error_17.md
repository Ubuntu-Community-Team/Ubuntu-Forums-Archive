---
title: "Installed on extermal drive: grub error 17"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by Rahu on 2008-08-19
I just tried installing ubuntu on an external drive for the first time.

The install went fine and now selecting the external drive from my BIOS's boot menu brings up grub. When I select ubuntu to boot I get error 17: unable to mount selected partition.

I'm guessing the cause of this is that when booting from the external, that becomes hd0 rather than hd1.

I'm new to messing with grub so I'm just looking for a way to change the grub installed on the external drive to point to hd0 rather than hd1 without touching the internal drive's bootloader.

Thanks for any help.

-Jeff

EDIT: Figured it out. I just wasn't sure it would find my menu.lst without chrooting the drive from the live cd but it did. All is well now :)

---

