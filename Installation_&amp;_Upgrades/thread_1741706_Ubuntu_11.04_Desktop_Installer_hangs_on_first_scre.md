---
title: "Ubuntu 11.04 Desktop Installer hangs on first screen"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by egandt on 2011-04-28
After booting I select Install and then get the "Preparing to Install Ubuntu" dialog box from which I can check or not check to include third party products.  I have tried both ways, and have not yet gotten beyond this screen.  
The installer just sits on this screen until I reboot, the installer can not be exited (I have waited over 30 minutes at one point before rebooting).  Looking at the logs (in /var/log/install) I see nothing of note in the file debug, but in the dm file I see messages such as those below.  I thought the problem might be accessing the network, as if I select third party, I get error finding Nivida ATI and basically any other third party items.  Yet even without a network connection (and without selecting these options) it still hangs on this screen.


dm:
** (panel:3089): DEBUG: Looking at Module: /usr/lib/indicators/5/libsession.so
** (panel:3089): DEBUG: Loading Module: /usr/lib/indicators/5/libsession.so
** (panel:3089): DEBUG: Signal: Entry Added
** (panel:3089): DEBUG: Looking at Module: /usr/lib/indicators/5/libapplication.so
** (panel:3089): DEBUG: Loading Module: /usr/lib/indicators/5/libapplication.so
** (panel:3089): DEBUG: Looking at Module: /usr/lib/indicators/5/libsoundmenu.so
** (panel:3089): DEBUG: Loading Module: /usr/lib/indicators/5/libsoundmenu.so

(panel:3089): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** (panel:3089): DEBUG: Signal: Entry Added
(panel:3089): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(panel:3089): Indicator-Application-DEBUG: Request current apps
(panel:3089): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget

(panel:3089): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(panel:3089): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(panel:3089): GLib-CRITICAL **: g_variant_get_double: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_DOUBLE)' failed

(panel:3089): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(panel:3089): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(panel:3089): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
(panel:3089): Indicator-Sound-DEBUG: indicator-sound: new_voip_slider_widget

(panel:3089): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(panel:3089): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(panel:3089): GLib-CRITICAL **: g_variant_get_double: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_DOUBLE)' failed

(panel:3089): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(panel:3089): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(panel:3089): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed
(panel:3089): Indicator-Sound-DEBUG: new_title_widget ("Banshee")
(panel:3089): Indicator-Sound-DEBUG: indicator-sound: new_metadata_widget
(panel:3089): Indicator-Sound-DEBUG: indicator-sound: new_transport_bar() called 

(panel:3089): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(panel:3089): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(panel:3089): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(panel:3089): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed

(panel:3089): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(panel:3089): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(panel:3089): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed
(panel:3089): Indicator-Sound-DEBUG: voip-item-widget - update mute with value 0
** (nm-applet:3090): DEBUG: foo_client_state_changed_cb
(panel:3089): Indicator-Application-DEBUG: Building new application entry: :1.13  with icon: nm-device-wired at position 0
** (panel:3089): DEBUG: Signal: Entry Added

(panel:3089): GLib-CRITICAL **: g_variant_get_string: assertion `value != NULL' failed

(panel:3089): GLib-GIO-CRITICAL **: g_themed_icon_new_with_default_fallbacks: assertion `iconname != NULL' failed

(panel:3089): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed



I had previously installed 11.04Beta2 server on the box to ensure that it would install and boot on a new P67 based MB using UEFI.  However this is a desktop, and I'd prefer starting with the Desktop edition of Ubuntu.

ERIC

---

### Post by manzdagratiano on 2011-04-28
I do not know much about what exactly is wrong here, but I had a similar hang-up issue when I tried to install Lucid/Maverick on a few new laptops. In my case, the 32-bit install kept on stalling, so I tried the 64-bit versions, which immediately proceeded as normal. I would suggest you give that a shot.

---

### Post by egandt on 2011-04-28
I got past the problem, by installing server and then installing ubuntu-desktop.  Not the best way, but one that will work.

ERIC

---

### Post by mörgæs on 2011-04-28
Good, please mark the thread 'solved'.

---

### Post by NormanFLinux on 2011-05-12
Exactly what server package did you use for the workaround?

I have the same issue.... Ubiquity just hangs on the first screen and doesn't advance.

---

### Post by NormanFLinux on 2011-05-12
Its not really solved. I even turned off my wireless LAN and Ubiquity still sits there and spins at the preparing to install Ubuntu screen.

If any one has found a workaround to get Ubiquity to run, I'd like to hear it. The Broadcom driver freezes the installer.

When that's turned off in BIOS, Ubiquity still sits there.

---

### Post by mörgæs on 2011-05-13
Have you tried the alternate installer?

---

### Post by NormanFLinux on 2011-05-13
The alternative installer doesn't seem to recognize the existence of a USB stick. It complains about looking for a CD drive.

What is this - the 1990s? Seriously, Canonical hasn't even updated the text-based installer to work with USB sticks!

---

