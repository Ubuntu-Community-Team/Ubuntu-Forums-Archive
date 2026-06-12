---
title: "Installation Help"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by dcf-joe on 2008-04-27
Okay, let me clarify everything, it might help resolve my issue.

I went online to download the Wubi installer. I installed it and ran the program. I let Ubuntu use 30 GB, I chose the Ubuntu desktop manager, and I set my login name and password. I saw that it needed to download about 700 MB of stuff, so I left my computer alone for two hours. I came back, and all it told me to do is restart. So I restarted into Vista, and then restarted again so that I could choose to go into Ubuntu.

Ubuntu and Vista both appear on my bootscreen. I chose Ubuntu, and then it loaded the splash screen. Right before the splash screen appears, a message appears on the top telling me something about a bug with some type of timer and an ACPI problem. And then, it goes into a BusyBox terminal with an inframstr thing. It just sits there, waiting for me to type something in. People have told me to wait 15 minutes. I waited 30 minutes, nothing happens.

Oh yeah, for the record, I have already edited one of the boot options by typing in "irqpool," like I was told by the Wubi forums to do, to no avail.

Are there any suggestions??? I hope this clarifies the problem.

---

### Post by Rocket2DMn on 2008-04-27
At the GRUB boot menu, press "e" on the kernel you want to boot from (usually the first option) so you can edit it.  Select the second line, it starts with "kernel" and press "e" again.  To the end add another option "acpi=off".  Escape from there and press "b" to boot.

Once you get into Ubuntu, you can make this permanent by adding the option GRUB's menu.lst file
```
gksudo gedit /boot/grub/menu.lst
```
Scroll down to the kernel entry and change it to something similar to
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d88c93a3-4af3-4cd0-824e-8d5c172afc47 ro splash acpi=off
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```
Note that I added acpi=off to the kernel line again, and added a line "savedefault" - this will keep the changes from being erased during upgrades later.  Do NOT copy and paste that since my UUID is going to be different than yours.

---

