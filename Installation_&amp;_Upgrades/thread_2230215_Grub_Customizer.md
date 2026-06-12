---
title: "Grub Customizer"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by tonymoloney on 2014-06-18
Hi. I've been trying to install Grub Customizer and after all the shell commands, the program is installed, but when I try to run it, I get the following error "grub-mkconfig couldn't be executed successfully. error message:
 /usr/sbin/grub-mkconfig: 1: /etc/default/grub: s#: not found"

Any ideas?

---

### Post by oldfred on 2014-06-18
Did you use grub customizer to edit grub?

Post this:
       cat /etc/default/grub

If there is a typo or any issue then the grub update fails.

---

