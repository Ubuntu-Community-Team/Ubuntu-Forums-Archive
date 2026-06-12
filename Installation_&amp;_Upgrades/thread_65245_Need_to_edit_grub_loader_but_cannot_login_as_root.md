---
title: "Need to edit grub loader but cannot login as root"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by Waxer on 2005-09-13
Hello all, I need to login as root to edit the grub loader, or find a method to do so, so that Windows XP is loaded by default (the missus wants familiraity!)

When I edit it logged in as me it says it cannot save changes, but when i did the install it did not offer me the choice of creating a root account.

It's a clean install with no apps/e-mail etc, so maybe i should reinstall...any suggestions?  Thanks a lot....

---

### Post by mlomker on 2005-09-13
The root password is the same as the user that you created.

Try:  **sudo gedit /boot/grub/menu.lst** at a terminal prompt.

---

