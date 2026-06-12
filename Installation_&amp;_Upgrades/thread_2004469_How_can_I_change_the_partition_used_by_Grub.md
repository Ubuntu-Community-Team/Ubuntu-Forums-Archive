---
title: "How can I change the partition used by Grub?"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by Patriko_H on 2012-06-15
I've be running Ubuntu 10.4 and just installed 12.4 on another partition of the same drive. (10.4 on sda2, 12.4 now on sda6) I can select either system from the boot menu, both run fine. I needed to change the default start option, found I had to do it in on 10.4, not 12.4 (edit /etc/default/grub. run update-grub) But I now want to remove 10.4 on sda2 but I'm clearly running Grub from sda2, not from 12.4 on sda6. How can I change to using the Grub from sda6? Will running grub-install with the correct options do it?

---

### Post by drs305 on 2012-06-15
Boot into the Ubuntu installation you want to control Grub. Decide on the hard drive you want to control the boot (X). Run the following command from the desired OS:
```
sudo grub-install /dev/sdX
```
Example: sudo grub-install /dev/sda
Do NOT include the partition number

Reboot, making sure the BIOS is booting the correct drive first.

---

### Post by Patriko_H on 2012-06-16
Thank-you! that did the trick. I have some problems now with the video while displaying the menu and boot-splash but will deal with that separately.

---

