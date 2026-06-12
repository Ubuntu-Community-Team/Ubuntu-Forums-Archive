---
title: "Change GRUB boot order"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by cruiser891 on 2011-08-15
I have ubuntu 11.04 and windows vista installed on my pc. I have already set windows vista as my default os, but I'd like to put it at the top of the boot menu (currently it's in 4th). How do I do that???:confused:

---

### Post by YesWeCan on 2011-08-15
Hi there.
Go to /etc/grub.d/ and you'll see a file named '30_os-prober'. Rename it '09_os-prober' (to give it a lower number than 10_linux').
Then sudo update-grub
You'll have to change the default menu entry number again.

---

### Post by cruiser891 on 2011-08-15
Thanks a lot! Just a quick tip for those that might want to do this: you need to have root privileges to rename the file.

---

