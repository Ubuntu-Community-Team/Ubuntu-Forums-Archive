---
title: "compiz/unity/gnome-desktop-background fail after upgrading to 13.04"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by simpsus on 2013-05-16
Hallo,

I upgraded from 12.10 to 13.04.
I did not have unity installed because I basically hate it. Instead I had a setup with a cairo dock bar and kupfer.

After the upgrade, my desktop is white, the cursor above the white window is a black X, the white window does not span the dock.
Starting a terminal brings the window, but wihtout decorations, there is no way to alt+drag the window. fortunately focus by clicking works.
Running ```
compiz --replace
``` gives me back window decorations and normal window management functionalities, but the window close button does not work on maximized windows. It closes the window which is not in the foreground but behind it. You have to demaximize a window to be able to close it (or do alt-f4).

Out of anxiety I installed unity because I thought that was the cause of the problem. The result is basically the same but after starting compiz unity starts as well, including the side and top bar.

I would appreciate any help in resolving this situation. Normally I would do a fresh install, but my /home is not on a separate partition and I have quite a lot of applications installed and configured that are not so easy to reinstall/port.

Thank you very much!

simpsus

---

### Post by grahammechanical on 2013-05-16
The upgrade process is designed to upgrade from one default Ubuntu to another default Ubuntu. The developers have no way of knowing of the modifications that you have made to the desktop. How could they know that? How could they make provision for your installation not having Unity installed?

```
sudo apt-get install dconf-tools
```
```
dconf reset -f /org/compiz/
```

The second command resets compiz in 13.04. You may need to reinstall Compiz first. You may also need to use these commands to get Unity functioning. Reset Unity
```
setsid unity
```
```
unity --reset-icons
```

Regards.

---

### Post by simpsus on 2013-05-16
Thank you very much for your answer.
I did not mean to imply it was anybodies fault, although I would hope to be able to uninstall some packages and still be able to upgrade, but that's another story.

I tried your instructions, the commands execute without error, but the situation does not go away. After a reboot, I still have a white desktop, no window decorations and hardly functioning windows.

---

