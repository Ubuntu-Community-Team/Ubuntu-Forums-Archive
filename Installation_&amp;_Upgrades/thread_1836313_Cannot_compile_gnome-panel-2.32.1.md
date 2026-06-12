---
title: "Cannot compile gnome-panel-2.32.1"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by braikar on 2011-08-30
Hi,

I just switched to ubuntu 11.04 and I am trying to apply a patch for the notification area, that makes it display properly on vertical wide panels.
The patch is on:
[https://bugzilla.gnome.org/show_bug.cgi?id=531371](https://bugzilla.gnome.org/show_bug.cgi?id=531371)
I'm not using unity.. (and I know the notification area is deprecated, but easystroke still uses it and skype still uses the notification area aswell...)


The patch worked perfectly on gnome-panel-2.30.2 and I never had problems applying it and compiling on ubuntu 10.04. However on 11.04, gnome-panel is in version 2.32.1.
I managed to modify the patch to work with the 2.32.1 version, but I cannot compile gnome-panel-2.32.1!
I got all the dependencies etc. but when I 'make' the source after a flawless 'configure -prefix=/usr' I get the following errors from the make.

```

  CCLD   gnome-panel
gnome_panel-applet.o: In function `panel_applet_destroy':
/home/braikar/Desktop/d/gnome-panel-2.32.1/gnome-panel/applet.c:754: undefined reference to `panel_applet_signaler_remove_applet'
gnome_panel-applet.o: In function `panel_applet_register':
/home/braikar/Desktop/d/gnome-panel-2.32.1/gnome-panel/applet.c:1437: undefined reference to `panel_applet_signaler_add_applet'
gnome_panel-panel-menu-bar.o: In function `panel_menu_bar_setup_tooltip':
/home/braikar/Desktop/d/gnome-panel-2.32.1/gnome-panel/panel-menu-bar.c:151: undefined reference to `panel_applet_signaler_get_default'
gnome_panel-panel-menu-items.o: In function `panel_menu_items_append_lock_logout':
/home/braikar/Desktop/d/gnome-panel-2.32.1/gnome-panel/panel-menu-items.c:1604: undefined reference to `panel_applet_signaler_get_default'

```

Applying the patch or not makes no difference, when I try to compile the source straight after having downloaded it, I still have the same errors :(
Is this somekind of a big error in the code of gnome-panel itself? or am I missing some dev dependencies?

---

### Post by braikar on 2011-08-30
Well I sorted the proble with a dirty hack proposed on
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/655205](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/655205)

just editing the makefile of the gnome-panel subfolder and changing
gnome_panel-panel-compatibility.$(OBJEXT) \
to
gnome_panel-panel-compatibility.$(OBJEXT) applet-signaler.$(OBJEXT) \
But I'm still amazed that I had to use such a hack :s

---

