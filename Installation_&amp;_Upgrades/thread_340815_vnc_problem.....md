---
title: "vnc problem...."
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by scho on 2007-01-17
It really makes me crazy!!!

Now I'm using kenel 2.6.17-10-generic and I can't make the vnc4server ( version 4.1.1+xorg1.0.2 in the synaptic manager)
working....
Actually, the server looks like working but when I connect to localhost using vncviewer,
I got one plain big window without anything in it except find checker board texture.

My xstartup file in ~/.vnc/ directory looks like this

#!/bin/sh

# Uncomment the following two lines for normal desktop:
 unset SESSION_MANAGER
 exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#twm &

And the log file that I got when I run the server is as following,
Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Wed Jan 17 16:28:04 2007
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!

Wed Jan 17 16:28:37 2007
 Connections: accepted: 127.0.0.1::47940
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)

It was O.K a couple of months ago. Surely, I think it's been screwed after updating something,
but I can't find out what it was.

Anyone has similar problem or some clues ? Please !!!

---

### Post by grumpymole on 2007-01-17
I think it may be [this bug.]("https://launchpad.net/ubuntu/+source/vnc4/+bug/78282")  vnc4server broke about a week ago with an update.  Broken for Feisty and Edgy.

I have seen a thread describing a workaround by downgrading to the previous version of the vnc4server package.  Search the forums for vnc4server or vnc and you should find it.

Alternatively, x11vnc is still working at the moment, but it might not be what you are looking for.  Only serves :0.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by scho on 2007-01-18
Thank you for helpful information. I could finally solve the problem.
I re-installed just previous version vnc4server_4.1.1+xorg1.0.2_0ubuntu1
from xxxubuntu1.6.10 something... and it is working now.

---

### Post by jinx099 on 2007-04-21
> **scho said:**
> Thank you for helpful information. I could finally solve the problem.
I re-installed just previous version vnc4server_4.1.1+xorg1.0.2_0ubuntu1
from xxxubuntu1.6.10 something... and it is working now.

Are you running Edgy or Feisty?

I am running feisty and I cannot downgrade to the specified version.  :(

---

### Post by buddijeevi on 2007-04-22
Hi
dpkg -l |fgrep xorg
ii  xvnc4viewer                            4.1.1+xorg1.0.2-0ubuntu4             
  Virtual network computing client software fo
ii  xserver-xorg-core                      1.2.0-3ubuntu8                         X.Org X server -- core server

   It looks like vncserver is compiled against older version of xorg1.0.2. If you compile the xvnc against xorg1.2.0, the problem will go away. One stopgap solution is to use only old X programs.  I am using twm as window manager, xpdf, xterm, firefox etc as fallback now. My feeling is that new X -programs  are using some extensions available only in 1.2.0 or libraries may be incompatible.

---

### Post by jinx099 on 2007-04-25
I had the same problem in debian etch.  I solved it by replacing this line:
```
exec /etc/X11/xinit/xinitrc
```
with this:
```
exec sh /etc/X11/xinit/xinitrc
```
I've not tried this fix in feisty yet.

---

