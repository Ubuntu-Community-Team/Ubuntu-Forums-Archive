---
title: "UNR Upgrade to 10.10 hung because screen too small"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by jrowland on 2010-10-11
I'm in the process of upgrading my netbook remix from 10.04 to 10.10 via the software update manager.  It gets to this point (in screen shot) and (I'm guessing here) is waiting for some kind of response from me, but the window is out side the screen space.

Are there specific steps I should take from here?  The only thing I can think of is to reboot, but I don't want to hose the install.

I've tried hitting the enter key; then tab, enter; then tab, tab, enter... hoping that I could tab my way to the "ok" button, if such a thing exists.

My desktop upgrade went just fine, and it was at about this point where the installer asked me if I wanted to replace my custom config_ssh file.  I'm guessing the Netbook is at this same point.  but... just guessing.

I cannot click-and-drag on the windows that are showing, but the computer itself is not frozen.  I can click on the power button and the Indicator applet, etc... but I cannot click on the "application popup menu" (sorry, not sure what it's called... the "start button" in Windows speak).

Sorry for the poor cellphone picture, but under the circumstances, it's the best I've got.

[IMG]http://lh3.ggpht.com/_yQrDZ4MszvQ/TLKlgrjaLjI/AAAAAAAABTs/_Fu4OglP63o/photo.jpg[/IMG]
[URL="http://lh3.ggpht.com/_yQrDZ4MszvQ/TLKlgrjaLjI/AAAAAAAABTs/_Fu4OglP63o/photo.jpg"]
[/URL]

---

### Post by waveskiJohn on 2010-10-11
I got the exact same problem with a Toshiba NB200.

---

### Post by Seano1957 on 2010-10-11
You should be able to create a virtual screen that you can pan using xrandr.

In a terminal window type xrandr -q and look for the connected display which is usually LVDS1 for a laptop panel. Then type xrandr --output <display> --panning widthxheight where width is your normal screen width and height is something bigger than your normal height.

For example xrandr --output LVDS1 --panning 1024x768 creates a 1024x768 virtual screen on my Aspire that 'pans' up when the mouse pointer is moved beyond the screen bottom.

This is a good trick to know anyway if you have a netbook because of the 16x9 screen aspect. I have it on a hotkey along with screen/trackpad rotate for reading docs. 

--sean.

---

### Post by jrowland on 2010-10-12
I wasn't able to launch anything.  Finally ended up just rebooting and choosing "repair mode" (or whatever it is)  in the grub menu.  It kicked back off, started going through the upgrade again, and worked just fine.

Very nice, new interface in 10.10 UNR!

Appreciate the tip on xrandr.

---

### Post by Matruskan on 2010-10-12
It's probably similar to this problem:
[http://ubuntuforums.org/showthread.php?p=9957424](http://ubuntuforums.org/showthread.php?p=9957424)

---

### Post by Seano1957 on 2010-10-12
Funnily enough I have just run the upgrade myself and sure enough eventually I get a mother-may-I that is waiting for a click that is off the bottom of the screen no matter how far up you pull the window !

Netbooks have been out long enough now for folks to make their software aware for gawd's sake!

In my case everything was still responding so it was a simple case of firing off the xrandr command so you are right in that you clearly had a secondary issue.

--sean.

---

