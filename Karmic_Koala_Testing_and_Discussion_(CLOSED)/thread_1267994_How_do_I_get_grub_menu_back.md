---
title: "How do I get grub menu back?"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by infamousrev on 2009-09-16
After recent updates it skips straight to booting the first kernel.
 
However that process instantly fails and leaves me without a command prompt.
 
I tried pressing esc as fast as I can during the entire boot process but it wont go to grub.
 
Any ideas?

---

### Post by drs305 on 2009-09-16
With Grub 2, try holding down the SHIFT key during boot. That is written into the boot script to display the menu.

For a guide to Grub 2, check the link in my signature line.

If that doesn't work, you can edit the settings in /etc/default/grub. After making the changes, don't forget to run "sudo update-grub".  How to do it is explained in the guide.

---

