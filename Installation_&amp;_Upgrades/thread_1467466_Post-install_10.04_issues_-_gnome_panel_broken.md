---
title: "Post-install 10.04 issues - gnome panel broken"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Chris Sharman on 2010-04-30
I had ubuntu 9 already, but chose to do a clean install in a different partition (with the same /home partition). Call me paranoid, but I like to have a line of retreat! Went well - detected my old ubuntu & w2k - I let it inherit settings because it mentioned firefox, & I thought I'd like to keep my bookmarks.
It comes up (after autologin) with the top panel broken.
Right click/properties/background/change fixes it.
The .xsession.errors are below.
I had installed thunderbird 3 via ubuntuzilla, and some of the errors below look like they've come from there.

Any suggestions on how to fix the panel? It's a pain to have to fiddle it every login.

Thanks
Chris

PS: Other comments:
1. Had to install thunderbird! sure I read 10.04 included t'bird v3?
2. Didn't recognise my scanner (epson stylus sx415). Fixed by downloading iscan from epson - simple scanner now works - but I preferred xsane.
Like being able to preview, trim, rotate before saving.
3. My eyetoy still doesn't seem to work (although I haven't installed skype yet).
4. Ubuntu's still great - years since I booted w2k, i'd almost forgotten it was on there!

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-x2abrW
GNOME_KEYRING_PID=1176
GNOME_KEYRING_CONTROL=/tmp/keyring-x2abrW
GNOME_KEYRING_CONTROL=/tmp/keyring-x2abrW
SSH_AUTH_SOCK=/tmp/keyring-x2abrW/ssh

(polkit-gnome-authentication-agent-1:1200): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1200): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Initializing nautilus-gdu extension
Unable to find a synaptics device.
Unable to open desktop file /usr/share/applications/thunderbird-mozilla-build.desktop for panel launcher: No such file or directory
/usr/bin/compiz (core) - Warn: Exceeded max texture size
Starting gtk-window-decorator
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (update-notifier:1393): DEBUG: Skipping reboot required
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by tonus on 2010-05-14
Looks like this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/574247]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/574247")
I have the same problem on a relatively old PC with a Matrox G450 graphics card, fresh Lucid install.
My .xsession-errors below:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=nl_NL.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-pblOtq
GNOME_KEYRING_CONTROL=/tmp/keyring-pblOtq
SSH_AUTH_SOCK=/tmp/keyring-pblOtq/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-pblOtq
SSH_AUTH_SOCK=/tmp/keyring-pblOtq/ssh

(polkit-gnome-authentication-agent-1:1261): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1261): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1260): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x85da6e0'
** (nm-applet:1258): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1258): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Initializing nautilus-gdu extension
/usr/bin/compiz (core) - Warn: Exceeded max texture size
Starting gtk-window-decorator

(gnome-settings-daemon:1244): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
evolution-alarm-notify-Message: Setting timeout for 39919 1273881600 1273841681
evolution-alarm-notify-Message:  Sat May 15 02:00:00 2010

evolution-alarm-notify-Message:  Fri May 14 14:54:41 2010

** (update-notifier:1391): DEBUG: Skipping reboot required

---

### Post by alcarola on 2010-07-18
I have the problem too.

Linux kamikaze2 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G550 AGP (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 82)

---

### Post by alcarola on 2010-07-18
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/572550](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/572550)

---

