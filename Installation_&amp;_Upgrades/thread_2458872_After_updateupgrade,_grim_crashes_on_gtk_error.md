---
title: "After update/upgrade, grim crashes on gtk error"
date: 2021-03-05
forum: Installation &amp; Upgrades
---

### Post by paulk59 on 2021-03-05
I have a headless Ubuntu 20.04.2 on AARCH64. I have been running GVIM over ssh with no problems for more than a year (including from 18.04 to 20.04). 
I ran apt update and apt upgrade and now gvim crashes on startup due to pixbuf error. I checked and permissions are fine for /usr/share/mime and I have tried the apt --fix-broken and gdk-pixbuf-query-loaders --update-cache and reinstall of vim-gtk3, etc. I also tried a reinstall of [COLOR=#000000][FONT=Menlo]libgdk-pixbuf2.0-0 and libpng-dev. [/FONT][/COLOR]
Nothing has fixed it. I do not know where to look and I cannot find any other suggested fixes/changes from anyone. I should note that XWindows is still working fine as apps like xterm and the like all work with no issue. 
The error is as follows:

[COLOR=#000000][FONT=Menlo](gvim:22007): Gtk-[COLOR=#9fa01c]**WARNING**[/COLOR] **: [COLOR=#400bd9]09:55:04.292[/COLOR]: Could not load a pixbuf from icon theme.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]This may indicate that pixbuf loaders or the mime database could not be found.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Gtk:ERROR:../../../../gtk/gtkiconhelper.c:494:ensure_surface_for_gicon: assertion failed (error == NULL): Failed to load /usr/share/icons/Yaru/16x16/status/image-missing.png: Unrecognized image file format (gdk-pixbuf-error-quark, 3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Bail out! Gtk:ERROR:../../../../gtk/gtkiconhelper.c:494:ensure_surface_for_gicon: assertion failed (error == NULL): Failed to load /usr/share/icons/Yaru/16x16/status/image-missing.png: Unrecognized image file format (gdk-pixbuf-error-quark, 3)[/FONT][/COLOR]

---

### Post by norobro on 2021-03-05
I'm on an amd64 machine and the file 'loaders.cache' is in /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0. If I move that file out of the way I get the same errors that you are seeing.

Does that file exist in /usr/lib/(Architecture)/gdk-pixbuf-2.0/gdk-pixbuf-query-loaders?
If so is the owner root/root and are the permissions set to 755?

---

### Post by paulk59 on 2021-03-06
The file exists in [FONT=Menlo][COLOR=#000000]/usr/lib/aarch64-linux-gnu/gdk-pixbuf-2.0/2.10.0 as well as a directory called loaders. The loaders.cache was 644. I tried 755 but it did not help. 
I then looked in loaders and they are all 644 which seems very wrong for a DLL (shared object). I changed them to 755 but it did not help. But, clearly these are the files that know the file types. So, I do not know what is going on here.

[/COLOR][/FONT][COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 10368 Mar 21  2020 io-wmf.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 18480 Feb 18 06:41 libpixbufloader-ani.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 18496 Feb 18 06:41 libpixbufloader-bmp.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 22576 Feb 18 06:41 libpixbufloader-gif.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 14384 Feb 18 06:41 libpixbufloader-icns.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 18544 Feb 18 06:41 libpixbufloader-ico.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 22592 Feb 18 06:41 libpixbufloader-jpeg.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 22576 Feb 18 06:41 libpixbufloader-png.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 18528 Feb 18 06:41 libpixbufloader-pnm.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 14400 Feb 18 06:41 libpixbufloader-qtif.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 10016 Nov 30 09:08 libpixbufloader-svg.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 18488 Feb 18 06:41 libpixbufloader-tga.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 18488 Feb 18 06:41 libpixbufloader-tiff.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 14384 Feb 18 06:41 libpixbufloader-xbm.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 26672 Feb 18 06:41 libpixbufloader-xpm.so[/FONT][/COLOR]


[FONT=Menlo][COLOR=#000000]

[/COLOR][/FONT]

---

### Post by paulk59 on 2021-03-08
I ran fsck on the disk (SDCard) and it found a few inodes needing repair, but that did not help.
But, it was the underlying problem. The /usr/share/mime directory permissions were missing the "x" for group and world, and so it could not read them as a directory. 
Interestingly the update-mime-cache never mentioned this. Seems like it should be aware of that. 
Anyway, it all works again.

---

