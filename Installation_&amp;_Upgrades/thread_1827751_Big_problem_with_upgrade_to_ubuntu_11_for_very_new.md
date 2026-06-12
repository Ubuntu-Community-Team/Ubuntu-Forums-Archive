---
title: "Big problem with upgrade to ubuntu 11 for very new linux user."
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by sfjhackett on 2011-08-18
Hi,

I am a complete novice at Ubuntu (I had it for a week before I had this problem) so please can I have any help assuming I am completely incompetent.

I installed Ubuntu 10 on a separate partition on an Asus EEE leaving a dual boot system. It worked fine until it tried to upgrade to Ubuntu 11.04 (not sure about the.04). It said that installation was successful yet when I start it I get the background with no panels of any kind. Saying this, if I insert a usb flash drive the window comes up and I can access and "run" files. I have tried every variation of alt,tab,ctrl and F..s I can think of with no success in accessing any programs.

I have looked through the forums but can't find this exact problem (I am probably searching using the wrong key words) so please re-direct me or help me here and accept my apologies for wasting your time if this problem is in another thread.

Thanks

Simon

---

### Post by dino99 on 2011-08-18
hi simon & welcome,

boot in recovery mode: 
hold "shift" key down at bios end process to get the grub menu, then select the 2d line (recovery mode).

 You will get a prompt for running command:
- sudo apt-get update
- sudo apt-get install -f
- sudo apt-get install --reinstall ubuntu-desktop

- sudo rm /etc/X11/xorg.conf
- sudo dpkg --configure -a

then reboot

---

