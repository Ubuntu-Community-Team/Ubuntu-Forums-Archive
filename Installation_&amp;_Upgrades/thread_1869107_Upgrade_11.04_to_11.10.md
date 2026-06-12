---
title: "Upgrade 11.04 to 11.10"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by runeh76 on 2011-10-25
Hi guys!

So i upgrade today 11.04 to 11.10 and i got problems.
Boot hangs black screen by few white-font words..
I can only enter to graphic-mode by hitting ctrl+alt+F1 and type startx. Second problem..i dont have working network anymore..


(I reinstalled Nvidia-drivers earlier)

What should i try?

Thx!

---

### Post by dino99 on 2011-10-25
sudo rm /etc/X11/xorg.conf

sudo synaptic
- purge all nvidia & jockey installed packages
- reinstall nvidia-current, nvidia-settings & jockey-gtk

log out and reboot

check driver activation (sudo jockey-gtk)

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

### Post by runeh76 on 2011-10-26
Will try that! How about my network? When i looked network manager, i couldnt change any settings there.

Thank you!!

---

