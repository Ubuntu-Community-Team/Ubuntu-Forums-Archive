---
title: "login screen freeze after update"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by FalacyNine on 2011-02-19
Hi all, 

so I updated to a new build (I don't know if that is actuaaly what its called), and now my comp freezes everytime after I put in my password to load the system. from the grub menu i can load the previous build and it starts up just fine. Any thoughts why/how to fix it. by build i mean its the same ubuntu version 10.10, but the grub menu has 3 different builds for my system.


Thanks in advance everyone.

---

### Post by dino99 on 2011-02-19
booting into recovery mode from grub menu (hold "shift" key down at end of bios process if grub menu is hidden (normal if only 1 OS))  

then into a terminal:

sudo rm /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

close then reboot to know if its better

---

### Post by FalacyNine on 2011-02-20
the only xorg.conf file i have is located in 

/usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf

i tried the rest of the commands to no avail.

EDIT: i type in my password, hit enter, it thinks for a second while I am able to move the mouse, then it hangs, mouse freezes, and stops loading/processing information.

Can I delete the latest build somehow, and try to re-update after?

---

### Post by FalacyNine on 2011-02-21
Found solution.

for some reason the graphics card on my netbook wouldnt support some of my compiz settings (even though it for the past few months).

in grub, enter recovery mode,
enter root

sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit

then restart system

---

