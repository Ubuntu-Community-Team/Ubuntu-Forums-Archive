---
title: "[SOLVED] 21.10 -&gt; 22.04 Firefox does not open"
date: 2022-04-30
forum: Installation &amp; Upgrades
---

### Post by igouy on 2022-04-30
[SOLVED]  — **installed nvidia driver**

```
$ firefox -safe-mode
Importing existing firefox profiles from /home/z/.mozilla/firefox
Found default profile: 0fl3jk8h.default-release
Import done in 0.123 s
Gtk-Message: 19:38:48.727: Failed to load module "canberra-gtk-module"
Gtk-Message: 19:38:48.729: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option mesa_glthread overridden by environment.
$ Gtk-Message: 19:39:22.203: Failed to load module "canberra-gtk-module"
Gtk-Message: 19:39:22.205: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.

(firefox:5124): Gdk-WARNING **: 19:39:22.911: The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc'.
  (Details: serial 452 error_code 11 request_code 146 (unknown) minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```


Have un-installed and re-installed Firefox snap and restarted Ubuntu several times. That did not fix the problem.

----

Also

```
$ firefox -safe-mode
update.go:85: cannot change mount namespace according to change mount (/var/lib/snapd/hostfs/usr/share/libreoffice/help /usr/share/libreoffice/help none bind,ro 0 0): cannot create directory "/usr/share/libreoffice/help": permission denied
Gtk-Message: 08:46:46.883: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:46:46.921: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option mesa_glthread overridden by environment.
```

---

