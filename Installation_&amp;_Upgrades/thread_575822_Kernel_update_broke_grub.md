---
title: "Kernel update broke grub"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by usarmykr on 2007-10-14
I installed kubuntu and updated it via adept.  When I rebooted (installed graphic driver) I saw the new kernel in the boot menu, with the last kernel.  my issue is that it auto selects the kernel unless I hit esc at boot to get the grub menu.  If I let it auto boot, I get the recovery mode, i think (its a black screen with only a text input, but i tried startx which didnt work) but when I select recovery mode from the grub menu I get into kubuntu proper.  Cant figure out the issue online, and am too new to linux to try things.

---

### Post by meierfra on 2007-10-14
Could you post your whole "menu.lst"  and the  output of "cat /boot/grub/default"

---

### Post by usarmykr on 2007-10-14
I found my issue, if I use the envy script to install nvidia drivers, I need to uninstall them before I install a new kernel, and then reinstall.

---

