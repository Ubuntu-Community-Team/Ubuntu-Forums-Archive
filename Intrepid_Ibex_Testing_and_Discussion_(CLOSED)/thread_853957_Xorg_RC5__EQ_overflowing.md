---
title: "Xorg RC5 : EQ overflowing"
date: 2008-07-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-07-09
Im getting alot of these in my Xorg.0.log:

[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.

Anyone else? Im on nvidia 177.13 with Compiz turned off.

---

### Post by plun on 2008-07-09
Nope, just as a reference you have my startup log
Using tseliots ppa driver , 177

[http://paste.ubuntu.com/26156/](http://paste.ubuntu.com/26156/)

---

### Post by ShirishAg75 on 2008-07-09
Hi all, 
 I dunno if this is similar or not. I have this in my xsession-errors file 

```
gdm[7187]: DEBUG: Attempting to parse key string: daemon/Greeter=/usr/lib/gdm/gdmlogin
gdm[7187]: DEBUG: Attempting to parse key string: daemon/PreSessionScriptDir=/etc/gdm/PreSession/
gdm[7187]: DEBUG: Forking extra process: /etc/gdm/PreSession/Default
gdm[7189]: DEBUG: Attempting to parse key string: xdmcp/Enable=false
gdm[7189]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm
gdm[7189]: DEBUG: Attempting to parse key string: daemon/RootPath=/sbin:/usr/sbin:/bin:/usr/bin
gdm[7187]: DEBUG: Attempting to parse key string: daemon/DefaultPath=/bin:/usr/bin
gdm[7187]: DEBUG: Attempting to parse key string: daemon/BaseXsession=/etc/gdm/Xsession
gdm[7187]: DEBUG: Running /etc/gdm/Xsession /usr/bin/gnome-session for shirish on :0
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
Setting IM through im-switch for locale=en_IN.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

(seahorse-agent:7187): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(seahorse-agent:7187): atk-bridge-WARNING **: IOR not set.

(seahorse-agent:7187): atk-bridge-WARNING **: Could not locate registry
Xlib:  extension "XEVIE" missing on display ":0.0".
SESSION_MANAGER=local/Mugglewille:/tmp/.ICE-unix/7187
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

** (gnome-session:7187): WARNING **: Failed to send buffer

** (gnome-session:7187): WARNING **: Failed to send buffer
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

```This is most probably a gnome-session errors or what? Any or all pointers are welcome. 

```

root@Mugglewille:/home/shirish# ls -lh .xsession-errors 
-rw-r--r-- 1 shirish shirish 1.9K Jul  9 13:33 .xsession-errors

```I am able to run only through going through root prompt, invoke startx which starts xfce and things work.

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-session/+bug/247003](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-session/+bug/247003)

---

