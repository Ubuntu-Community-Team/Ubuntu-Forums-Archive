---
title: "[SOLVED] Installing Windows XP/Partitioning"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by talking Llama on 2008-08-29
I've installed Ubuntu 8.04 (Hardy), had it installed for 6-ish months now, and I want to re-install Windows XP, for certain reasons, in a partition. How would I go about doing this? Thanks to anyone who helps out.

---

### Post by Pumalite on 2008-08-29
Make sure is a primary partition, preferably sda1. Save all your data in Ubuntu. The other way is this:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
Make sure you don't install Windows in a logical partition.

---

### Post by talking Llama on 2008-08-29
I got to page three, but I'd already installed the Partition Editor so didn't have to use the Live CD but when I open it up and right click on my main partition (SDA 1) it doesn't give me any of the options. I can only chose: Unmount, Manage Flags and Information.

---

### Post by Too Late on 2008-08-29
> **talking Llama said:**
> I got to page three, but I'd already installed the Partition Editor so didn't have to use the Live CD but when I open it up and right click on my main partition (SDA 1) it doesn't give me any of the options. I can only chose: Unmount, Manage Flags and Information.
You cannot modify mounted partitions (i.e. partitions which are in use). LiveCD won't mount anything by default (maybe swap, I don't know). But you can still unmount that partition by simply selecting the unmount option, assuming, that the partition you want to unmount is not the root partition.

---

### Post by Pumalite on 2008-08-29
That's why is better to work with Gparted Live CD.(unmounted drives/partitions)

---

### Post by talking Llama on 2008-08-31
Thank you! This method worked great. Now I can dual-boot! Thanks! ^-^

---

