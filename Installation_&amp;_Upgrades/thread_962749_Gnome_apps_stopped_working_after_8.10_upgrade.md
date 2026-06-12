---
title: "Gnome apps stopped working after 8.10 upgrade"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by Czar on 2008-10-29
I'm at desktop of 8.1 yet none of my gnome apps load.  Firefox, nautilis, gnome-terminal, synaptic, etc... all fail!  Some apps work; Opera, keepassx, pidgin, and wesnoth.  

When loading a broken apps sometimes the entire gnome-panel bar reloads.  Other times the app just doesn't run.  

I can't load a terminal in this x-session to figure out what is going on... The x/dmesg logs do not report anything when the app fails. 

What should I do?

---

### Post by Czar on 2008-10-29
> **Czar said:**
> The x/dmesg logs do not report anything when the app fails. 

$cat ~/.xsession-errors
```

The program 'gnome-panel' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadFont (invalid Font parameter)'.
  (Details: serial 6845 error_code 7 request_code 94 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

(gnome-panel:12228): Gdk-WARNING **: /build/buildd/gtk+2.0-2.14.4/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window
The program 'xfce4-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadCursor (invalid Cursor parameter)'.
  (Details: serial 711 error_code 6 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
The program 'xfce4-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadCursor (invalid Cursor parameter)'.
  (Details: serial 717 error_code 6 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
The program 'gedit' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadName (named color or font does not exist)'.
  (Details: serial 280 error_code 15 request_code 45 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
X-Error: BadName (named color or font does not exist)
	Major opcode: 45 (X_OpenFont)
	Resource ID:  0x280004a
	Serial No:    402 (402)
These errors are reported asynchronously,
set environment variable SAL_SYNCHRONIZE to 1 to help debugging
```

---

### Post by torspo on 2008-11-02
Pretty much the same here..

Terminal works for me, but most of the apps don't. Running them from terminal gives the BadName -error.

Using /etc/init.d/xfs stop seems to help, maybe you can do that in another window.

8.10 also broke my networking (wired network not working anymore, if i boot with hardy live dvd it works on 8.10 too until dhcp lease expires)

---

### Post by Czar on 2008-11-02
My original issues was resolved by purging all the ubuntu 8.10 NVIDIA stuff and installing the official 1.77 drivers from Nvidia.com.

---

### Post by torspo on 2008-11-02
Didn't help me.

---

### Post by mdmonk on 2008-11-12
I did an upgrade to 8.10 as well, and have had issues with video every since.

What worked for me was to remove the xfs (X11 font server) package. Once I did that, I was able to get apps to open/work again. (xfs is deprecated in the xorg released in Ubuntu 8.10?)

I tried the nvidia drivers available via Ubuntu, and the nvidia drivers available from Nvidia themselves, and had no luck, until I removed the xfs package. Now the nvidia driver(s), v177, available via Ubuntu work without a problem.

-Chuck (MdMonk)

---

### Post by matthewgeier on 2008-12-10
Removing xfs worked for me.

 What I assume is happening -

 Older system required XFS, so it was upgraded in the distro upgrade,
 But 8.10 xfs is broken some how.

 8.10 X server doesn't use xfs anymore in it's 'normal' configuration. - it won't be used unless 

FontPath        "unix/:7100"

is in the config file. So even if xfs running, it won't be used.

Roll on Nvidia.
 nvidia-settings when generating a new 'twinview' configuration file for you helpfully adds 

Section "Files"
	FontPath        "unix/:7100"
EndSection

thus configuring your X server to use the broken font server.

 Restarting xfs 'fixed' things as it broke the unix socket connection between X and the font server - however restarting X would remake that connection and fonts would be broken again.

---

