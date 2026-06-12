---
title: "[SOLVED] 8.10 install black screen"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Cellwind929 on 2008-10-30
Trying to do a fresh install of 8.10. 2.6 p4 celeron on an old mobo with intel integrated graphics. I go to do the live desktop to grab some files off the disks before I reformat and it gets to a black screen with the pointer that I can move, but nothing else. This leads me to believe that X is started but is dying out somewhere. I'm not sure what I can do to resolve it. Is there a command I can run? ctrl+alt+f1 does nothing. All I need to do is be able to install and I don't need compiz and stuff.

---

### Post by andrewwg94 on 2008-10-30
> **Cellwind929 said:**
> Trying to do a fresh install of 8.10. 2.6 p4 celeron on an old mobo with intel integrated graphics. I go to do the live desktop to grab some files off the disks before I reformat and it gets to a black screen with the pointer that I can move, but nothing else. This leads me to believe that X is started but is dying out somewhere. I'm not sure what I can do to resolve it. Is there a command I can run? ctrl+alt+f1 does nothing. All I need to do is be able to install and I don't need compiz and stuff.

same here, they need to fix this quick

---

### Post by Cellwind929 on 2008-10-30
Hit f4 and arrow down to safe graphics, try booting with that. I got it to boot into a desktop, not sure if I should install on it though.

edit:640x480 is so small that I cannot see the "next" button to install in the install dialogue.

---

### Post by Cellwind929 on 2008-10-30
Ubiquity boots up fine, safe mode starts up fine. Quiting ubiquity and waiting for the live session to start up yields the Ibex wallpaper with an arrow pointer I can move instead of a black background.

Edit: Graphics chipset is 82845G/GL integrated intel

This launchpad bug looks to be it: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/277699](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/277699)

---

### Post by Cellwind929 on 2008-10-31
The problem with X was compiz. I installed, dropped to console, then did a sudo apt-get remove compiz compiz-core.

Restart and things work fine.

---

