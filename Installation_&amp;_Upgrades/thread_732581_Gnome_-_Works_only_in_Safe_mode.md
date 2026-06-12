---
title: "Gnome - Works only in Safe mode"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by omshivaprakash on 2008-03-23
Hi, 

Please help me with this. I would love to live with the normal Gnome session. Started facing this error after upgrading to Hardy on my Dell M1210. Have Nvidia Geforce Go 7600 GPU. nvidia-glx-new cannot be installed via Hardware Drivers. I guess this driver itself causing issue. 

xsession-errors file logs the following. 
------------------


SESSION_MANAGER=local/techfiz:/tmp/.ICE-unix/9144
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 89 error_code 1 request_code 151 minor_code 6)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
1206255201.249098 Session manager: disconnected...

** (gnome-settings-daemon:9256): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:9256): WARNING **: Could not acquire name
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 89 error_code 1 request_code 151 minor_code 6)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 89 error_code 1 request_code 151 minor_code 6)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
seahorse nautilus module initialized
Initializing nautilus-share extension
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
Screen is composited.
APPLET : /usr/lib/awn/applets/cairo_main_menu.desktop
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 89 error_code 1 request_code 151 minor_code 6)
  (Details: serial 89 error_code 1 request_code 151 minor_code 6)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
APPLET : /usr/lib/awn/applets/showdesktop.desktop

** (awn-applet-activation:9308): WARNING **: This desktop file does not exist /usr/lib/awn/applets/cairo_main_menu.desktop

The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 89 error_code 1 request_code 151 minor_code 6)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by owenll on 2008-03-23
Same here

[http://ubuntuforums.org/showthread.php?t=731312](http://ubuntuforums.org/showthread.php?t=731312)

and it seems to be a bug.

---

