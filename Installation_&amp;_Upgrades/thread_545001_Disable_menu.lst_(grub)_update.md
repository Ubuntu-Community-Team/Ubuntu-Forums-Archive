---
title: "Disable menu.lst (grub) update"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by gaiterin on 2007-09-07
Hi.
I installed Ubuntu to a friends.
In two installs I had to modify the file menu.lst of grub, in an occasion to disable acpi because he didn't have connection with it (it's a old motherboard), and in another one, after moving the partition, changing the device (hda2 to hda1).

The problem is that the Ubuntu's updates MODIFY this file, receiving called from these friends, without Internet connection or without boot computer.

I readed that enable the line of menu.lst "groot", and specifying the device that contains Ubuntu it disable the updates, but it didn't work, continues updating this file.

How I can disable that grub update?
Thank you very much.
Marks.

---

### Post by Warren Watts on 2007-09-07
My suggestion would be to make a backup copy of menu.lst (call it menu.lst.bak or something similar).  Then when a kernel update modifies the menu.lst, all you have to do is copy your  list of OS's back into the new menu.lst.

---

### Post by gaiterin on 2007-09-07
The problem is that my friends are newbie with computers.
I like disable the update, then I will not need go to their house, for only edit one line in the file.

In one case, the computer not boots! Imposible do a script for repair the menu.lst.

---

