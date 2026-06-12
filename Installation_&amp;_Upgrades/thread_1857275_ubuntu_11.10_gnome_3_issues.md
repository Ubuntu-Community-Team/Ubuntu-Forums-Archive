---
title: "ubuntu 11.10 gnome 3 issues"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by odror on 2011-10-10
I have upgraded from ubuntu 11.04 to 11.10.

I have the following issues:

1 There is a significant delay on start-up. and logout (when compared to Unity or kde)

2 I get a minimal useless shell. with a panel but no system tray or any other useful menu. The defualt theme or shell are not activated. (all of theme are installed). I have to use CTR-ALT-DEL to get out of it. When I used it the second time I got the Unity theme, which subsequently disappeared.

3. On dual monitor (using separate X display) the second display is white with no active display manager. (the same issue is in Unity, but not in kde)

---

### Post by kurt18947 on 2011-10-10
I'm assuming you're talking about Gnome Shell here. Black bar on the top of the screen with the date in the middle? If so, try tapping the &quot;windows&quot; key. That should bring up a bar similar to Unity. Or put the mouse pointer in the upper left corner.    Ubuntu 11.10 runs gnome 3 but can have Unity, Gnome(Shell) or Classic(with panels) running on top. I cannot be of any help with the second monitor, sorry.

---

### Post by odror on 2011-10-10
tapping on the windows key did no make any difference.

I have a black bar on the top with no date or any of the system tray items. On the left side it has the following items file, edit, view, go, bookmarks and help. I do not have the Unity bar. It looks line an empty shell with no theme.

---

### Post by thatguruguy on 2011-10-10
There is a [sub-forum dedicated to 11.10]("http://ubuntuforums.org/forumdisplay.php?f=403").  You may want to peruse the threads there to see if your issues have already been addressed.  If they haven't been, you may wish to start a thread there.

---

### Post by kurt18947 on 2011-10-12
Checking the 11.10 forum as TGG mentioned is a good idea. My guess would be a lack of graphics capability.  The items you're seeing are I've seen when I've had graphics card issues.  Can you run Gnome Classic or Gnome Classic - no effects? You may have to install the gnome-session-fallback package if you haven't.  Gnome classic -no effects places less demands on the graphics subsystem.  If that works, you could try adding Xubuntu - desktop or Lubuntu - desktop and selecting one of those at log-in.

---

### Post by odror on 2011-10-12
> **kurt18947 said:**
> Checking the 11.10 forum as TGG mentioned is a good idea. My guess would be a lack of graphics capability.  The items you're seeing are I've seen when I've had graphics card issues.  Can you run Gnome Classic or Gnome Classic - no effects? You may have to install the gnome-session-fallback package if you haven't.  Gnome classic -no effects places less demands on the graphics subsystem.  If that works, you could try adding Xubuntu - desktop or Lubuntu - desktop and selecting one of those at log-in.
Actualy the problem is solved now. The nvisia card was in a "separate X screen" mode. I changed it to twinview and the problem is solved. But there is a bug in Ubuntu/Nvidia regarding the "separate X screen" mode.

---

