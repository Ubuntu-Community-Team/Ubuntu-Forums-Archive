---
title: "Nothing showing after X installation"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by andrewheiss on 2007-06-19
Newbie here!

I just installed Feisty Server to get a LAMP server set up and it went smoothly and quick and great. However, this is my first foray into Linux, so I wanted the GUI. I found online that I'm supposed to do sudo apt-get install ubuntu-desktop or something to install the GNOME desktop.

It installed just fine - no errors. However, after restarting the computer to boot into the desktop mode, I can't get anything to show on my monitor, like the video card never installed. The sound works--I even logged in blindly, but couldn't do anything.

I then used an old 6.06 CD to boot as a live CD to see if my video card is supported (it's integrated in an old Compaq smallform box), and it worked just fine. 

How can I get the GUI desktop to work? How can I leave the blank screen GUI and get to the shell to fix it?

Thanks!

---

### Post by angryfirelord on 2007-06-19
First, in case something went awry, do a ```
sudo apt-get install gdm
```

If that doesn't work, or is already installed, then see if pressing Ctrl+Alt+F1 will get you into a terminal.

If it does, type ```
sudo nano /etc/X11/xorg.conf
```

Look for something called *Section "Device"*. Change the thing in front of Driver to say "vesa". Reboot and attempt to log in again.

On a side note, if you want a GUI, you may as well use the desktop or alternate cd.

---

