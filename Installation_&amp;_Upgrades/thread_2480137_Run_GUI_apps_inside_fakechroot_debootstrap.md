---
title: "Run GUI apps inside fakechroot debootstrap"
date: 2022-10-20
forum: Installation &amp; Upgrades
---

### Post by hikariws on 2022-10-20
[LEFT][COLOR=#232629][FONT=-apple-system]I'm following the tutorial on [https://github.com/dex4er/fakechroot](https://github.com/dex4er/fakechroot).

[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]I'm trying to install and run some apps keeping them isolated on an unprivileged user, without root. They are proprietary software distributed as .deb, so normally I'd need to go root to install them, but I don't wanna install them on the general system.

[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]The easiest solution would be install them on a VM, but I'm trying to do it first with fakechroot to save RAM.

[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]CLI apps work fine, as hello on the tutorial. But GUI apps fail with

[/FONT][/COLOR][/LEFT]
```
$ echo $DISPLAY
:1
$ fakechroot fakeroot chroot /home/restricted/chroot firefox
Authorization required, but no authorization protocol specified

Error: cannot open display: :1
```

[LEFT][COLOR=#232629][FONT=-apple-system]I am using Ubuntu 22.04. How can I authorize it to use the display?
[/FONT][/COLOR][/LEFT]

---

### Post by MAFoElffen on 2022-10-22
The user "root' does not normally have access to start the Linux Graphics Engine... meaning when you are in a chroot environment, you would have to change users to another user (besides 'root') to start the graphics engine, then the desktop... Then that user would have access to their ~/.Xauthority file to authorize the Graphics engine to start up (Xorg or Wayland)... Then you would start the Graphics engine, then start a desktop manager... Then start "Firefox"...

The GUI app 'Firefox' cannot run without the Linux Graphics Layer framework running and in place first. Then 'Firefox' itself needs to create a user profile file... Running a browser, to the internet, as 'root', is a security risk in itself.

You could certainly clobber it to override that, so that user 'root' could run the Graphics Layer, but that is normally considered a security risk...

---

