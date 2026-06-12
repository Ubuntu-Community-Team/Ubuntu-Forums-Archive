---
title: "GNOME Shell (from git) build error"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by Rekenber on 2011-01-30
Here's the error.

In file included from tray/na-tray-child.c:25:
tray/na-tray-child.h:44: error: expected specifier-qualifier-list before &#8216;GtkSocket&#8217;
tray/na-tray-child.h:53: error: expected specifier-qualifier-list before &#8216;GtkSocketClass&#8217;
tray/na-tray-child.c: In function &#8216;na_tray_child_get_type&#8217;:
tray/na-tray-child.c:32: error: &#8216;GTK_TYPE_SOCKET&#8217; undeclared (first use in this function)
tray/na-tray-child.c:32: error: (Each undeclared identifier is reported only once
tray/na-tray-child.c:32: error: for each function it appears in.)
tray/na-tray-child.c: In function &#8216;na_tray_child_realize&#8217;:
tray/na-tray-child.c:51: error: &#8216;NaTrayChild&#8217; has no member named &#8216;has_alpha&#8217;
tray/na-tray-child.c:62: error: &#8216;NaTrayChild&#8217; has no member named &#8216;parent_relative_bg&#8217;
tray/na-tray-child.c:70: error: &#8216;NaTrayChild&#8217; has no member named &#8216;parent_relative_bg&#8217;
tray/na-tray-child.c:75: error: &#8216;NaTrayChild&#8217; has no member named &#8216;parent_relative_bg&#8217;
tray/na-tray-child.c:78: error: &#8216;NaTrayChild&#8217; has no member named &#8216;composited&#8217;
tray/na-tray-child.c:81: error: &#8216;NaTrayChild&#8217; has no member named &#8216;parent_relative_bg&#8217;
tray/na-tray-child.c:81: error: &#8216;NaTrayChild&#8217; has no member named &#8216;has_alpha&#8217;
tray/na-tray-child.c:88: error: &#8216;NaTrayChild&#8217; has no member named &#8216;parent_relative_bg&#8217;
tray/na-tray-child.c: In function &#8216;na_tray_child_size_allocate&#8217;:
tray/na-tray-child.c:170: error: &#8216;NaTrayChild&#8217; has no member named &#8216;parent_relative_bg&#8217;
tray/na-tray-child.c: In function &#8216;na_tray_child_draw&#8217;:
tray/na-tray-child.c:193: error: &#8216;NaTrayChild&#8217; has no member named &#8216;parent_relative_bg&#8217;
tray/na-tray-child.c: In function &#8216;na_tray_child_new&#8217;:
tray/na-tray-child.c:278: error: &#8216;NaTrayChild&#8217; has no member named &#8216;icon_window&#8217;
tray/na-tray-child.c:290: error: &#8216;NaTrayChild&#8217; has no member named &#8216;has_alpha&#8217;
tray/na-tray-child.c:293: error: &#8216;NaTrayChild&#8217; has no member named &#8216;composited&#8217;
tray/na-tray-child.c:293: error: &#8216;NaTrayChild&#8217; has no member named &#8216;has_alpha&#8217;
tray/na-tray-child.c: In function &#8216;na_tray_child_get_title&#8217;:
tray/na-tray-child.c:320: error: &#8216;NaTrayChild&#8217; has no member named &#8216;icon_window&#8217;
tray/na-tray-child.c: In function &#8216;na_tray_child_has_alpha&#8217;:
tray/na-tray-child.c:367: error: &#8216;NaTrayChild&#8217; has no member named &#8216;has_alpha&#8217;
tray/na-tray-child.c: In function &#8216;na_tray_child_set_composited&#8217;:
tray/na-tray-child.c:388: error: &#8216;NaTrayChild&#8217; has no member named &#8216;composited&#8217;
tray/na-tray-child.c:391: error: &#8216;NaTrayChild&#8217; has no member named &#8216;composited&#8217;
tray/na-tray-child.c: In function &#8216;na_tray_child_force_redraw&#8217;:
tray/na-tray-child.c:406: error: &#8216;NaTrayChild&#8217; has no member named &#8216;parent_relative_bg&#8217;
cc1: warnings being treated as errors
tray/na-tray-child.c:418: error: implicit declaration of function &#8216;gtk_socket_get_plug_window&#8217;
tray/na-tray-child.c:418: error: implicit declaration of function &#8216;GTK_SOCKET&#8217;
tray/na-tray-child.c:418: error: assignment makes pointer from integer without a cast
tray/na-tray-child.c: In function &#8216;na_tray_child_get_wm_class&#8217;:
tray/na-tray-child.c:529: error: &#8216;NaTrayChild&#8217; has no member named &#8216;icon_window&#8217;
make[3]: *** [libtray_la-na-tray-child.lo] Error 1
make[3]: Leaving directory `/home/rekenber/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/rekenber/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rekenber/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [30/33]

Are there any fixes to this?

EDIT: I am using Maverick.

---

### Post by dino99 on 2011-01-30
pick it from there:

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by keplerspeed on 2011-01-30
Rekenber, if you keep getting that error when building from source, just delete the "Source" and "gnome-shell" folders that jhbuild put in your home folder, and rerun the build instructions from [http://live.gnome.org/GnomeShell#building]("http://live.gnome.org/GnomeShell#building").

---

