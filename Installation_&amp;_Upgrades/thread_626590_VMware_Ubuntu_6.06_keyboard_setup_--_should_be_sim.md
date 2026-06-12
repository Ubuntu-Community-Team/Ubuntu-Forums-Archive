---
title: "VMware Ubuntu 6.06 keyboard setup -- should be simple"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by mikecrowe on 2007-11-29
Hi folks,

I have a VMWare virtual machine I'm trying to install.  It is the 3rd VM on this particular machine.  Other 2 work fine.

The keyboard is acting funny:  / is mapped as -, etc.  

Since the other two machines work fine, I think there is something in this linux distro telling it to map the keyboard incorrectly.  I tried looking where 7.04 has the keyboard (/etc/default/console-setup), but that doesn't existing in 6.06.

How did 6.06 control the keyboard layout?

TIA
Mike

---

### Post by mikecrowe on 2007-11-29
install-keymap /usr/share/keymaps/i386/qwerty/us.kmap.gz

---

