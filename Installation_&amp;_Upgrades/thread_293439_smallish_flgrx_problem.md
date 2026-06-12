---
title: "smallish flgrx problem"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by melat0nin on 2006-11-05
HI all

Installed edgy fine and got things working (after a 'sudo dpkg-reconfigure xserver-xorg') and things seemed fine, although I could no longer login with Xgl (it would accept my user/pass but then fall back to the login screen).  However, when I logged in with standard Gnome, compiz still worked and all the effects were there (is that to be expected? I was confused.. was i using Aiglx w/compiz then?)

Thing is, compiz was a extremely slow so i figured my gfx driver was duff.  I disabled blurring in the compiz settings and it sped things up, but not to the stage it was with Dapper.  So i figured I better install the fglrx driver (esp since there's been talk of a new one)

So I did that thru Synaptic, but now I can't login.  What happens with Gnome is i enter user/pass and then I get a blank white screen with the mouse cursor, and there's a flash of grey activity in the system tray where the clock etc is but then it disappears and I'm left with a white screen when I can't get out of without pressing Ctrl+Alt+F1.

Any ideas?  I re-ran dpkg-reconfigure after the fglrx install and changed tried both 'ati' and 'fglrx' as the display driver but that made no difference.

Thanks in advance - and Edgy looks really nice - many of my niggles have been addressed!

---

### Post by boban on 2006-11-05
With fglrx try adding to you /etc/X11/xorg.conf

```

Section "Extensions"
    Option        "Composite" "0"
EndSection

```

---

