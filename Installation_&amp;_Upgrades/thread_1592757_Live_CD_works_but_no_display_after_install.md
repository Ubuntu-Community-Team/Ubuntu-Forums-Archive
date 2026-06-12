---
title: "Live CD works but no display after install"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by mattTheNewb on 2010-10-10
Hi guys,

I have this problem where the 10.10 LiveCD 64-bit works (as in I get full resolution display and no video issues at all). But after install, the OS boots successfully but there's no display. I know it's successful because I was able to login in the dark (sound works).

Here's what I have:
HP m9340f (NVIDIA GeForce 9500M GS with HDMI)
46" Sharp connected via HDMI
Windows 7, works fine.

Here's what I tried with no luck:
1. CTRL-ALT-F1 still doesn't show anything on screen, no terminal
2. Connected via VGA
3. Connected another 17" monitor via VGA, rebooted
4. Added vga=789 in grub before booting

The weird thing is that I had 10.04 before and it was working for a while then it suddenly stopped working. I figured I'd wait until 10.10 but I now have the same issue. I haven't tried 32-bit... I can give that a shot in a bit.

Any ideas?](*,)

---

### Post by VMC on 2010-10-10
Boot up using the livecd again and go to your home folder of the one that doesn't work and output the file ".xsession-errors". something in there may give us clues to what's going on.

---

### Post by mattTheNewb on 2010-10-11
Here it is... no manageable screens found??

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-cmjxPv
GNOME_KEYRING_CONTROL=/tmp/keyring-cmjxPv
GNOME_KEYRING_CONTROL=/tmp/keyring-cmjxPv
SSH_AUTH_SOCK=/tmp/keyring-cmjxPv/ssh

(polkit-gnome-authentication-agent-1:1953): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1953): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
/usr/bin/compiz (core) - Fatal: Software rendering detected.
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0
** (nm-applet:1964): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1964): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Initializing nautilus-gdu extension

(nautilus:1958): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: applet now embedded in the notification area
/usr/lib/python2.6/dist-packages/UpdateManager/SimpleGtkbuilderApp.py:35: GtkWarning: Ignoring the separator setting
  self.builder.add_from_file(path)
** (update-notifier:2139): DEBUG: aptdaemon on bus: 0
** (update-notifier:2139): DEBUG: Skipping reboot required
WARNING:root:timeout reached, exiting

```

---

### Post by mattTheNewb on 2010-10-12
Seems to be related to the nvidia driver. I think I remember an update to the driver when all this started on 10.04. I only tried 10.10 since which probably has the same update or newer. I don't know to change drivers though if I can't see anything...

I tried 32-bit and 64-bit.

What driver is the live cd using?

---

### Post by mattTheNewb on 2010-10-24
Same problem with Kubuntu.

Any ideas anyone? :(

---

### Post by mattTheNewb on 2010-10-28
Here's the Xorg.0.log from /var/log/:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux matt-kubuntu 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=58d390a7-0a67-4665-9f82-92fd84f0c484 ro vga=791 quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 24 09:15:02 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 8


Fatal server error:
xf86OpenConsole: VT_WAITACTIVE failed: Interrupted system call


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

Okay. Found this: [HTML]https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/441653[/HTML]

I've tried everything from that page and still no luck :( I've never had a successful boot since some kernel update on 10.04.

---

