---
title: "[SOLVED] Can't start X - no path to fonts"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by ixus_123 on 2008-07-09
Hello, I have installed Hardy (64) server edition and wanted to install a light weight desktop (I was thinking fluxbox)

I installed the following xserver-xorg-core xinit menu menu-xdg fluxbox synaptic but a startx just throws out errors..

here is the output of /var/log/Xorg.0.log

I could do with some help please

```
root@asus:~# less /var/log/Xorg.0.log

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux asus 2.6.24-16-server #1 SMP Thu Apr 10 13:15:38 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 10 03:54:58 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/misc" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
        Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
        Entry deleted from font path.

Fatal server error:
No valid FontPath could be found.
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
(END) 
```

---

### Post by Partyboi2 on 2008-07-10
try installing xfonts-base 
```
sudo apt-get install xfonts-base
```

---

### Post by ixus_123 on 2008-07-10
Thank-you Thank-you Thank-you :D


That worked perfectly.  I had tried installing individual fonts and ms core fonts both with no luck.

Desktop is up and running now and you have saved me a lot of head scratching

---

