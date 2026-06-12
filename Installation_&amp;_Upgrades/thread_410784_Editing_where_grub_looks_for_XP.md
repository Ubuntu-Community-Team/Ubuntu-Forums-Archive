---
title: "Editing where grub looks for XP"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by Quby on 2007-04-16
I want to dual boot ubuntu, but i remember that grub only searches for windows in its default directory
C:/WINDOWS
however, this is not the case for me.. my directory is in C:/WINDOWS/WINDOWS because when windows had a problem i thought of writing another windows in a new folder instead of overwriting or reformating

anyway.. what do i do so that i may tell grub to look in C:/WINDOWS/WINDOWS for XP so that it may be dual booted if i wish to do so, and where may i find the files to edit grub?

---

### Post by thelinuxguy on 2007-04-16
/boot/grub/menu.lst

---

### Post by bulldog on 2007-04-16
Don't think this is necessary.
GRUB only points to the partition,not a folder.
If you can boot windows from it's own bootloader,you can boot windows with GRUB.

If I'm not mistaken,the windows boot.ini file should provide the actual boot for your windows.

---

### Post by thelinuxguy on 2007-04-16
> **bulldog said:**
> Don't think this is necessary.
GRUB only points to the partition,not a folder.
If you can boot windows from it's own bootloader,you can boot windows with GRUB.

If I'm not mistaken,the windows boot.ini file should provide the actual boot for your windows.

Yeah. I missed that completely. If your Windows folder has changed in the **same partition** then an update to boot.ini should be fine. But Windows will do that anyway when you install. So basically as long as you reinstall windows into the same partition, you don't need to edit Grub entries. You will just need to reinstall Grub after that because Windows installation will overwrite it.

---

### Post by Quby on 2007-04-16
okay thanks.  I'm going to install ubuntu today then :)

---

