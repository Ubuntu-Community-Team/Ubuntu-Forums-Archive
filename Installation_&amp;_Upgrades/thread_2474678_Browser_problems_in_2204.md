---
title: "Browser problems in 22/04"
date: 2022-05-05
forum: Installation &amp; Upgrades
---

### Post by UBUminJ on 2022-05-05
I did a dualboot install with Windows 10. Basically that worked well but, apart from being quite slow, the new Ubuntu has browser problems.

Firefox doesn't start from the menu and doesn't start from terminal.
Chromium doesn't start from the menu - but from the terminal.

So here is the terminal log.

mke@brbrbr220405:~$ firefox
Gtk-Message: 20:36:46.907: Failed to load module "canberra-gtk-module"
Gtk-Message: 20:36:46.908: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.

(firefox:8343): Gdk-WARNING **: 20:36:47.897: The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc'.
  (Details: serial 529 error_code 11 request_code 146 (unknown) minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Exiting due to channel error.

mke@brbrbr220405:~$ chromium
Gtk-Message: 20:37:24.040: Failed to load module "canberra-gtk-module"
Gtk-Message: 20:37:24.041: Failed to load module "canberra-gtk-module"
Opening in existing browser session.
mke@brbrbr220405:~$

---

### Post by sudodus on 2022-05-05
In one computer I switched from the default Wayland to X in order to make Firefox work. I think it was in a computer with nvidia graphics.

Edit a configuration file,

```

sudo nano /etc/gdm3/custom.conf

```
to uncomment (remove '#') the line containing
```

WaylandEnable=false

```

and reboot.

[hr][/hr]
Someone else might know and show a way to make Firefox work also in Wayland.

---

### Post by UBUminJ on 2022-05-15
@sudodus
That helped. Firefox started, Chromium started. Thank you very much.

---

### Post by fearless752 on 2022-05-15
No go for me. All still not starting.

---

### Post by sudodus on 2022-05-15
@UBUminJ,

I'm glad that the web browsers for for you now :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by sudodus on 2022-05-15
@ fearless752,

The solution in this thread could not solve your problem, so you need another solution.

Please create a new thread and describe with many details your computer, your Ubuntu system and what symptoms you can see. That will help us help you.

---

