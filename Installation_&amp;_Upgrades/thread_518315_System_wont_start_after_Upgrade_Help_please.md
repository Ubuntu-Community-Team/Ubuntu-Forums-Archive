---
title: "System wont start after Upgrade Help please"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by spender63 on 2007-08-05
I installed abunch of updates and the next time I started my computer these are the errors i received. I cannot get into UBUNTU at all please help me

INIT:etc/event.d/tty1:13unknown stanza
INIT:etc/event.d/tty2:13unknown stanza
INIT:etc/event.d/tty3:13unknown stanza
INIT:etc/event.d/tty4:13unknown stanza
INIT:etc/event.d/tty5:13unknown stanza
udevd[1976]:add_to_rules:PHYSDEV*values are deprecated and will be removed from a futer kernel please fix it in /etc/udev/rules.d/40-permissions.rules:17
udevd[1976]:add_to_rules:PHYSDEV*values are deprecated and will be removed from a futer kernel please fix it in /etc/udev/rules.d/40-permissions.rules:45
udevd[1976]:lookup-group:specified group 'nvram' unknown
udevd[1976]:udevd_rules'_init: could not read '/etc/udev/rules.d/60-libpisock.rules': no such file or directory
udevd[1976]: add_to_rules_: do not reference parent sysfs directories directly, that may break with a future kernel, please fix it in /etc/udev/rules.d-65 persistent- storage' .rules:12
*activating swap...
*checking root file system...
fsck 1.40- WIP ( 14-NOV-2006)
/dev/hda1:clean, 193900/4718592 files  2710189/9426130 Blocks
checking file systems
 fsck 1.40- WIP ( 14-NOV-2006)

---

### Post by Pumalite on 2007-08-05
Plug in your Live CD and check your /boot/grub/menu.lst and your /etc/fstab for changes, especially 'root' (hd0.0?)

---

### Post by spender63 on 2007-08-05
sorry i am a nubie could you tell me slower. Once I am at the terminal i type in what line? /boot/grub/menu.lst  ?

---

### Post by Pumalite on 2007-08-05
You have to chroot into your system: sudo chroot /dev/??? If you have trouble with the Live CD, download yourself a Knoppix Lice CD. It mount systems automatically.

---

