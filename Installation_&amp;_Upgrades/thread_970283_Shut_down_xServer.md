---
title: "Shut down xServer"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by Anharath on 2008-11-04
Hi,
I'm trying to install my ATI-driver, downloaded from the official ATI website. But I'm having some problems with shutting down my Xserver, I'm trying to install the driver as root but I can't acces the CLI..
I've tried Ctrl+Alt+Shift+F[1-6] but that didn't work.. (I've got this shortcut-keys from a friend that uses Ubuntu)
Is this a different shortcut in Xubuntu or something?

Greets
Anharath

---

### Post by mikewhatever on 2008-11-04
None of these shortcuts shuts xserver down. You have to run <sudo /etc/init.d/gdm stop>.

---

### Post by Archmage on 2008-11-04
To acces the CLI you should enter CTRL+ALT+F1 (or F2, F3, F4, F5 or F6). The X-Server is normaly under CTRL+ALT+F7.

---

### Post by Anharath on 2008-11-05
> **Archmage said:**
> To acces the CLI you should enter CTRL+ALT+F1 (or F2, F3, F4, F5 or F6). The X-Server is normaly under CTRL+ALT+F7.
Ok thanks ^^!!

Greets

---

