---
title: "Tried to install Nvidia drivers now blank screen."
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by Newy11 on 2013-11-30
Hi guys, 

I know this is covered a lot. But im in a bit of a different situation to most. 

Im running a fresh install of ubuntu 13.10 and I tried installing the Nvidia drivers from the nvidia website (before i knew there was a easier way to do it :P) It got to the point where it said it was disableing the nouveau drivers. It said to restart then try to install the Nvidia drivers again but everytime i restart it must be booting into a screen resolution that my monitor can not support.

I have tried hitting Shift before grub loads. nothing seems to happen. Or if it does i cannot see it.

I have tried hitting Ctrl - Alt - F1 and this does indeed work as i can log in and reboot BUT i can still not see what im typing. the whole screen is just blank.

I have a live CD that boots fine and just wondering if i can un-do what the nvidia drivers disabled from the live CD?

Thanks heaps..

---

### Post by mikewhatever on 2013-11-30
If you've managed to login and reboot without seeing the output, you can probably also cd to the directory with the Nvidia installation file, and run, ...for example, 'NVIDIA-Linux-x86-310.19.run --uninstall'. The file name may differ, but you should just type NV and then press Tab to auto-complete.

Source: [http://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers](http://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers)

---

### Post by Newy11 on 2013-11-30
Ended up just reinstalling everything as no matter what I tried nothing seemed to help :(

---

