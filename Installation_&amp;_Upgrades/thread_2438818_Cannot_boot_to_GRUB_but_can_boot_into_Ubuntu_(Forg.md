---
title: "Cannot boot to GRUB but can boot into Ubuntu (Forgot Admin pass)"
date: 2020-03-18
forum: Installation &amp; Upgrades
---

### Post by aseferfan on 2020-03-18
I forgot my admin password and normally I could reset it via GRUB menu but unfortunately I have actually disabled the autostartup of the menu at boot via 
sudo nano /etc/default/grub

and changing 
GRUB_HIDDEN_TIMEOUT=0

now I tried holding shift but it doesn't boot into the grub menu, boots up straight to ubuntu, I cannot change grub.cfg either as it requires admin password:(

is there anyway to edit grub.cfg externelly? thanks

---

