---
title: "Editing grub menu"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by hojjat on 2012-04-27
I just upgraded my Ubuntu 11.10 to 12.04, and I had installed Ubuntu on LV with encryption. Now, it doesn't boot.

In grub menu, I have the options for "Ubuntu, with Linux 3.2.0.24-generic-pae" and the corresponding recovery mode, but none of them show me the screen where I'm supposed to type in the passphrase for encrypted volume.

I also have the option "Previous Linux version", under that, I have "Ubuntu, with Linux 3.2.0.24-generic" which works correctly.

I'm very upset that Grub menu is overwritten (I told it to keep the existing menu during upgrade, but it didn't listen). :mad:

Anyways, the solution for me seems to be that I have to modify the grub menu and move one of the submenus "previous linux version" options to the grub's main menua and make it default. I don't know how to do that and I couldn't find any tutorial that describes submenus in a clear way. Any advice is highly appreciated.

---

### Post by hojjat on 2012-04-27
Also, how can I get rid of these generic-pae linux images forever? I just want the generic ones, not the generic-pae ones.

---

