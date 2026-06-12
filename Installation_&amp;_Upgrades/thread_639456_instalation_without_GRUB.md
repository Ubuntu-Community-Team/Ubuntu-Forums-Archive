---
title: "instalation without GRUB"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by lulon on 2007-12-13
Hi!

I've installled Ubuntu 7.10 with Windows XP in the same computer.

I have one partition with Windows XP. 75GB
I have other primary partition for path directory ("/"). 3GB
I have other extended partition. 2GB
In this primary partition I have 1GB for SWAP and the rest for /HOME

The instalation has finished well, but the GRUB hasn't been installed, and when I restart the computer, Windows is initiated.

¿Why? ¿What could I do for install GRUB?

Thanks a lot.

---

### Post by logos34 on 2007-12-13
> **lulon said:**
> The instalation has finished well, but the GRUB hasn't been installed, and when I restart the computer, Windows is initiated.

Try pressing 'ESC' key immediately after Bios POST on startup.  If grub menu screen doesn't come up, then it probably did not write to the mbr.  In which case boot from the live cd and check your menu.lst file.

Click on the root partition to mount...it should do so at '/media/disk'.  Then, 

$ cat /media/disk/boot/grub/menu.lst

Post it.

The 'default' line near the top should say '0'.

The 'timeout' set for '10'.

and hiddenmenu disabled.

#hiddenmenu

If everything looks correct, try [reinstalling grub to mbr.]("http://ubuntuforums.org/showthread.php?t=224351")

---

