---
title: "Cannot Display Video Mode--confusing problem help please!"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by kyrinae on 2010-03-09
I currently have Windows 7 Ultimate installed, and to keep the boot manager for windows I decided to make a small partition for Ubuntu, and install 9.10 into the drive (which I named U:) and installed it by means of Wubi. Everything went fine past the first reboot, and the rest of the installation I can't see because it shows the gray ubuntu symbol in the middle of the screen for a few seconds then goes to a black screen saying "cannot display this video mode". I have tried everything I could find but "sudo dpkg-reconfigure xserver-xorg" doesn't work on Karmic.

I have tried everything I could find online, and the only thing that even worked a little was "sudo nano /etc/x11/xorg.conf";however, it was blank. I could not get "sudo gedit /etc/x11/xorg.conf" to work so I made it "sudo nano gedit /etc/x11/xorg.conf" for the heck of it and it came up ```
(gedit:1555) Gtk-WARNING**: cannot open display
```

Help please? I can edit it anyway, if you have an idea that means going into the drive and making a file, please tell me. I will try anything at this point.

---

