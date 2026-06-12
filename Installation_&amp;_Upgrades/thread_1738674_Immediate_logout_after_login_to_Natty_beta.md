---
title: "Immediate logout after login to Natty beta"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by shatil06 on 2011-04-25
Hi,

i have installed Ubuntu 11.04 beta release 64 bit and frequently updating with latest updates(allmost all).

now i'm having some problem, while i'm login to GUI interface it shows a blank screen(seems logging) and in the next screen it shows login screen again.(Immediate logout).


Can anybody please suggest to get rid off this situation?

i found some messages from syslog like below:

acpid: client 2889[0:0] has disconnected
acpid: client 2889[0:0] has disconnected
acpid: client connected from 3034[0:0]
acpid: 1 client rule loaded
acpid: client connected from 3034[0:0]
acpid: 1 client rule loaded
pulseaudio[1919]: module-alsa-card.c: Failed to find a working profile.
pulseaudio[1919]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
gdm-simple-greeter[3075]: Gtk-WARNING: /build/buildd/gtk+3.0-3.0.8/./gtk/gtkwidget.c:6786: widget not within a GtkWindow
gdm-simple-greeter[3075]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
gdm-simple-greeter[3075]: Gdk-WARNING: gdk_xsettings_watch_cb(): Couldn't find window to unwatch
gnome-session[3057]: WARNING: Application 'gnome-settings-daemon.desktop' killed by signal

---

### Post by kingdogbert on 2011-05-02
Try installing gnome-shell and then using the "Ubuntu Gnome Shell" (or similar; I don't remember the exact wording) environment.

---

### Post by shatil06 on 2011-05-02
Hi,

Thanks for your reply. 
I found there was some problem in gdm, i had installed kdm as default manager and it works fine.
However i have upgraded using option upgrade from "Ubuntu 11.04 to Ubuntu 11.04" of Ubuntu 11.04 released version cd.

Thanks, Minhaz

---

