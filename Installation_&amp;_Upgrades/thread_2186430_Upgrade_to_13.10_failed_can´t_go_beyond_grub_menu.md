---
title: "Upgrade to 13.10 failed: can´t go beyond grub menu"
date: 2013-11-07
forum: Installation &amp; Upgrades
---

### Post by Pablo W on 2013-11-07
Hi, Forum.

When upgrading from Ubuntu 13.04 to 13.10 in my PC, the installation process got "frozen". After a hard restart, I've reached the grub menu and can´t go beyond it. 

What I’ve already tried: Out of the options in the grub menu, if I chose to start Ubuntu normally I get the following message “Filesystem check or mount failed. The maintenance shell will now be started. CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further erors will be ignored
boot@pablo-HP-Compaq-dc-7700-Small-Form-Factor:&#8764;#  

If I chose the Ubuntu advanced options, I get the possibility to start from 3.8.0-31-generic (recovery mode). This brings me to a new set of command options (resume, clean, dpkg, failesafeX, fsck, grub, and other). Before messing around with these and turning things worse, I wonder if you could provide me some guidance to find the way to restart 13.04 and finish the upgrading process properly.

Thank you!

---

### Post by Pablo W on 2013-11-07
Update: the message I get when trying to perform 'clean' 'fsck' or ' dpkg' commands in recovery mode is the following:

lib/recovery-mode/recovery-menu: line 76: /etc/default/rcS: the file or directory does not exist

Any hint on how to go on? Thanks

---

### Post by Pablo W on 2013-11-08
24 hs after the incident, here comes a new update: I've tried all kernel versions available from the grub 2.0 menu (from 3.8.0-31-generic to 3.2.0-49-generic-pae) to no avail. I've also tried 

```
dpkg --configure -a
``` but I get stuck with the message lib/recovery-mode/recovery-menu: line 76: /etc/default/rcS: The file or directory does not exist.

Any kind of constructive feedback would be much appreciated.

---

