---
title: "Change display for install from DVD install"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by MicahCarrick on 2007-05-10
Hello.

I'm installing Ubuntu 7.04 from the install/live DVD for AMD64. When it gets to the Gnome desktop, the install druid is too large for the window. The only resolutions available in the screen resolution applet are 640x480 and 800x600. I have an LCD panel which I run at 1280x1024 on my Fedora system. I set this using the "Display" application. However, I don't see this when I boot into the Ubuntu install/live DVD. Is there a way I can force this resolution for the install?

---

### Post by MicahCarrick on 2007-05-10
I was able to resolve this issue. For those who are curious:

1. Re-configured x-server accepting all default values:
```
sudo dpkg-reconfigure xserver-xorg
```

2. Due to a glitch with my nvidia adapter, turned off hardware cursor:
```
sudo gedit /etc/X11/xorg.conf
```
Under the "display" section, added:
```
     Option    "HWCursor"    "false"
```

3. Logged out using CTRL+BACKSPACE and logged back in as "ubuntu" with empty password.

4. Started installation, now with a screen resolution big enough to see the installation screens.

---

