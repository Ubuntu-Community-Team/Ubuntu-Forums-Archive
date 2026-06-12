---
title: "Wubi installation migration"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by anovalberto on 2010-11-23
Hello Ubuntu community, i have a question. I have changed my computer, where i had a wubi ubuntu installation. I have saved the whole C:/Ubuntu folder, and now i want to use this installation in my new computer. Both computers are Windows XP. Which are the steps to follow?

Thanks.

---

### Post by bcbc on 2010-11-23
I assume you want to keep using wubi? If that's not the case let me know.

To reinstall on new computer:
Install the same version of ubuntu using wubi on the new computer using the standard method - give it a small size (e.g. 4GB since we'll be replacing it). Reboot into it to complete install, reboot a second time, this time when you see the grub menu, press 'e' and note the drive designation:
you're looking lines similar to the following:
set root=(hd0,2)
and
/dev/sda2

These show the partition you installed Ubuntu on for the NEW computer.

Then... 
Delete the new root.disk and copy in all the backed up *.disk files from the old computer (in c:\ubuntu\disks). Reboot and select Ubuntu, when you see the grub menu, press 'e' again.
Delete the line that says 'search --no-floppy ... --set xxxxxx' 
Make sure you see the same lines with the correct partition designation. If not, edit them to what you found initially.
Press CTRL-X to boot.

Once booted, run "sudo update-grub" from a terminal prompt (CTRL-ALT-t) to correct the 'search' line with the new UUID and update the partition designation.

PS these instructions are for Ubuntu versions 9.10 and later. It's different if you're using grub-legacy (9.04 and earlier)

---

