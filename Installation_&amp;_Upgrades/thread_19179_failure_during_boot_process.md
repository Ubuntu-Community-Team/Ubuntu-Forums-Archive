---
title: "failure during boot process"
date: 2005-03-10
forum: Installation &amp; Upgrades
---

### Post by nacho_magacho on 2005-03-10
During boot process, the following error appear

  *Temporary failure in name resolution [ fail ]

then my screen monitor shows the following error

   Out of frecuency
      HF  95.4 Khz
   Operation
      HF 30-54 Khz

How can I correct the frecuency value of the monitor operation? :-|

---

### Post by GrapeApe on 2005-03-10
I'm not sure I completely understand.  The first error appears to be a failure of the DNS.  It shouldn't have any bearing on your monitor.   It's most likely trying to start gdm and it isn't configured correctly for your monitor.

Hit Ctrl-Alt-F1.  That will take you to a terminal instead of X.
There you can login.   Then depending on which X server you have installed you can rerun it's configure script and set the monitor frequence correctly for your monitor.   The xorg configuration program is xorgconfig (I believe).   XFree is probably similar.  You will have to sudo those commands.

Or you can edit /etc/X11/XFConfig-4 (if XFree) or /etc/X11/xorg.conf (if xorg).   Example, sudo vi /etc/X11/XFConfig-4.

In XFConfig-4 or xorg.conf you will see a Section "Monitor".  Under that you can put your monitor capabilities.

For example

Section "Monitor"
    Identifier "Monitor0"
    HorizSync  31.5-60.0   (whatever yours was)
    VertRefresh 60-85       (whatever your monitor supports)

If I don't understand, sorry and please disregard.

---

### Post by nacho_magacho on 2005-03-12
[QUOTE=GrapeApe]I'm not sure I completely understand.  The first error appears to be a failure of the DNS.  It shouldn't have any bearing on your monitor.   It's most likely trying to start gdm and it isn't configured correctly for your monitor.

Hit Ctrl-Alt-F1.  That will take you to a terminal instead of X.
There you can login.   Then depending on which X server you have installed you can rerun it's configure script and set the monitor frequence correctly for your monitor.   The xorg configuration program is xorgconfig (I believe).   XFree is probably similar.  You will have to sudo those commands.

Or you can edit /etc/X11/XFConfig-4 (if XFree) or /etc/X11/xorg.conf (if xorg).   Example, sudo vi /etc/X11/XFConfig-4.

In XFConfig-4 or xorg.conf you will see a Section "Monitor".  Under that you can put your monitor capabilities.

For example

Section "Monitor"
    Identifier "Monitor0"
    HorizSync  31.5-60.0   (whatever yours was)
    VertRefresh 60-85       (whatever your monitor supports)

If I don't understand, sorry and please disregard.[/QUOTE]
 It works now, Thanks

---

