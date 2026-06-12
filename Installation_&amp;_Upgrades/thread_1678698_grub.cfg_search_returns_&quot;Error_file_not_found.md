---
title: "grub.cfg search returns &quot;Error: file not found&quot;"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by billstei on 2011-01-30
After installing Ubuntu Lucid 10.04.1 grub briefly shows a message "Error: file not found" before the list of bootable OS's appears.  Note that there is *no* error number (like Error 15 or similar) and that this error does not stop grub from running, and the OS bootable choices all work fine.  I have narrowed the error message down to this line in /boot/grub/grub.cfg (at approximately line #34):

search --no-floppy --fs-uuid --set 9954c8e0-f547-463c-a7be-50b7d38368d1

This line is in the /etc/grub.d/00_header section of grub.cfg.  Note that this line is present regardless of whether GRUB_DISABLE_LINUX_UUID is set true or not.  A list from: ls -l /dev/disk/by-uuid shows that the uuid is correct for device sda1, which is where Ubuntu Lucid root resides.  I suppose I could hunt down the source code for the "search" module of grub to find out what produces this message -- a more verbose answer concerning "What file?" would be helpful (search --verbose ?).  Or perhaps I should just disable 00_header (or is that not possible, or fatal? ).

---

