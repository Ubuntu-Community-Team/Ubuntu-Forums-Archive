---
title: "Delete temporary GRUB"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by mediodude on 2011-07-18
Hello i have a question. My pc (dell studio 15) needs to go to dell because i have some problems with my screen now i dont want that they see that i have also a dual boot windows and ubuntu so is it possible that i delete the grub boot screen so its going straight to Windows 7?
And how can i do this? 
Thanks in advance!

Bye,

Mediodude

---

### Post by dino99 on 2011-07-18
boot on ubuntu, then :

sudo synaptic

there, search "grub" and remove/purge all the "grub" packages installed

on next reboot it will boot on win7. If not, then reinstall the win bootloader with its livecd (have you one ?)

---

