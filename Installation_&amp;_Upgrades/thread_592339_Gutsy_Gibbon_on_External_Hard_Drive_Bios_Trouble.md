---
title: "Gutsy Gibbon on External Hard Drive Bios Trouble"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by audiofreq on 2007-10-26
Hi,

My bios supports booting from USB and i have successfully installed Ubunutu 7.10 on it.

The problem is when booting grub is loaded, but then i can't read vmlinuz due to Error:18. I can't remember the specific words but it's like "cylinder exceeds maximum supported by bios". (using "kernel /vmlinuz root=/dev/sda ro vga=791" - when you hit tab to autocomplete directory you can see that vmlinuz is actually there)

I tried another fresh install but this time when i hit "advanced" before ready to install i changed the location for grub from (hd0) to /dev/sda

Still i get the same problem so after looking around I figured i'd try changing the mode of the drive to LBA or Large to experiment.

However, when i looked in the bios under the list of ide hdd (the only place it could possibly get listed) it's not actually detected.

I have an AWARD bios and am confused as to how it finds grub if the bios doesn't show that it's detecting the hard drive.

Does anyone have any ideas?

Thanks in advance.

---

### Post by audiofreq on 2007-10-26
Anyone?

---

