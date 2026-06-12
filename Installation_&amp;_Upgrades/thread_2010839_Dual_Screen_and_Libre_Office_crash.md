---
title: "Dual Screen and Libre Office crash"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by pimparello on 2012-06-26
Dear all, 

when I open libre office on my second screen, it crashes before a document appears. It does not crash when started on screen 0. 
Documents$ lowriter

```

(soffice:8865): Gtk-WARNING **: Unable to locate theme engine in module_path: "oxygen-gtk",

(soffice:8865): Gtk-WARNING **: Unable to locate theme engine in module_path: "oxygen-gtk",

(soffice:8865): Gtk-WARNING **: Unable to locate theme engine in module_path: "oxygen-gtk",

(soffice:8865): Gtk-WARNING **: Unable to locate theme engine in module_path: "oxygen-gtk",
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-pnICZL/pkcs11: No such file or directory
The program 'soffice' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 827 error_code 8 request_code 70 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

The background problem is:

I have upgraded my system from ubuntu 11.10 to 12.04, 64bit. I have installed ubuntu but I am using KDE, it seemed to be the only wm with which my dual screen is working (Nvidia GeForce 8400GS]. xrandr does not recognize the default resolution of screen 0 nor that there is another screen on VGA1.

So far the only way to use dual screen and to rotate the x screen 1 has been to run nvidia setting every time I log in and to manually adjust the resolution of screen 0 and to rotate screen 1 (seperate x screen, other options don't work even though I would love to change that and to be able to move windows to the other screen). I forgot how I enabled the rotate function in nvidia settings, but originally this option was not available.

Now libre office seems to be the only program that crashes when started on screen 1, it does run on screen 0 though. 

The two options are: 
a) to get libre office to run normally on screen 1 as it used to. 

b) to get a proper setup running for this graphic card (for instance via xrandr, but whatever I've tried just won't work...) which then will hopefully also solve the libre office problem.

Please help, I need to work and I start going mad with this nvidia mess.

Thanks a lot, 
pimparello

---

### Post by pimparello on 2012-06-27
*up*

Please help, share some ideas or whatever.  I need this for my work.

---

### Post by pimparello on 2012-06-28
This is caused by a bug in the packages in the ubuntu repositories. 

I have de-installed LO and re-installed the deb packages supplied by LO on its homepage, and the problem has disappeared. 

Please acknowledge before I mark this as solved.

---

### Post by ronnybob7 on 2013-04-27
I was having the same problem. What I found out was on the second screen you must disable the launcher from coming out on the second screen, I don't mean to let it stick out from the side but to stop it from coming out all together.

---

