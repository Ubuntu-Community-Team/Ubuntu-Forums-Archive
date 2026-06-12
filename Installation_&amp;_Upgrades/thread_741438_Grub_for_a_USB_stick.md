---
title: "Grub for a USB stick"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by madmagic on 2008-03-31
Ok heres what i have. A 4 gig usb stick partioned into 3, a 1gig ext3, 1gig fat32 and a 2gig fat32. For the ext3 i have Puppy Linux installed, for the 1 gig fat32 i have windows xp  boot files, the 2gig is empty. i install grub to the ext3 part, it boots from the stick goes to the menu, it sees the linux and windows drive. My problem is it keeps saying that the directory doesnt exist. Can any one help me edit the grub bootfiles? or have another option?

---

### Post by dstew on 2008-03-31
> My problem is it keeps saying that the directory doesnt existIs this a grub error you are getting? Post the error message. I don't know much about Puppy linux, but I assume it has a /boot/grub/menu.lst or grub.conf file. Can you boot a live CD and see the files on the USB stick? If so, post the contents of /boot/grub/menu.lst and the output of```
sudo fdisk -l
```entered into a terminal command line.

---

