---
title: "&quot;Show desktop&quot; shows remains of previous window not wallpaper"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by simonspringett on 2014-10-27
Hi all

I upgraded from 14.04 to 14.10.  Now using "show desktop" instead of clearing all windows away to show clear  wallpaper leaves the ghost images of the previously opened window(s) immediately over the desktop.  I have tried to set a wallpaper photo but this does not work.  More details at a bug rep here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1385457](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1385457).

Any advice or help gratefully received.

---

### Post by raydar on 2014-10-27
Same ghost image problem here, after Ubuntu upgraded from 14.04 to 14.10, but I don't need to do a show desktop for it to occur. When I log in, everything to the right of the Unity launcher is black; my previous wallpaper (which still shows up in the settings as the current wallpaper) and all the icons (still, in fact, per file manager) on my desktop are not visible. As soon as I start the file manager, all the icons appear but there's still just black instead of the wallpaper image. Ghost images remain of any windows I open, including icons, streaks from window animations, etc. 

Everything is just fine, however, in all the Gnome session variants I have to choose from if I log out and log back in using one of them. The problem comes right back if I choose an Ubuntu session again. I also had nemo installed and set up as the default file manager under 14.04, and to try to fix this problem after the upgrade to 14.10 I reissued the commands to make nemo the default file manager in case that was responsible for the desktop icon behavior, but it made no difference that I could tell.

What's the best setting to zap to make things usable until the real issue is resolved?

---

### Post by simonspringett on 2014-10-30
All I am doing is keeping the browser open as the bottom level of window.

---

### Post by raydar on 2014-10-30
That helps for me too; thanks!

---

### Post by simonspringett on 2014-11-01
I hvve removed the graphics card - the problem remains using hte onboard graphics.  It is a Foxconn motherboard - I read a couple of posts about Foxconn support - or lack of - for Ubuntu.

---

### Post by simonspringett on 2014-11-01
> **simonspringett said:**
> I have removed the graphics card - the problem remains using the onboard graphics.  It is a Foxconn motherboard - I read a couple of posts about Foxconn support - or lack of - for Ubuntu.

Just flashed the BIOS today - no improvement.

---

### Post by simonspringett on 2014-11-01
Now switched to Gnome desktop - I have my wallpaper back adn all seems much more stable.  No sign of ghosting.

---

