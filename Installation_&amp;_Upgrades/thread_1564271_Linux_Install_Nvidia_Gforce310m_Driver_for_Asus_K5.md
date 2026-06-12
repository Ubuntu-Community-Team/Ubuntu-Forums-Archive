---
title: "Linux Install Nvidia Gforce310m Driver for Asus K52 Laptop"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by kara_iran on 2010-08-30
Hi all
i have a laptop asus series k52 . and model k52jc . ubuntu installed on my laptap .But when the graphic drive fully installed. system restarting. After restarting the black page is displayed. Where is the problem? i don't known ..

I went this route . and i download NVIDIA driver , And I use this 
guide , but Problem still not resolved 
```
http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html
```

Again no answer .
I am very sad  :(:(

---

### Post by dino99 on 2010-08-30
better to use the ubuntu genuine packages you can find into synaptic:

boot into recovery mode (hold "shift" key down at end of bios process to see grub menu, if its hidden), edit the boot line, remove "quiet splash" and add video=nv, then boot

into a terminal:
sudo rm -f /etc/X11/xorg.conf

then with synaptic: remove/purge (right click ) each installed nvidia packages, then install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

reboot and check driver activation: system admin hardware driver (nvidia-current might be activated)

---

### Post by kara_iran on 2010-08-31
> **dino99 said:**
> better to use the ubuntu genuine packages you can find into synaptic:

boot into recovery mode (hold "shift" key down at end of bios process to see grub menu, if its hidden), edit the boot line, remove "quiet splash" and add video=nv, then boot

into a terminal:
sudo rm -f /etc/X11/xorg.conf

then with synaptic: remove/purge (right click ) each installed nvidia packages, then install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

reboot and check driver activation: system admin hardware driver (nvidia-current might be activated)
how to remove "quiet splash" on recovery mode ? i don't understand .
1-I do it fast. Do after installing Ubuntu
2-how to remove "quiet splash" on recovery mode ?. Where is it .i don't understand

---

