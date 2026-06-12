---
title: "Display won't work after display update"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by tbaggett on 2008-03-08
First off, I'm pretty new to the Ubuntu scene.  But i recently got Ubuntu working well with a dual boot set up along with Vista.  Got everything running smoothly and then went to update my video card, using a 'Envy' in hopes to get dual monitors recognized.  Now when I boot Ubuntu some text comes up to fast to read it and then the monitor switches off.  And that's where I'm stuck.  I'm hoping there is away to roll back my driver update?  Or something to prevent a full new install.  Anyone had any luck with installing this driver?

---

### Post by jakev383 on 2008-03-12
Sounds like it's going into a display mode that your monitor can't handle.
When the screen goes blank, try hitting Ctrl-Alt-F1 and login using your username/pass.  Then run ```
sudo dpkg-reconfigure xserver-xorg
``` And then for good measure give it a reboot and see if it comes up.

---

