---
title: "Strange problems after Ubuntu 11.10 install"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by Oldhacker on 2011-10-16
Having been running 64 bit Ubuntu 10.04 for some time, I downloaded the latest Ubuntu 64 bit 11.10 and let it do the default side by side install with my old OS. It installed, but when I go to the grub menu, there are FOUR identical entries for 10.04 and all of them only produce a lockup.

Hopefully, I can find a way to access my old OS as well as the new one.

Also, at shutdown 11.10 left the NUMLOCK light glowing on my keyboard, even though the desktop appeared yo shut off normally.

Any knowledgeable suggestions are welcome. Aside from these two problems, I think that I can get used to the switch from the old desktop.

---

### Post by gordintoronto on 2011-10-16
This might not work, but it's worth a try. In 11.10, open Terminal and enter the command:
sudo update-grub

---

### Post by gordintoronto on 2011-10-16
This might not work, but it's worth a try. In 11.10, open Terminal and enter the command:
sudo update-grub

---

### Post by Oldhacker on 2011-10-16
Your suggestion DID work! Thank you very much.

A couple of things are worth mentioning: There are now FIVE identical entries in the boot menu for Ubuntu 10.04 I tried them all and they all work the same. However, they only respond to an old login password, which I had changed in 10.04 and am now using the new password in 11.10 as well.

The next step will be for me to remember how to edit the GRUB menu to get rid of all of the extraneous material.

---

