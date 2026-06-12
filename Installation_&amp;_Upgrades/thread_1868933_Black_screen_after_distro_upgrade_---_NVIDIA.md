---
title: "Black screen after distro upgrade --- NVIDIA"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by runeh76 on 2011-10-25
Hi guys!

I solved my problem and wanna share it.
So i upgrade 10.10 to 11.04 and after reboot i got black screen with blinking cursor. I have Nvidia graphic-card.

This is what i did:

-hit ctrl+alt+del (reboot)
-choose safe graphic mode
-Go to synaptic package manager and search NVIDIA
-delete all Nvidia results and XSERVER-XORG-VIDEO results.
-open terminal and write
```
sudo apt-get install nvidia-current
```
-reboot and everything should be ok.

---

