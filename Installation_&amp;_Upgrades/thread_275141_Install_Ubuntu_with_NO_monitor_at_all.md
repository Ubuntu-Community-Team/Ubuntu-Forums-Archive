---
title: "Install Ubuntu with NO monitor at all"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by motin on 2006-10-10
I have an old P3 450mhz computer with no working graphic card lying around, and I am going to attempt to install Ubuntu on it without plugging no monitor to it whatsoever, only remote desktop... I have a plan but don't know if it is worth trying, maybe you can help?

This is my strategy:

1. Put the desktop-iso install/live CD in the drive and let it boot
2. (Should be at boot-menu) Press Enter
3. Wait until it starts up and hopefully gets connected to my network through DHCP
4. Press Alt->F2 and run "gnome-terminal"
5. Execute "gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true"
6. Log on through my laptop to the computer in Live CD mode
7. Install Ubuntu to the hard-drive and reboot
8. Wait a while for login screen and log-in
9. Press Alt->F2 and run "gnome-terminal"
10. Execute "gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true"
11. Connect via remote desktop again and configure the hell out of it :)

Any noticable flaws or suggestions? I know Murphys law is going to play a significant role here, but it is worth trying isn't it?

Is there a even better way to do this, like via PXE or similar?

---

### Post by mssever on 2006-10-11
Sounds like it might work. You could also try the alternate install CD if you can find a good set of screenshots. Once you install, you can install and use SSH for just about everything. SSH was much easier for me to get working than any kind of remote desktop.

---

