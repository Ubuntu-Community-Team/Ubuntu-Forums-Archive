---
title: "[SOLVED] Broken Gnome menu after upgrade from 7.10 to 8.04"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by StephaneLenclud on 2008-08-15
Hi,

After upgrading to 8.04 and going through the problem described on [http://ubuntuforums.org/showthread.php?t=865679](http://ubuntuforums.org/showthread.php?t=865679) my desktop menu's behavior is broken in very much the same way as described on [http://ubuntuforums.org/showthread.php?t=130660](http://ubuntuforums.org/showthread.php?t=130660) . Except that the solution provided there ain't working for me.

It's like the menus have the old Apple menu behavior: click and hold to browse the menus and release the button to select a menu item. Except that it's broken and behaves half like that and half like a Windows menu. On top of that I can't just launch programs from the top bar anymore just by clicking the icons. I have to right click the program's icon to bring up the contextual menu and select launch. Also in FF mouse interaction is broken; can't bring up list box menu for instance.

Can anyone help me out with that?
Is there a way to restore Gnome's default configuration?

Cheers,
S.

---

### Post by StephaneLenclud on 2008-08-15
Sometimes my left click just won't work at all until I right click on an icon in the top bar. My desktop is just unusable :(

---

### Post by StephaneLenclud on 2008-08-16
It does look like my single left click is interpreted as a double click.

---

### Post by kflorek on 2008-08-16
Are you sure the menu configuration items won't fix this?

System->Prefernces->Mouse

like may left and right are changed? or Trigger secondary click by holding down the primary button.

---

### Post by StephaneLenclud on 2008-08-16
I was indeed a case of too many mouse click event generated. It appears that my X server configuration was broken. By looking at my xorg.conf I realized there was quite fun extra InputDevice in there. Things like stylus, cursor and eraser, when I only have a standard PC configuration with mouse, keyboard and no touch screen.

I fixed the problem by regenerating my X configuration using ```
X -configure
``` from the recovery console. Then I used the newly generated xorg.conf as a base and put back into it my keyboard, mouse and screen configuration from my original xorg.conf.

See [http://slion.net/view/Dev/UbuntuUpgrade#From_7_10_to_8_04](http://slion.net/view/Dev/UbuntuUpgrade#From_7_10_to_8_04)

---

