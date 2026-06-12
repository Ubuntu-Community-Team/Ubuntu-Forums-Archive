---
title: "Question about sudo dpkg-reconfigure linux-image-2.6.32-21-generic"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by mbuller10 on 2010-05-02
I did the following command while I had my partition mounted and was not able to restart until i pulled the power. sudo dpkg-reconfigure linux-image-2.6.32-21-generic. Everything seems to be working okay now but before I start getting into 10.04 i wanna make sure i just didn't screw anything up. Please Help.

---

### Post by mbuller10 on 2010-05-02
bump

---

### Post by dino99 on 2010-05-02
why did you need to make that ?

sudo dpkg --configure -a
sudo apt-get install -f

look at .xsession-errors and logs (system admin log viewer) to see if troubles are logged

---

### Post by mbuller10 on 2010-05-02
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
_IceTransmkdir: Owner of /tmp/.ICE-unix should be set to root
GNOME_KEYRING_CONTROL=/tmp/keyring-jcVXea
SSH_AUTH_SOCK=/tmp/keyring-jcVXea/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-jcVXea
SSH_AUTH_SOCK=/tmp/keyring-jcVXea/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-jcVXea
SSH_AUTH_SOCK=/tmp/keyring-jcVXea/ssh
Window manager warning: Failed to read saved session file /home/max/.config/metacity/sessions/10ea6227589156f61e127281911015087400000024800028.ms: Failed to open file '/home/max/.config/metacity/sessions/10ea6227589156f61e127281911015087400000024800028.ms': No such file or directory

(polkit-gnome-authentication-agent-1:2553): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2553): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:2547): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.0/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x946e680'
** (nm-applet:2551): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2551): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2551): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-gdu extension
** (nm-applet:2551): DEBUG: foo_client_state_changed_cb
** (nm-applet:2551): DEBUG: foo_client_state_changed_cb

** (gnome-screensaver:2704): WARNING **: screensaver already running in this session

(gnome-terminal:2738): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
evolution-alarm-notify-Message: Setting timeout for 43660 1272862800 1272819140
evolution-alarm-notify-Message:  Mon May  3 00:00:00 2010

evolution-alarm-notify-Message:  Sun May  2 11:52:20 2010

** (rhythmbox:2796): DEBUG: Loading the real store page
** (rhythmbox:2796): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)

(rhythmbox:2796): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2796): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2796): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2796): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2796): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2796): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed
** (rhythmbox:2796): DEBUG: navigation requested to [http://stores.7digital.com/default.aspx?shop=480&partner=983](http://stores.7digital.com/default.aspx?shop=480&partner=983)
** (update-notifier:2825): DEBUG: Skipping reboot required
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4a00007 specified for 0x4a0001e (Warning - ).
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4a00007 specified for 0x4a00056 (Facebook U).
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4a00007 specified for 0x4a0005f (Facebook U).

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4a0006e specified for 0x4a00073 (Warning - ).

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4e00024 (Contact Li)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2721): Gdk-WARNING **: XID collision, trouble ahead
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4a00090 specified for 0x4a00095 (Warning - ).
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(gnome-terminal:3495): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3810): Gdk-WARNING **: XID collision, trouble ahead
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4e00be3 (brother)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(gnome-terminal:4189): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

---

