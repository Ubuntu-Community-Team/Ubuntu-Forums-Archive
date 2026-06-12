---
title: "Error while logging in"
date: 2008-07-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by nephilim206 on 2008-07-13
When logging in without using failsafe mode, I guess this error:

> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Waiting 10 more seconds for Xgl to start...
Failed to initialize TTM buffer manager.  Falling back to classic.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

Gdk-ERROR **: The program 'gnome-session' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 11 error_code 1 request_code 151 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
aborting...

Does anyone know exactly what the issue is, and/or how to fix it?

Thank you

---

### Post by Eclipse. on 2008-07-13
The top part is nothing to worry about, the bottom part however is a bug.

Please post a bug report on lauchpad with the information there so the devs can try and help solve the problem.

---

### Post by RAOF on 2008-07-13
I'd suggest a quick and easy way to unbreak your login is to remove the xserver-xgl package.  Almost no-one still needs it, and they all have old nvidia cards.

Or you can wait until I get it building in Intrepid; I'll be trying making the next upload refuse to start unless you need it.

---

### Post by nephilim206 on 2008-07-13
Thank you! ^-^ Log in works just fine.

And is it possible to use compiz, and/or activate sound? They both don't seem to be working (activating compiz makes the screen completely white and unresponsive.)

---

