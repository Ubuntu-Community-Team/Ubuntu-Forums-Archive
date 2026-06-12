---
title: "Upgrade broke X fonts, tried adding new directories to xorg.conf, no luck"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by siennalizard on 2006-12-15
Dear all,

I have upgraded mostly successfully to Edgy with one failing: vncviewer complains that it cannot find a font:
```

james@garnet:~$ vncviewer xxx.xxx.xxx.101
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
VNC server supports protocol version 3.6 (viewer 3.3)
Password: 
VNC authentication succeeded
Desktop name "mainoffice ( 192.168.1.35 )"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-16-*-*-*-*-*-*-*" to type FontStruct
Warning: Unable to load any usable ISO8859 font
Warning: Unable to load any usable ISO8859 font
Error: Aborting: no font found

```

This is even after adding more font sources to the xorg.conf file as some people have tried.
Looking for that font itself produces the goods (see below). Why can't vncviewer find them?

```

james@garnet:~$ xlsfonts -fn '-*-helvetica-bold-r-*-*-16-*-*-*-*-*-*-*'
-adobe-helvetica-bold-r-normal--16-154-75-75-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--16-154-75-75-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--16-154-75-75-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--16-154-75-75-p-0-iso10646-1
-adobe-helvetica-bold-r-normal--16-154-75-75-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--16-154-75-75-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--16-154-75-75-p-0-iso8859-1
-adobe-helvetica-bold-r-normal--16-154-75-75-p-0-iso8859-1

```

Many thanks,
J.

---

### Post by PhilOSparta on 2006-12-15
I have the same problem with emacs.  Same fonts also.
Diagnostic shows that they are on the system.

The problem exists when emacs is first started the graphic fonts on the opening window are all squares.
Also, when the cursor is floated over the graphic menu items at the tool bar, the tool tip items are squares.

Any help would be appreciated.



Phil

---

### Post by PhilOSparta on 2006-12-15
I found a fix.  These changes must be made to **/etc/X11/xorg.conf**

Make a backup copy of the file first.

After I changed each occurrence of **/usr/share/X11/fonts** to **/usr/share/fonts/X11**, things now work as expected.


Phil

---

### Post by siennalizard on 2006-12-21
I had already tried that, but have found that the most effective way is to enable the universe repository and install xvnc4viewer. That has a little more advanced interface thanthe older version (3.3?), and seems to be able to find the fonts. It replaces the /usr/bin/vncviewer symlink, so you don't even need to use the new command: just carry on using vncviewer as before.

Regards,
J.

---

