---
title: "KDE freezes constantly, SO frustrating!"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by autumnraine on 2010-04-21
I'm at my wits end. During the Alpha stage I was able to run Kubuntu fairly well with few interrupts, except for kernel updates. Since the betas however I can't seem to use KDE at all, either the default Kubuntu install or by installing KDE minimal and other necessary packages from within Ubuntu (from a fresh install). 

Everytime I boot into the system it freezes either immediately or as soon as I open a program or two. Even just having the packages installed seems to somehow make the system more unstable, even when I'm using Gnome. 

I think it's related to boot, since if my system's been up and running for a few days it gets much more stable, whereas if I have to reboot for some reason the system's much more likely to freeze, sometimes before it even gets to the login page. 

This is on the Shuttle box listed in my sig. I know it does have some bios related issues (principally to do with usb recognition and the card read/writer) but it works perfectly with Karmic. What can I do? Would somehow disabling Plymouth help? I always try to press a key as soon as the purple screen shows up (prior to that the screen's black with a command-line) but that just brings me into the login page, which sometimes freezes, especially if it's the Kubuntu login screen. 

I've searched all the relevent forums and bug trackers but haven't seen any posts with problems similar to mine. Anyone else having this sort of issue?

---

### Post by caryb on 2010-04-21
Wish I could help but my Kubuntu 64 bit is current & I'm happy as a pig in mud! this has been a boring release for me as far as breakages. (So it should be being a long term release)

Cary

---

### Post by Kokopelli on 2010-04-21
I too regret your experience but do not share it.  I have Kubuntu Lucid running on 2 of my laptops and have little to complain on them for any reason and no lockups.  Have you checked your logs to see if maybe something is showing up in there to give a clue?

---

### Post by autumnraine on 2010-04-21
> **Kokopelli said:**
> I too regret your experience but do not share it. I have Kubuntu Lucid running on 2 of my laptops and have little to complain on them for any reason and no lockups. Have you checked your logs to see if maybe something is showing up in there to give a clue?

Thanks for the suggestion. Any particular logs I should look at as likely suspects? I've never checked logs before, though I know their location. 

These are the logs present in /var/log/:

[IMG]http://lh6.ggpht.com/_bAA2vErImEQ/S8-tH4ZnrgI/AAAAAAAAABE/IXppAb0mdq0/s800/logs.png[/IMG]

---

### Post by ankspo71 on 2010-04-22
Hi,
I'm not very good at deciphering log files, and relatively new to KDE, but I have been able to pinpoint a few problems before in ./home/<user>/.xsession-errors while using Ubuntu before. The last few lines might give a clue about something wrong after the next time the system hangs. As far as I know, it is normal to see some random (but usually minor) errors in there, so don't be surprised to find alot of error messages.

Also, do you have any crash logs in /var/crash? 

By any chance, are you letting ubiquity format your drive, or are you using gparted to format your drive in advance before installing?

As of 2 weeks ago, I was still having my problems with the partitioner in the Ubiquity installer. It's wasn't crashing like it used to anymore but it is not partitioning my drives as exactly as I tell it to do (both kubuntu and Ubuntu). It creates a 1mb unoccupied space before my primary partition, and I think it was the cause of my slower than normal boot time and poor performance in Ubuntu (at the time I discovered it). Formating my drives with gparted before installing Ubuntu/Kubuntu eliminated this unoccupied space for me. You can see if you have that problem by installing gparted and looking over your partitions.

I hope I said something that will help.

---

### Post by autumnraine on 2010-04-22
Good suggestions. var/crash/ doesn't hold anything significant (just a PlayonLinux crash report) but .xsession-errors seems to hold some stuff of concern: 

Xsession: X session started for autumn at Wed Apr 21 17:21:46 EDT 2010
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-VHMUmq
GNOME_KEYRING_PID=1666
GNOME_KEYRING_CONTROL=/tmp/keyring-VHMUmq

(polkit-gnome-authentication-agent-1:1680): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1680): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Initializing nautilus-gdu extension

(gnome-power-manager:1688): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.0/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x1a999c0'

** (gnome-power-manager:1688): WARNING **: Either HAL or DBUS are not working!

** (gnome-power-manager:1688): WARNING **: proxy failed

** (gnome-power-manager:1688): WARNING **: failed to get Computer root object

** (gnome-power-manager:1688): WARNING **: proxy NULL!!
/usr/bin/compiz (core) - Fatal: Software rendering detected.
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0
Unable to find a synaptics device.
** (update-notifier:1954): DEBUG: Skipping reboot required
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3600003 specified for 0x3600027 (StartUp-Ma).
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sda11
Found Ubuntu lucid (development branch) (10.04) on /dev/sda9
done
Grub2 detected
Usplash not detected
Splashy not detected
qUncompress: Z_DATA_ERROR: Input data is corrupted
qUncompress: Input data is corrupted
basket(3582): ""lastBackup" - conversion of "-4713,1,1" to QDate failed" 
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kbuildsycoca4(3594) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(3594) KBuildSycoca::checkTimestamps: timestamps check ok
kbuildsycoca4(3594) kdemain: Emitting notifyDatabaseChanged ()
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kglobalaccel.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(3597) GlobalShortcutsRegistry::loadSettings: Loading group  "kwin"
kglobalaccel(3597) GlobalShortcutsRegistry::loadSettings: Loading group  "krunner"
kglobalaccel(3597) GlobalShortcutsRegistry::loadSettings: Loading group  "plasma-desktop"
kglobalaccel(3597) GlobalShortcutsRegistry::loadSettings: Loading group  "basket"
kglobalaccel(3597) GlobalShortcutsRegistry::loadSettings: Loading group  "khotkeys"
kglobalaccel(3597) GlobalShortcutsRegistry::loadSettings: Loading group  "kded"
kglobalaccel(3597) GlobalShortcutsRegistry::loadSettings: Loading group  "klipper"
kglobalaccel(3597) GlobalShortcutsRegistry::loadSettings: Loading group  "ktorrent"
kglobalaccel(3597) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+W" for "basket" : "global_show_hide_main_window"
kglobalaccel(3597) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+V" for "basket" : "global_paste"
kglobalaccel(3597) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+S" for "basket" : "global_paste_selection"
kglobalaccel(3597) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+T" for "basket" : "global_note_add_html"
qUncompress: Z_DATA_ERROR: Input data is corrupted
qUncompress: Input data is corrupted
qUncompress: Input data is corrupted
qUncompress: Input data is corrupted
qUncompress: Input data is corrupted
qUncompress: Input data is corrupted
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(3582)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.74'
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket25" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
basket(3582)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/autumn/MyFiles/Documents/Basket Notes/baskets/basket8" 
qUncompress: Z_DATA_ERROR: Input data is corrupted
qUncompress: Input data is corrupted

x-session-errors.old has more stuff related to KDE, even though I installed Ubuntu with gnome first (don't understand that - maybe from a previous install): 

Xsession: X session started for autumn at Wed Apr 21 11:42:55 EDT 2010
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kbuildsycoca4(1734) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(1734) KBuildSycoca::checkTimestamps: timestamps check ok
kbuildsycoca4(1734) kdemain: Emitting notifyDatabaseChanged ()
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QObject::connect: Cannot connect (null)::accessibilityChanged(bool, const QString) to DeviceAutomounter::deviceMountChanged(bool, const QString)
QObject::connect: Cannot connect (null)::accessibilityChanged(bool, const QString) to DeviceAutomounter::deviceMountChanged(bool, const QString)
kded(1733)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kded(1733)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_hal_power.so" does not offer a qt_plugin_instance function.
Invalid D-BUS member name 'idle-hint' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'is-local' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'remote-host-name' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'session-type' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'unix-user' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kglobalaccel.so
kglobalaccel(1852) GlobalShortcutsRegistry::loadSettings: Loading group  "kwin"
kglobalaccel(1852) GlobalShortcutsRegistry::loadSettings: Loading group  "krunner"
kglobalaccel(1852) GlobalShortcutsRegistry::loadSettings: Loading group  "plasma-desktop"
kglobalaccel(1852) GlobalShortcutsRegistry::loadSettings: Loading group  "basket"
kglobalaccel(1852) GlobalShortcutsRegistry::loadSettings: Loading group  "khotkeys"
kglobalaccel(1852) GlobalShortcutsRegistry::loadSettings: Loading group  "kded"
kglobalaccel(1852) GlobalShortcutsRegistry::loadSettings: Loading group  "klipper"
kglobalaccel(1852) GlobalShortcutsRegistry::loadSettings: Loading group  "ktorrent"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kded(1733)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Object::connect: No such signal Solid::Button::pressed(int, const QString &)
kded(1733)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kcminit_startup.so
Object::connect: No such signal Solid::Button::pressed(int, const QString &)
kded(1733)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Object::connect: No such signal Solid::Button::pressed(int, const QString &)
kded(1733)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Object::connect: No such signal Solid::Button::pressed(int, const QString &)
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.5'
kdeinit4: preparing to launch /usr/lib/libkdeinit4_ksmserver.so
<unknown program name>(1730)/ KStartupInfo::createNewStartupId: creating:  "autumn-desktop;1271864597;24013;1730_TIME0" : "unnamed app"
kephald starting up 
XRANDR error base:  165 
RRInput mask is set!! 
RandRScreen::loadSettings - adding mode:  99 1920 x 1080 
RandRScreen::loadSettings - adding mode:  100 1600 x 1200 
RandRScreen::loadSettings - adding mode:  101 1680 x 1050 
RandRScreen::loadSettings - adding mode:  102 1280 x 1024 
RandRScreen::loadSettings - adding mode:  103 1440 x 900 
RandRScreen::loadSettings - adding mode:  104 1280 x 960 
RandRScreen::loadSettings - adding mode:  105 1280 x 800 
RandRScreen::loadSettings - adding mode:  106 1280 x 720 
RandRScreen::loadSettings - adding mode:  107 1280 x 720 
RandRScreen::loadSettings - adding mode:  108 1024 x 768 
RandRScreen::loadSettings - adding mode:  109 800 x 600 
RandRScreen::loadSettings - adding mode:  110 800 x 600 
RandRScreen::loadSettings - adding mode:  111 720 x 576 
RandRScreen::loadSettings - adding mode:  112 720 x 480 
RandRScreen::loadSettings - adding mode:  113 640 x 480 
RandRScreen::loadSettings - adding crtc:  95 
RandRScreen::loadSettings - adding crtc:  96 
RandRScreen::loadSettings - adding output:  97 
Setting CRTC 0 on output "VGA-1" (previous 0 ) 
RandRScreen::loadSettings - adding output:  98 
Setting CRTC 95 on output "DVI-D-1" (previous 0 ) 
CRTC outputs: (98) 
Output name: "DVI-D-1" 
Output refresh rate: 60 
Output rect: QRect(0,0 1920x1080) 
Output rotation: 1 
XRandROutputs::init 
  added output  97 
  added output  98 
output: "DVI-D-1" QRect(0,0 1920x1080) 0 false false 
output: "VGA-1" QRect(0,0 0x0) 0 false false 
load xml 
connected: 1 
looking for current "DVI-D-1" 
known "*" has score: 0.25 
screen: 0 QRect(0,0 1920x1080) 
looking for a matching configuration... 
connected: 1 
looking for current "DVI-D-1" 
known "*" has score: 0.25 
found outputs, known: false 
connected: 1 
looking for current "DVI-D-1" 
known "*" has score: 0.25 
activate external configuration!! 
registered the service: true 
screens registered on the bus: true 
outputs registered on the bus: true 
configurations registered on the bus: true 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Right" for "kwin" : "Switch Window Right"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Left" for "kwin" : "Switch Window Left"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kdeinit4: preparing to launch /usr/bin/knotify4
kdeinit4: preparing to launch /usr/lib/libkdeinit4_plasma-desktop.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusObjectPath: invalid path ""
knotify(1861) KNotify::event: 1  ref= 0
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F1" for "plasma-desktop" : "activate widget 4"
QGraphicsLinearLayout::removeAt: invalid index 0
plasma-desktop(1862)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "systemsettings" not found
plasma-desktop(1862)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/autumn/.kde/share/apps/RecentDocuments/temp notes for some pages of the history of the computer (ceruzzi).desktop" not found
plasma-desktop(1862)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/autumn/.kde/share/apps/RecentDocuments/Paul E. Ceruzzi. A History of Modern Computing 2nd Ed.pdf.desktop" not found
plasma-desktop(1862)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/autumn/.kde/share/apps/RecentDocuments/Concept of Mind 60th.torrent.desktop" not found
plasma-desktop(1862)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/autumn/.kde/share/apps/RecentDocuments/Backup.desktop" not found
plasma-desktop(1862)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_hal_power.so" does not offer a qt_plugin_instance function.
kded(1733)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_networkmanager07.so" does not offer a qt_plugin_instance function.
plasma-desktop(1862)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-3, -2) 
plasma-desktop(1862)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-3, -2) 
plasma-desktop(1862)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-3, -2) 
knotify(1861) NotifyByPopup::slotServiceOwnerChanged: "org.freedesktop.Notifications" "" ":1.12"
knotify(1861) KNotify::event: 2  ref= 0
Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_desktop.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kio_desktop(1866)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kio_desktop(1866)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/autumn/.local/share/mime/magic"
kcminit(1854)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_kpk_addrm.so"
kcminit(1854)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_emoticons.so"
kcminit(1854)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_hotkeys.so"
kcminit(1854)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_kpk_settings.so"
kcminit(1854)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_kpk_update.so"
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kaccess.so
<unknown program name>(1871)/ kdemain: Xlib XKB extension major= 1  minor= 0
kcminit(1854)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcminit_nsplugins.so"
kdeinit4: preparing to launch /usr/bin/nspluginscan
kaccess(1871) kdemain: X server XKB extension major= 1  minor= 0
plasma-desktop(1862)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
plasma-desktop(1862)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/autumn/.local/share/mime/magic"
kglobalaccel(1852) KGlobalAccelImpl::x11Event: Got XMappingNotify event
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Right" for "kwin" : "Switch Window Right"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Left" for "kwin" : "Switch Window Left"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F1" for "plasma-desktop" : "activate widget 4"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1852) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Right" for "kwin" : "Switch Window Right"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Left" for "kwin" : "Switch Window Left"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F1" for "plasma-desktop" : "activate widget 4"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kcminit(1854)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_keys.so"
kdeinit4: preparing to launch /usr/lib/libkdeinit4_nepomukserver.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_krunner.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/bin/kwrited
kdeinit4: preparing to launch /bin/sh
kdeinit4: preparing to launch /usr/lib/kde4/libexec/polkit-kde-authentication-agent-1
kdeinit4: preparing to launch /usr/bin/start-pulseaudio-x11
kdeinit4: preparing to launch /usr/bin/wicd-gtk
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klipper.so
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Print" for "khotkeys" : "{131a0180-4901-4e45-8fc1-445a201537e1}"
kglobalaccel(1852) KdeDGlobalAccel::Component::cleanUp: 1
knotify(1861) NotifyBySound::notify:  going to play  "/usr/share/sounds/KDE-Sys-Log-In-Short.ogg"
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
New PolkitAgentListener  0x81aca0 
Adding new listener  PolkitQt1::Agent::Listener(0x94a020) for  0x81aca0 

(process:1914): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(process:1914): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
[/usr/bin/nepomukservicestub] Using Virtuoso Version: "6.1.0.3126-pthreads"
[/usr/bin/nepomukservicestub] Using Virtuoso Version: "6.1.0.3126-pthreads"
[/usr/bin/nepomukservicestub] void Soprano::VirtuosoController::writeConfigFile(const QString&, const Soprano::BackendSettings&) "/home/autumn/.cache/virtuoso_hX1895.ini"
[/usr/bin/nepomukservicestub] Starting Virtuoso server: "/usr/lib/virtuoso/virtuoso-t" ("+foreground", "+configfile", "/home/autumn/.cache/virtuoso_hX1895.ini", "+wait")
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+V" for "klipper" : "show_klipper_popup"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+R" for "klipper" : "repeat_action"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+X" for "klipper" : "clipboard_action"
[/usr/bin/nepomukservicestub] "
"
[/usr/bin/nepomukservicestub] "        Wed Apr 21 2010
" 
"11:43:30 OpenLink Virtuoso Universal Server
" 
"11:43:30 Version 06.01.3126-pthreads for Linux as of Feb 19 2010
" 
"11:43:30 uses parts of OpenSSL, PCRE, Html Tidy
"
nspluginscan(1944)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib/mozilla/plugins/libjavaplugin.so"
kglobalaccel(1852) KGlobalAccelDPrivate::_k_newGlobalShortcutNotification: Showing Notification for component "klipper"
nspluginscan(1945)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so"
[/usr/bin/nepomukservicestub] "11:43:30 Database version 3126
"
nspluginscan(1946)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib/mozilla/plugins/libtotem-cone-plugin.so"
nspluginscan(1952)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so"
[/usr/bin/nepomukservicestub] "11:43:31 Entering Lite Mode
" 
"11:43:31 SQL Optimizer enabled (max 1000 layouts)
"
nspluginscan(1955)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib/mozilla/plugins/libtotem-mully-plugin.so"
nspluginscan(1956)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so"
nspluginscan(1970)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib64/mozilla/plugins/libjavaplugin.so"
nspluginscan(1971)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib64/mozilla/plugins/librhythmbox-itms-detection-plugin.so"
nspluginscan(1973)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib64/mozilla/plugins/libtotem-cone-plugin.so"
nspluginscan(1974)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib64/mozilla/plugins/libtotem-gmp-plugin.so"
nspluginscan(1975)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib64/mozilla/plugins/libtotem-mully-plugin.so"
nspluginscan(1976)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "/usr/lib64/mozilla/plugins/libtotem-narrowspace-plugin.so"
QGraphicsLinearLayout::removeAt: invalid index 1
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F2" for "krunner" : "Run Command"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F2" for "krunner" : "Run Command on clipboard contents"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Esc" for "krunner" : "Show System Activity"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Ins" for "krunner" : "Switch User"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+L" for "krunner" : "Lock Session"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Del" for "krunner" : "Log Out"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+Del" for "krunner" : "Log Out Without Confirmation"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgDown" for "krunner" : "Halt Without Confirmation"
kglobalaccel(1852) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgUp" for "krunner" : "Reboot Without Confirmation"
"/usr/bin/kdeinit4(1896)" Error in thread 140386872239968 : "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/kdeinit4(1896)" Error in thread 140386872239968 : "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/kdeinit4(1896)" Error in thread 140386872239968 : "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/kdeinit4(1896)" Error in thread 140386872239968 : "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/kdeinit4(1896)" Error in thread 140386872239968 : "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/kdeinit4(1896)" Error in thread 140386872239968 : "QLocalSocket::connectToServer: Connection refused"
[/usr/bin/nepomukservicestub] "11:43:32 Compiler unit is timed at 0.000979 msec
"
krunner(1896)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "" not found
[/usr/bin/nepomukservicestub] "11:43:33 Roll forward started
" 
"11:43:33 Roll forward complete
"
[/usr/bin/nepomukservicestub] "11:43:33 Checkpoint started
"
[/usr/bin/nepomukservicestub] "11:43:33 Checkpoint finished, log reused
"
[/usr/bin/nepomukservicestub] "11:43:36 Server online at 1111 (pid 1924)
"
[/usr/bin/nepomukservicestub] Virtuoso started: 1924
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() QThread(0xedd160)
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(1895)" Error in thread 139784228005728 : "SQLGetData for data lenght failed (iODBC Error: [OpenLink][Virtuoso iODBC Driver]CL056: Bookmarks not enable for statement)"
[/usr/bin/nepomukservicestub] bool Soprano::Virtuoso::DatabaseConfigurator::updateFulltextIndexRules(bool) empty rule name!
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() QThread(0xedd160)
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() QThread(0xedd160)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::slotNewSocketConnection() 
void Soprano::Server::ServerCore::Private::handleIncomingConnection(QIODevice*) 
void Soprano::Server::ServerCore::Private::handleIncomingConnection(QIODevice*) New connection. New count: 1
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::slotNewSocketConnection() 
void Soprano::Server::ServerCore::Private::handleIncomingConnection(QIODevice*) 
void Soprano::Server::ServerCore::Private::handleIncomingConnection(QIODevice*) New connection. New count: 2 
void Soprano::Server::ServerCore::slotNewSocketConnection() 
void Soprano::Server::ServerCore::Private::handleIncomingConnection(QIODevice*) 
void Soprano::Server::ServerCore::Private::handleIncomingConnection(QIODevice*) New connection. New count: 3 
Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x7f21f80045e0) 
void Soprano::Server::ServerCore::slotNewSocketConnection() 
void Soprano::Server::ServerCore::Private::handleIncomingConnection(QIODevice*) 
void Soprano::Server::ServerCore::Private::handleIncomingConnection(QIODevice*) New connection. New count: 4 
Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x7f21f8006410)
[/usr/bin/nepomukservicestub] Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
[/usr/bin/nepomukservicestub] Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(1997)" Error in thread 140636833703776 : "Parsing failed (3)": "syntax error at '"'" (line: 459, column: -1)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
<unknown program name>(1730)/ KStartupInfo::createNewStartupId: creating:  "autumn-desktop;1271864622;328665;1730_TIME0" : "unnamed app"
kbuildsycoca4 running...
kbuildsycoca4(2007) kdemain: Reusing existing ksycoca
kbuildsycoca4(2007) KBuildSycoca::recreate: Recreating ksycoca file ("/var/tmp/kdecache-autumn/ksycoca4", version 162)
kbuildsycoca4(2007) KBuildSycoca::createEntry: modified: "nsplugin.desktop"
kbuildsycoca4(2007) KBuildSycoca::createEntry: new: "screensaver.desktop"
kbuildsycoca4(2007) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/autumn/.config/menus/applications-merged/wine-Programs-PDF-XChange PDF Viewer-PDF-Viewer.menu"
kbuildsycoca4(2007) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/autumn/.config/menus/applications-merged/wine-Programs-PDF-XChange PDF Viewer-PDF-Viewer Users Manual.menu"
kbuildsycoca4(2007) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/autumn/.config/menus/applications-merged/wine-Programs-PDF-XChange PDF Viewer-PDF-Viewer License.menu"
kbuildsycoca4(2007) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/autumn/.config/menus/applications-merged/playonlinux-Programmes.menu"
kbuildsycoca4(2007) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/autumn/.config/menus/applications-merged/wine-Programs-PDF-XChange PDF Viewer.menu"
kbuildsycoca4(2007) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/autumn/.config/menus/applications-merged/wine-Programs-PDF-XChange PDF Viewer-Uninstall.menu"
kbuildsycoca4(2007) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/applications-merged/wine.menu"
kbuildsycoca4(2007) VFolderMenu::pushDocInfo: Menu "debian-menu.menu" not found.
kbuildsycoca4(2007) VFolderMenu::pushDocInfo: Menu "applications-kmenuedit.menu" not found.
kbuildsycoca4(2007) VFolderMenu::processMenu: Processing KDE Legacy dirs for <KDE>
kbuildsycoca4(2007) VFolderMenu::processKDELegacyDirs:
kbuildsycoca4(2007) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/"
kbuildsycoca4(2007) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/screensavers"
kbuildsycoca4(2007) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/kde4"
kbuildsycoca4(2007) VFolderMenu::loadApplications: Looking up applications under "/home/autumn/.local/share/applications/"
kbuildsycoca4(2007) VFolderMenu::loadApplications: Looking up applications under "/home/autumn/.local/share/applications/wine"
kbuildsycoca4(2007) VFolderMenu::loadApplications: Looking up applications under "/home/autumn/.local/share/applications/wine/Programs"
kbuildsycoca4(2007) VFolderMenu::loadApplications: Looking up applications under "/home/autumn/.local/share/applications/wine/Programs/PDF-XChange PDF Viewer"
kbuildsycoca4(2007) KBuildMimeTypeFactory::parseAliasFile: Ignoring alias "application/vnd.ms-asf" because also defined as a real mimetype
kbuildsycoca4(2007) KBuildMimeTypeFactory::parseAliasFile: Ignoring alias "application/x-kexiproject-sqlite" because also defined as a real mimetype
kbuildsycoca4(2007) KBuildMimeTypeFactory::parseAliasFile: Ignoring alias "application/x-ogg" because also defined as a real mimetype
kbuildsycoca4(2007) KBuildMimeTypeFactory::parseAliasFile: Ignoring alias "application/x-vnd.kde.kexi" because also defined as a real mimetype
kbuildsycoca4(2007) KBuildMimeTypeFactory::parseAliasFile: Ignoring alias "audio/m3u" because also defined as a real mimetype
kbuildsycoca4(2007) KBuildMimeTypeFactory::parseAliasFile: Ignoring alias "audio/vorbis" because also defined as a real mimetype
kbuildsycoca4(2007) KBuildMimeTypeFactory::parseAliasFile: Ignoring alias "audio/x-mp2" because also defined as a real mimetype
kbuildsycoca4(2007) KBuildMimeTypeFactory::parseAliasFile: Ignoring alias "audio/x-oggflac" because also defined as a real mimetype
kbuildsycoca4(2007) KBuildMimeTypeFactory::parseAliasFile: Ignoring alias "video/x-ogm" because also defined as a real mimetype
kbuildsycoca4(2007) KBuildMimeTypeFactory::parseAliasFile: Ignoring alias "video/x-theora" because also defined as a real mimetype
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-7z-compressed-tar"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ar"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1-compressed-tar"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-cabinet"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ear"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-lzip-compressed-tar"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-lzop-compressed-tar"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rar-compressed"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rzip"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-war"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/nautilus-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/gnome-default-handler"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/nautilus-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/normal"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/home/autumn/.local/share/applications/BasKet Note Pads.desktop" specifies undefined mimetype/servicetype "application/x-basket-archive"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/home/autumn/.local/share/applications/BasKet Note Pads.desktop" specifies undefined mimetype/servicetype "application/x-basket-template"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-quicktime"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mkv"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/aiff"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-basic"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-8svx"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/8svx"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-16sv"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/168sv"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/ilbm"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/anim"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mng"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg2"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg2"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg3"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "x-mpegurl"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/amarok_append.desktop" specifies undefined mimetype/servicetype "audio/*"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/kpackagekit.desktop" specifies undefined mimetype/servicetype "application/x-servicepack"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/amarok.desktop" specifies undefined mimetype/servicetype "application/x-ogm-audio"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "okularMobi.desktop" specifies undefined mimetype/servicetype "application/x-mobipocket-ebook"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/brasero.desktop" specifies undefined mimetype/servicetype "application/x-toc"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/evince.desktop" specifies undefined mimetype/servicetype "image/*"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/soundconverter.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/jpg"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-gray"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.slideshow.macroEnabled.12"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroEnabled.12"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroEnabled.12"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroEnabled.12"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-calc.desktop" specifies undefined mimetype/servicetype "application/csv"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-calc.desktop" specifies undefined mimetype/servicetype "application/excel"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-calc.desktop" specifies undefined mimetype/servicetype "application/tab-separated-values"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-calc.desktop" specifies undefined mimetype/servicetype "application/x-dos_ms_excel"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-calc.desktop" specifies undefined mimetype/servicetype "application/x-excel"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-calc.desktop" specifies undefined mimetype/servicetype "application/x-ms-excel"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-calc.desktop" specifies undefined mimetype/servicetype "text/comma-separated-values"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.stardivision.writer-global"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-writer.desktop" specifies undefined mimetype/servicetype "application/x-extension-txt"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroEnabled.12"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/onboard-settings.desktop" specifies undefined mimetype/servicetype "application/x-onboardsettings"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/okularApplication_mobi.desktop" specifies undefined mimetype/servicetype "application/x-mobipocket-ebook"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/basket.desktop" specifies undefined mimetype/servicetype "application/x-basket-archive"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/basket.desktop" specifies undefined mimetype/servicetype "application/x-basket-template"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/onboard.desktop" specifies undefined mimetype/servicetype "application/x-onboard"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "application/x-extension-m4a"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "application/x-smil"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-sbc"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "video/x-ms-asx"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "video/x-totem-stream"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/ktorrent.desktop" specifies undefined mimetype/servicetype "application/x-torrent"
kbuildsycoca4(2007) KBuildServiceFactory::populateServiceTypes: "libokularGenerator_mobi.desktop" specifies undefined mimetype/servicetype "application/x-mobipocket-ebook"
kbuildsycoca4(2007) KBuildSycoca::save: Saving
kbuildsycoca4(2007) kdemain: Emitting notifyDatabaseChanged ("services")
plasma-desktop(1862)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "systemsettings" not found
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::slotNewSocketConnection() 
void Soprano::Server::ServerCore::Private::handleIncomingConnection(QIODevice*)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::Private::handleIncomingConnection(QIODevice*) New connection. New count: 5
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x7f21f801c740)
kdeinit4: preparing to launch /usr/bin/krandrtray
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
[/usr/bin/nepomukservicestub] '                             ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '            ' is not a UTF8 or latin1 string
'                            ' is not a UTF8 or latin1 string
'         ' is not a UTF8 or latin1 string
'     !"        "        #    #    ' is not a UTF8 or latin1 string
'$        % ' is not a UTF8 or latin1 string
'&"        ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     !"#$' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'%&'#' is not a UTF8 or latin1 string
'&     ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
'*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#     & ' is not a UTF8 or latin1 string
'%&%    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#    &        &' ' is not a UTF8 or latin1 string
'+"&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %    '    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%&#    '&&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    '&,    ' is not a UTF8 or latin1 string
'-*. ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/ ' is not a UTF8 or latin1 string
'0 ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '0& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '  ' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
'0 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '0& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '3  ' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
'0 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '0& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '0 ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'0& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '56 ' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '0 ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '0& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '57889:*    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&     ' is not a UTF8 or latin1 string
'%    #     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '  ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '% &    '&' is not a UTF8 or latin1 string
'    % ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#$&        &&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '             %'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        %;;' is not a UTF8 or latin1 string
'." ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/    ' is not a UTF8 or latin1 string
'!" ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&2     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%            '' is not a UTF8 or latin1 string
'#-%:            ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ."'    %%#        %' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%&     ' is not a UTF8 or latin1 string
'4& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '&'#' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' &:*' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '% &'&' is not a UTF8 or latin1 string
''&&    '*' is not a UTF8 or latin1 string
'6$&&*4 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '6#    &&% ' is not a UTF8 or latin1 string
'!"'% ' is not a UTF8 or latin1 string
'&        &    !"&' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'#    &!"    &' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!"        &        &' is not a UTF8 or latin1 string
'#< ' is not a UTF8 or latin1 string
'!" ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '-    ' is not a UTF8 or latin1 string
'=' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '-    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&+?84788@' is not a UTF8 or latin1 string
'/2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&&    &    &%' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '6 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '0 '' is not a UTF8 or latin1 string
'%%#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' A$.5' is not a UTF8 or latin1 string
'    #     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     '&    %  ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '                &&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    B4."#     ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '."!"' B4."#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
''&     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '         %#4    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' /1#82    ' is not a UTF8 or latin1 string
':5 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&%/ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&             D' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '"' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#-%'&     ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&&     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'&& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&    &'&% /' is not a UTF8 or latin1 string
':' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '2&'/' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'D'    &    '' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
''& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    &/##' is not a UTF8 or latin1 string
'/2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!'2    ':5#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&%:5        % ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    #%    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        :5' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     &''' is not a UTF8 or latin1 string
'&' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&&'    /!2'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#$D    %    ' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '',&    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '  ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$'    %        &&&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
''&&*# /    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '2     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &&A&' is not a UTF8 or latin1 string
'&     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '.A    %'*' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        %&    /            %' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        %"%'/%C%@2#'*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ,E ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        %&&%/?F#888G ' is not a UTF8 or latin1 string
'2' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        '/*    &2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        ,%&,H&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'I'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '-%    +' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    % ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'A    %        &A' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'&A    A ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%&        &' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'A    %%&&    &&    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '-%&    A' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    A& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!"# ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&'&' is not a UTF8 or latin1 string
'&' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '            %&     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ##&##' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'    &'A#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%    '&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$%    # ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '            ;;&#    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    &' is not a UTF8 or latin1 string
'    #-     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%'    %%    ' is not a UTF8 or latin1 string
'&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '-    A:5'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    ' is not a UTF8 or latin1 string
'    % ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%#            ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&+%&    #' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &&&&/' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '2."#' is not a UTF8 or latin1 string
'    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'A'    &    #' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&     ' is not a UTF8 or latin1 string
'    :5'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%    &A&'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&%    A ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#%    ' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&&    #    ' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '                 *    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %    '&"&&' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B&'' is not a UTF8 or latin1 string
'    ,% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        J    *B$4.3 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '.&KA&, ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',&,H    H% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!7'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#&%&&    A ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    &' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&"##     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '.A%AI###' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&'     ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '0L&    34*    %' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&&#        '    ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &    %&' is not a UTF8 or latin1 string
'&        ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%&    '.#    +%' is not a UTF8 or latin1 string
'34*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    #*+, ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        %:5'&%' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
':5&&    :::I#:5' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&%' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        #    &    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#&&    *    *#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    &    ';B";AL' is not a UTF8 or latin1 string
'*###' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&!-+ # ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&'        #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '-        ' is not a UTF8 or latin1 string
'% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        #J    %' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '    '' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B ' is not a UTF8 or latin1 string
'    B'*#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&$     ' is not a UTF8 or latin1 string
'$    %&EAL    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    %&' is not a UTF8 or latin1 string
'"" ' is not a UTF8 or latin1 string
'    &#3'&&    &' is not a UTF8 or latin1 string
'?K#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&'    , ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    B%%%    &0 ' is not a UTF8 or latin1 string
'K ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&    "%'&"&#$$     ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'%%%JH    &%"#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&./&0**&' is not a UTF8 or latin1 string
'!*     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    &&&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#% ' is not a UTF8 or latin1 string
'    KM@    @C#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '.+# # ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$%A&''' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    !"'&#' is not a UTF8 or latin1 string
' A& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&'/            %2' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        #&/     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '2"#$    ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'/##' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '2'        0&    &' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &A    &#!' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '+# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&'/2    *' is not a UTF8 or latin1 string
'*46# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#"#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'A&'%    &' is not a UTF8 or latin1 string
'&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '."#            &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %#A&    #$' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&'    ,' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'        &    &'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    #    &''' is not a UTF8 or latin1 string
''    :5 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    :5'&#' is not a UTF8 or latin1 string
'0    "     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' &    '&    &' is not a UTF8 or latin1 string
'&:5 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&%' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' 1#8&' is not a UTF8 or latin1 string
'    !" ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&%&     "&%' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    +&'%    &&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' /:' is not a UTF8 or latin1 string
'&2        &' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '*+&&%/4&4 ' is not a UTF8 or latin1 string
'"4&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'H.2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '*+:5&& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&'/2'&' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    '    &' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4&&     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$,,%*5"& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%&+    & ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '6,7888        /    NC2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&        #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$     1&&/     F%&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' " ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    &&%' is not a UTF8 or latin1 string
'6 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '1     2,3*4 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' !"'&$O!"%' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''/2                KM@C#C&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'.' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/...    2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4&$&&/'2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' /' 4&2' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '3$*$'&%&,& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&        &&/' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''' ' is not a UTF8 or latin1 string
'78''2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$B!,."&&'4'' is not a UTF8 or latin1 string
'&K' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'N'C#            ."&./..2#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&    ."&%  ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '5% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$&788M A##' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '1#8 ' is not a UTF8 or latin1 string
' 1#81#?    % 1#?A#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '?#9#?7K$&788M ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'$ *550 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '?#C#?#7CP7881 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '?#C#?#?C7881 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '?#C#??@B%7881 ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!!55. ' is not a UTF8 or latin1 string
'?#K#C?1$&7881 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '?#K#K?7 7881 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '?#K#7?FP7881 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'55& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'6    55& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '?#???FP788@ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '?#?7F*788@ ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '51755& ' is not a UTF8 or latin1 string
'8#M#K7K47889 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '8#M#779&7889 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '8#M#?78&7889 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '8#M?K&7889 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '8#1#M?MP7889 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '8#1#979P7889 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &%    &'#        &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     8%9     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        I    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'&#&&'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'I#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     9    : ' is not a UTF8 or latin1 string
'         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '79@*3$* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '@-%&/5    &'2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%9    : ' is not a UTF8 or latin1 string
'C         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '9?7*3$* ' is not a UTF8 or latin1 string
'?7-%&/5    &'2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B' ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'K%/BH$2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &/&%        ' is not a UTF8 or latin1 string
'2' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$*4&$*$    $*$    6$*$    @C$*$    @C67$*$     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' 6$*$*&$*@C$*@C67' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '6C' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '* ' is not a UTF8 or latin1 string
'5"57 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        79@*3$*        9?7*3$*&# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&%    !' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%&        '%#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '8 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '*        '        &        ' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#&                H$BH' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    &' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &&    '    ' is not a UTF8 or latin1 string
' 1#8-.' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        #    %' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&    &+    ,&' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
'6 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &&' is not a UTF8 or latin1 string
' *' is not a UTF8 or latin1 string
'    6#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$%' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    C' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'H ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!      ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    D#        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/I2     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&    '/&2#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        5    /%2Q7#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    H    ?7##I' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    !!'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    4&&                ' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%    '#    &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'&'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!#*+ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B            A    '    ' is not a UTF8 or latin1 string
'"     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        %##    '    ##    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ';;A    '    ' is not a UTF8 or latin1 string
'    #' is not a UTF8 or latin1 string
''    '    E ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4    /2    '/' is not a UTF8 or latin1 string
'*9    ' ' is not a UTF8 or latin1 string
'2& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'**9 ' is not a UTF8 or latin1 string
'    A        ' is not a UTF8 or latin1 string
'*9 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J    *9    '    &    ##     ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
'        '&    **9*99            ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' ' is not a UTF8 or latin1 string
'A&#    *9A    A    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4!"/." 2    9    '    ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'         ' is not a UTF8 or latin1 string
'$    #*%/ 3' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J    %    '        4:#A ' is not a UTF8 or latin1 string
'    4H#    3/' is not a UTF8 or latin1 string
'2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '3/32#        %' is not a UTF8 or latin1 string
'$3H3$*%    + ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$H3$*3% ' is not a UTF8 or latin1 string
'$    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'" ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$!"&4#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    &    %            ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'# ' is not a UTF8 or latin1 string
'&    ' is not a UTF8 or latin1 string
'B ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'6 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '# ' is not a UTF8 or latin1 string
'!"&    :5/    2' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#$%!" ' is not a UTF8 or latin1 string
'        ' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
'34*#$    % ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '            *$#' is not a UTF8 or latin1 string
'$    #*%/  ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'&&    &#' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &&#&    '; R.' is not a UTF8 or latin1 string
'B###;' is not a UTF8 or latin1 string
'J' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    #';;' is not a UTF8 or latin1 string
'34*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$'        34*' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'#     ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        %A+' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
',4    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4&    ;&;    ' is not a UTF8 or latin1 string
'4'     ' is not a UTF8 or latin1 string
'    #' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '7*-    #%/  ' is not a UTF8 or latin1 string
'$    B34* ' is not a UTF8 or latin1 string
'    &&&& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '34*H3$*#$            %    ' is not a UTF8 or latin1 string
'#.A ' is not a UTF8 or latin1 string
'    34*&#.    B';3R' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ';' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'34*#$%'; R4&;' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    "    &&; ' is not a UTF8 or latin1 string
';&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '';4:;#4    "';;B' is not a UTF8 or latin1 string
''' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$B        &&' is not a UTF8 or latin1 string
'+     ' is not a UTF8 or latin1 string
'34*#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ; ' is not a UTF8 or latin1 string
'6 ' is not a UTF8 or latin1 string
'    &&#    '' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&#!6%.        ' is not a UTF8 or latin1 string
'&&#$ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&'        '    ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'    /2        34*A    %/B' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '2#J'    &;A/B*2;' is not a UTF8 or latin1 string
'$6A    &#    &&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''; R ' is not a UTF8 or latin1 string
'4 ###;' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' ' is not a UTF8 or latin1 string
'$    &&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#!;4;' is not a UTF8 or latin1 string
''    ;###;' is not a UTF8 or latin1 string
''' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        #            %;;' is not a UTF8 or latin1 string
'6' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'34*' is not a UTF8 or latin1 string
'             ' is not a UTF8 or latin1 string
'$    #*%/ <= ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '<#><=+*>?; ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$!"&/        :52     ' is not a UTF8 or latin1 string
'." ' is not a UTF8 or latin1 string
':5:K    34*&&' is not a UTF8 or latin1 string
'!"#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ':K            ' is not a UTF8 or latin1 string
'B ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '6 ' is not a UTF8 or latin1 string
'I#' is not a UTF8 or latin1 string
'.    :K';R###;' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    &        ##!;;'    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4'    ;;    &    :K' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'34*#' is not a UTF8 or latin1 string
'<#+<=+*; ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' ' is not a UTF8 or latin1 string
'&    34*,H    '&#' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '';$R;' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'#' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ';4:;' is not a UTF8 or latin1 string
'    34*%    &' is not a UTF8 or latin1 string
'#.%     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&#';;'' is not a UTF8 or latin1 string
'34* ' is not a UTF8 or latin1 string
'%' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''            #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    #/# /; ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '.    A'!AA$&&ARA!A' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''A A    A4&'###A            4' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    4'A4&A#' is not a UTF8 or latin1 string
'      ' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    4&            &#    4' is not a UTF8 or latin1 string
''    AA#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &&&    '    AHA&&' is not a UTF8 or latin1 string
''AA#' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&#*/* ' is not a UTF8 or latin1 string
'    !4     !&%            !"' is not a UTF8 or latin1 string
'AA' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '         ' is not a UTF8 or latin1 string
'P8        %!'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '.#**, ' is not a UTF8 or latin1 string
'D    &#D&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'&&    %#' is not a UTF8 or latin1 string
'##@' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '+        +        ,    ' is not a UTF8 or latin1 string
'    &        ' is not a UTF8 or latin1 string
'#*&& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&."/    2    &' is not a UTF8 or latin1 string
'# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&                %&##    '    &' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'    &/ ' is not a UTF8 or latin1 string
'    '&E ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''            '% ' is not a UTF8 or latin1 string
'&        '%        &' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &/&2 ' is not a UTF8 or latin1 string
'&    %'&%&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'        %%    &#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &    &' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
'&    &&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&' is not a UTF8 or latin1 string
'%"&&&' is not a UTF8 or latin1 string
'&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&A    ' is not a UTF8 or latin1 string
'%    #' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    +        *,+        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    I' is not a UTF8 or latin1 string
'&% ' is not a UTF8 or latin1 string
'        .%&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B        %34*        %A            ' is not a UTF8 or latin1 string
'L ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '34*AA' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'H*A%&A    *' is not a UTF8 or latin1 string
'#$.% ' is not a UTF8 or latin1 string
'%#' is not a UTF8 or latin1 string
'3'< ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'        !"'&' is not a UTF8 or latin1 string
'*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#    D    "' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'        %#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &' is not a UTF8 or latin1 string
'    &'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$0'&&                &' is not a UTF8 or latin1 string
''& ' is not a UTF8 or latin1 string
'I    %&#            ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&        &    ' is not a UTF8 or latin1 string
'%&% ' is not a UTF8 or latin1 string
'&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#* ' is not a UTF8 or latin1 string
'BA    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '5    ,H%4%&&' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$&        ,H%&!&%' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!&#$&    ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&A    &     M ?7'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    %    #J    %4*4' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '            %#    ' is not a UTF8 or latin1 string
'         ' is not a UTF8 or latin1 string
'%%        34*%    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'            #            ' is not a UTF8 or latin1 string
'&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
'    F&    ' is not a UTF8 or latin1 string
'A    B ' is not a UTF8 or latin1 string
'B&    &#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '*7 ' is not a UTF8 or latin1 string
'        $%,&' is not a UTF8 or latin1 string
'        4A&&< ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '% ' is not a UTF8 or latin1 string
'  ' is not a UTF8 or latin1 string
'&    4/     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '*$2    5    %34*%' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &5$/%    %    2KM@' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'$    $#' is not a UTF8 or latin1 string
'#    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &&        '     ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'*,### ' is not a UTF8 or latin1 string
'    &&         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &#' is not a UTF8 or latin1 string
'# ' is not a UTF8 or latin1 string
'"         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&%        %"#' is not a UTF8 or latin1 string
'%    '?7 ' is not a UTF8 or latin1 string
'    %% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'H5$#!    &?&    !' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'?C     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    AS #     ' is not a UTF8 or latin1 string
'%#' is not a UTF8 or latin1 string
'? ' is not a UTF8 or latin1 string
'&    &&%' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        '#' is not a UTF8 or latin1 string
'4&?/;<>;2&    ;5' is not a UTF8 or latin1 string
';;?;' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    D#    # ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    "            &' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    %' is not a UTF8 or latin1 string
'    &        &            ' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    ' is not a UTF8 or latin1 string
'                "&&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    I'&            &"&        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %    '#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &'0#J' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    '        +' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%    #'        '' is not a UTF8 or latin1 string
'    ;     ' is not a UTF8 or latin1 string
':;        '%#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '# ' is not a UTF8 or latin1 string
'+        /    %' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!2    %            #    ' is not a UTF8 or latin1 string
';;"    '#%        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''"' ' is not a UTF8 or latin1 string
'##A' is not a UTF8 or latin1 string
''&     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ';;        0    #-%    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'            %    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&/,,&,,2#' is not a UTF8 or latin1 string
'!D7# ' is not a UTF8 or latin1 string
'    '    ;B";&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
'    &I&    #&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#J&            %#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &&    B%%%' is not a UTF8 or latin1 string
'# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &&        ' is not a UTF8 or latin1 string
'# ' is not a UTF8 or latin1 string
''    TU"#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$* ' is not a UTF8 or latin1 string
'4    K        %' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     !&,3& ' is not a UTF8 or latin1 string
''&5%5 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',H,!B' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ;     ;&    ' is not a UTF8 or latin1 string
'JA    %& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J    %&' is not a UTF8 or latin1 string
'        & ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ;&,3&;&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
''& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&% ' is not a UTF8 or latin1 string
'    '&%%    ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '-    &#$%' is not a UTF8 or latin1 string
'    6* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/%        2&    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'-&;    ;' is not a UTF8 or latin1 string
'+' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',H!%    ;,H,!' is not a UTF8 or latin1 string
''' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %/;' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B';2#         ' is not a UTF8 or latin1 string
';B';&            '' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'    /K#?#@2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ';B";    "&' is not a UTF8 or latin1 string
'&<7     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &$/;;2    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'#    &    %' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$% %    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'/,,%2' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!%A&&' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'D            &%    ' is not a UTF8 or latin1 string
'&     ' is not a UTF8 or latin1 string
'&#!&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    % ' is not a UTF8 or latin1 string
'I&        #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &I    A' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'A&&&    /2&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!&    ' is not a UTF8 or latin1 string
'    A ' is not a UTF8 or latin1 string
'#                ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#B    &#    ' is not a UTF8 or latin1 string
'    %     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '    ;$;        &&    ;!' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'$;    #J'    ' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ';$&&;%        #' is not a UTF8 or latin1 string
'J%    ;    ;#    &&    ' is not a UTF8 or latin1 string
'                 ' is not a UTF8 or latin1 string
'                    #        ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '*4*#' is not a UTF8 or latin1 string
'    "            ****    "' is not a UTF8 or latin1 string
'* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    @    +**+=    # ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '*'/        %2D' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    L ' is not a UTF8 or latin1 string
'';B";            ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'    "&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '., ' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
'    &        &        '%        &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'    #    ;-%;    '    ' is not a UTF8 or latin1 string
'    &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        #    '' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'A    %    &&&' is not a UTF8 or latin1 string
'    '    ;!';&    '&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''%#%    ;!';%' is not a UTF8 or latin1 string
'&L ' is not a UTF8 or latin1 string
'         &            ,%,8' is not a UTF8 or latin1 string
'?         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &        %/%2#' is not a UTF8 or latin1 string
'B% ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'88;%; ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '?;    &;; % ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' '%;8;&' is not a UTF8 or latin1 string
';?;#- ' is not a UTF8 or latin1 string
'"&' is not a UTF8 or latin1 string
',%,8?V %& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',%,??V%& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',%,8KV %/2    & ' is not a UTF8 or latin1 string
',%,??V%/2& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J    &        #    %' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &        ;;' is not a UTF8 or latin1 string
'"#    ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '*        %    &' is not a UTF8 or latin1 string
'    ' ' is not a UTF8 or latin1 string
'    ;    ;&#    "&&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &#    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&    %!"&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'$.    '    &'&"#    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     %' is not a UTF8 or latin1 string
'         ' is not a UTF8 or latin1 string
'"#*    &     ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
''&'    &    '"/' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%2#' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
''        '"&    &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'4    &    '&#' is not a UTF8 or latin1 string
'/ 2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %%&' is not a UTF8 or latin1 string
'3&';; /###2' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&%';; ' is not a UTF8 or latin1 string
'/' is not a UTF8 or latin1 string
',,%,    ####2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J'&&;,;&    %&' is not a UTF8 or latin1 string
''' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%"&#$    %;,;' is not a UTF8 or latin1 string
'&     ' is not a UTF8 or latin1 string
'    /CG2$&%#&' is not a UTF8 or latin1 string
'$& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%3$*#    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %?3$*?$&#*' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'"&    '    ; ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$'& ' is not a UTF8 or latin1 string
';     -'#' is not a UTF8 or latin1 string
'     '    ;!5&&&;&        ' is not a UTF8 or latin1 string
'% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&%&&#&&5' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
'        %*#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '';B";    "&' is not a UTF8 or latin1 string
'0 ' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4    &&'' is not a UTF8 or latin1 string
'/     ' is not a UTF8 or latin1 string
'    2#    ;$%&;"    &'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&     ' is not a UTF8 or latin1 string
' &     #' is not a UTF8 or latin1 string
'&'    &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%        #' is not a UTF8 or latin1 string
'    &'%&' is not a UTF8 or latin1 string
'= ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/*0A&&2' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'> ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/,H2' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'?     ' is not a UTF8 or latin1 string
'/:55&'2' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'/$2' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'/     ' is not a UTF8 or latin1 string
'/    :42' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'%&:/2' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '+E' is not a UTF8 or latin1 string
'/*&'&2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '//# ' is not a UTF8 or latin1 string
'/ 2' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/    2' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'E ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/ &2' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'/ 2' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'    &'Q7/*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&O ' is not a UTF8 or latin1 string
'5'2#' is not a UTF8 or latin1 string
'1%' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
'$    &&    34*    '%#' is not a UTF8 or latin1 string
'';B";    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    #    &I#4    '' is not a UTF8 or latin1 string
'%    ' ' is not a UTF8 or latin1 string
'?9#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'A    34*& ' is not a UTF8 or latin1 string
'&&Q7' is not a UTF8 or latin1 string
'5     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '                &&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&#J+    ';     ;    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&#' is not a UTF8 or latin1 string
'        %    ; ;    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#4    &        %' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'    =' '    = ' is not a UTF8 or latin1 string
'"H*H" ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&%#H" ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '."*    4&&&&' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'    %%&        A' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        A&&#H"&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    H"#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#    ,     ' is not a UTF8 or latin1 string
'    &&H"#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'H"#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'H"'    ;B;&    ' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
';B"; ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B&/        &' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'2    4&         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '"3$*%#B        3$*' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    A3$*'&##?3$*' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'KMC*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    "&&%    %#';";    ;;' is not a UTF8 or latin1 string
'&         ' is not a UTF8 or latin1 string
'%#        BH'0    &';B";#        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ';5"&%;; "0%;#    "&    ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'&##    &%    &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''& ' is not a UTF8 or latin1 string
'    &        A#    &' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    5"&' is not a UTF8 or latin1 string
'%#B    ' is not a UTF8 or latin1 string
'A    %##5%H"@' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '        A%    %#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%    %%            0        0#    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '0@&    H%#';B";' is not a UTF8 or latin1 string
'        0#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B    '    ;H-';-%    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
';-'/*2;#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '';B";    ;     ;&&    %' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&#' is not a UTF8 or latin1 string
'# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &%&%A&' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'    ,H%        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4    H"    '    ;' is not a UTF8 or latin1 string
';#J ' is not a UTF8 or latin1 string
''        3$*#*'    %    :5A' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&/M*    K7*&2 ' is not a UTF8 or latin1 string
'4        ;,H34*;'    ;,H%;#    ' is not a UTF8 or latin1 string
'    % ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    ,H&    ' is not a UTF8 or latin1 string
',H     ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$%    %,H&    #P' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
'    ;4 ;    /' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ,H ' is not a UTF8 or latin1 string
'    2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''4:A&&    /&    2    ' is not a UTF8 or latin1 string
'#     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '+    K#?,H!#' is not a UTF8 or latin1 string
'            '    ;,H%;    ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' + ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'! ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    &    %#$&' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ':5,6    A        +%#' is not a UTF8 or latin1 string
'!#    * ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &                &#*    ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    &    /%2#-%' is not a UTF8 or latin1 string
';' is not a UTF8 or latin1 string
'&&;&@;3H5$;#    ' is not a UTF8 or latin1 string
'    & ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        '    %&        ' is not a UTF8 or latin1 string
'&& ' is not a UTF8 or latin1 string
':5#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!# ' is not a UTF8 or latin1 string
'$        &' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&        %%# A%/&2     ' is not a UTF8 or latin1 string
'    '    A    A#    %' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '% ' is not a UTF8 or latin1 string
'    ;%%;&#    %        %'' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    %#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
'4&            0        %    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'+    ;$%;#        0%I'    ;* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ';'"    /            A' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    A2#' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        %    ';$&&;    ' is not a UTF8 or latin1 string
'% ' is not a UTF8 or latin1 string
'#    ''    ;&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '; ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    #A    &&        ';J;    "&#' is not a UTF8 or latin1 string
'';B; ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ;&;#' is not a UTF8 or latin1 string
'!D# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    %&        %        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&K#?#@#4&+    ' is not a UTF8 or latin1 string
'        #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    ;$!;K#?#@    A    ' is not a UTF8 or latin1 string
'        :5'&%    &&#5             ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '"    :5&    ' is not a UTF8 or latin1 string
'&#    '&#' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&            #*' is not a UTF8 or latin1 string
'    % ' is not a UTF8 or latin1 string
'    A#    %        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&' ' is not a UTF8 or latin1 string
'            %    #' is not a UTF8 or latin1 string
'!# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '.'&&&'' is not a UTF8 or latin1 string
'0#     ' is not a UTF8 or latin1 string
'*' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '*46' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'"&    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'"#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    "' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&& ' is not a UTF8 or latin1 string
''    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'';B";     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &#    &&'' is not a UTF8 or latin1 string
'4&4# ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'/& ' is not a UTF8 or latin1 string
'*K%2    ' is not a UTF8 or latin1 string
'4& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
' " ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %    &1#' is not a UTF8 or latin1 string
'!# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#    ' is not a UTF8 or latin1 string
'!' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'$        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'    ;;' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
''    #.:5 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#J         ' is not a UTF8 or latin1 string
'!&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
''&    & ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'#        %     ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    */2';R$' is not a UTF8 or latin1 string
'R ;#' is not a UTF8 or latin1 string
'         &' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '';$ ;    #    ';4';#J ' is not a UTF8 or latin1 string
':5'    '#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ' is not a UTF8 or latin1 string
'* ' is not a UTF8 or latin1 string
'        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'#$    A''*A#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!!6, ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '              * ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'P%35%/P352P%%&:/P:2        ' is not a UTF8 or latin1 string
'% ' is not a UTF8 or latin1 string
'#    P%&'         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'P% ' is not a UTF8 or latin1 string
'A#' is not a UTF8 or latin1 string
'!$ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     &    #    &' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    %    "A    #$&&*' is not a UTF8 or latin1 string
'    %& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        #$    ' is not a UTF8 or latin1 string
'        & ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        ##    !#A' is not a UTF8 or latin1 string
'    %A' is not a UTF8 or latin1 string
'    A&/"#    *5&2        ' is not a UTF8 or latin1 string
'#     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'    &&%/    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&2     ' is not a UTF8 or latin1 string
':*:' is not a UTF8 or latin1 string
'H. ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '6#    &&             ' is not a UTF8 or latin1 string
'FFW' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'  ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'%63* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#P'    ' is not a UTF8 or latin1 string
'  ' is not a UTF8 or latin1 string
':*/ ' is not a UTF8 or latin1 string
':2    &#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '-%"&%&&&/' is not a UTF8 or latin1 string
'2     ' is not a UTF8 or latin1 string
':*            %    :6#P' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '' is not a UTF8 or latin1 string
''&        #' is not a UTF8 or latin1 string
'!&E    *# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'EJA"'E-%&' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'&        :5E4    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'            A"&E    &' is not a UTF8 or latin1 string
'&        %' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &        ##' is not a UTF8 or latin1 string
'- ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'A%    %    &' is not a UTF8 or latin1 string
'&?7#J ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &%&&' is not a UTF8 or latin1 string
'! ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#:&        #    %    &' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
'            %    &#' is not a UTF8 or latin1 string
'7 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    A%&$/ ' is not a UTF8 or latin1 string
'$% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '"&    %'O    /&72#' is not a UTF8 or latin1 string
'-* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'A%    &            "' is not a UTF8 or latin1 string
'1 ' is not a UTF8 or latin1 string
';3H5$;#' is not a UTF8 or latin1 string
' $ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$%/7#C    '2    A        %"&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&A34*&' is not a UTF8 or latin1 string
'#5%     ' is not a UTF8 or latin1 string
''#    '    *9    '    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'*9    &#' is not a UTF8 or latin1 string
'8 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'D"&&        ' is not a UTF8 or latin1 string
' 1#8-.' is not a UTF8 or latin1 string
'D7 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$&    .$/.'$2' is not a UTF8 or latin1 string
'    4# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    '4.$/A' is not a UTF8 or latin1 string
'% ' is not a UTF8 or latin1 string
'2 ' is not a UTF8 or latin1 string
'  ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    *&    ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %%#        &' is not a UTF8 or latin1 string
'&0 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/&1    '    2#' is not a UTF8 or latin1 string
'    %    "&        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '         ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    '    &?C-&O&&#' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$D,  ' is not a UTF8 or latin1 string
'$'  ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'$D,3' ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&+ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '&+'    %' is not a UTF8 or latin1 string
'#         ' is not a UTF8 or latin1 string
'    '&'/    ' is not a UTF8 or latin1 string
'    & ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'&# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'&'2'    #    '&&        K    ' is not a UTF8 or latin1 string
'    &     ' is not a UTF8 or latin1 string
'&    %    '&#        &' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&&        ''&##' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'&'&&&    &' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
''        &        #' is not a UTF8 or latin1 string
'&E+ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4    '    &&&' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
'&&&'&' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '*'    ' is not a UTF8 or latin1 string
''4    & ' is not a UTF8 or latin1 string
'      ' is not a UTF8 or latin1 string
'-'#' is not a UTF8 or latin1 string
'&** ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$&             &#J' is not a UTF8 or latin1 string
'%     ' is not a UTF8 or latin1 string
'&:&    ' is not a UTF8 or latin1 string
'! ' is not a UTF8 or latin1 string
'!    &'%&&    AIA'    & ' is not a UTF8 or latin1 string
'    #J%    &        :I' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,,,    ,,1,    #1#0 ' is not a UTF8 or latin1 string
'-&&    /    ' is not a UTF8 or latin1 string
' -' ' is not a UTF8 or latin1 string
'  ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
', 3/&2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ', && ' is not a UTF8 or latin1 string
',     ' ' is not a UTF8 or latin1 string
', & ' is not a UTF8 or latin1 string
', &    % ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',&,", ."& ' is not a UTF8 or latin1 string
',% %A&A ' is not a UTF8 or latin1 string
',  ' is not a UTF8 or latin1 string
',,6?? J"# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,# &%& ' is not a UTF8 or latin1 string
',     % ' is not a UTF8 or latin1 string
',    , AA' is not a UTF8 or latin1 string
', &,, ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '," * ' is not a UTF8 or latin1 string
', *AH ' is not a UTF8 or latin1 string
', &A*A' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ', $/2& ' is not a UTF8 or latin1 string
', &#' is not a UTF8 or latin1 string
',& & ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ', !#' is not a UTF8 or latin1 string
',%      %0' is not a UTF8 or latin1 string
',%, .    & ' is not a UTF8 or latin1 string
',%,& +& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',%,  ' is not a UTF8 or latin1 string
',, & ' is not a UTF8 or latin1 string
',,  ' is not a UTF8 or latin1 string
',,     $',     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',, AA,GG& ' is not a UTF8 or latin1 string
',, .&,,,, ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,  &     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,, &    & ' is not a UTF8 or latin1 string
',,, &% ' is not a UTF8 or latin1 string
',,,# &%,,,Z ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,, .AA,GG%& ' is not a UTF8 or latin1 string
',,, .&,,,Z ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,, *&&,,,Z ' is not a UTF8 or latin1 string
',,, && ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,,     & ' is not a UTF8 or latin1 string
',,,    ,&&' :*     ' is not a UTF8 or latin1 string
',,,    , &,,,Z ' is not a UTF8 or latin1 string
',,,     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',"& ' is not a UTF8 or latin1 string
'5"&&,,,Z ' is not a UTF8 or latin1 string
',,,    , &    && ' is not a UTF8 or latin1 string
',,,    , :5/:'&5%2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,,    , :5 ' is not a UTF8 or latin1 string
',,,    ,     :5         ' is not a UTF8 or latin1 string
',,,     ' is not a UTF8 or latin1 string
',&& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&     ' is not a UTF8 or latin1 string
',,,     ' is not a UTF8 or latin1 string
',&& ' is not a UTF8 or latin1 string
'&A&&A' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,&     & ' is not a UTF8 or latin1 string
',,     & ' is not a UTF8 or latin1 string
',,    , 5"  ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,    ,"& 5"&  ' is not a UTF8 or latin1 string
',, *& ' is not a UTF8 or latin1 string
',,   ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&8 ' is not a UTF8 or latin1 string
'5%%A    A    &' is not a UTF8 or latin1 string
'         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#                ,    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'# "&/2    &+        &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'    ,    ,+        #I        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        %!"'&' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'4%#&' is not a UTF8 or latin1 string
'    *' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#J                #4     ' is not a UTF8 or latin1 string
'    #        ' is not a UTF8 or latin1 string
'"& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%    #J            % ' is not a UTF8 or latin1 string
'&     #3<    #, ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$"&        34*#&' is not a UTF8 or latin1 string
''34* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%&&' is not a UTF8 or latin1 string
'&&'    ' is not a UTF8 or latin1 string
'    '#-&&&'' is not a UTF8 or latin1 string
'%    I ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&$&#' is not a UTF8 or latin1 string
'    '    '    34*'' is not a UTF8 or latin1 string
'&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&''    &'         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#    '&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&    ,#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J&    :        %' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&    &#4&'    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'34*    ,' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',%,8,' is not a UTF8 or latin1 string
'    ,%,8&    &'%    ' is not a UTF8 or latin1 string
'&34* ' is not a UTF8 or latin1 string
'H34*%#5    %0' is not a UTF8 or latin1 string
'34* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%/    %2&,%,8    %    ,%,?#' is not a UTF8 or latin1 string
'4    '        &    ' is not a UTF8 or latin1 string
'%"& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '34*%            ,,#J    %&' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'%    %/2#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '+    '&    '' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        '+#        &&'' is not a UTF8 or latin1 string
'    !'"' is not a UTF8 or latin1 string
'    %    &#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '3    '    '&&34*%    ;;    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'+    '#J        &&'         ' is not a UTF8 or latin1 string
'/    AAAA2' is not a UTF8 or latin1 string
',' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J'    #J    %' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&    &        #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4*4&    '%%' is not a UTF8 or latin1 string
'"&$Y' is not a UTF8 or latin1 string
'&    &&%#4' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        /    &2#I' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
'',    ,, &&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$     -'' is not a UTF8 or latin1 string
'*!  ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '.#7 ' is not a UTF8 or latin1 string
'    %    #5    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'    /2 ' is not a UTF8 or latin1 string
''    I'  ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '      ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &    &&' is not a UTF8 or latin1 string
'             ' is not a UTF8 or latin1 string
''            &#    &&&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '+'#& ' is not a UTF8 or latin1 string
'&&'' is not a UTF8 or latin1 string
'    &    &#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J    &&&#    I' is not a UTF8 or latin1 string
''     ' is not a UTF8 or latin1 string
'&'%&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
'#, ' is not a UTF8 or latin1 string
'    &            &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    I ' is not a UTF8 or latin1 string
','    #    %&    ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '            #' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&' is not a UTF8 or latin1 string
'4    &&'            #' is not a UTF8 or latin1 string
'&&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &&    &' is not a UTF8 or latin1 string
'#    % ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&%    ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'';B";        '' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &#    '    ;;"';B";' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'J    %    &&'&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'    &&#    '"    &&';;' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4        &';     ;&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J"        ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'        &#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '"#$%    &'''# ' is not a UTF8 or latin1 string
'    '&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '    '&;'&&' is not a UTF8 or latin1 string
';#    & ' is not a UTF8 or latin1 string
'            &/'    2#    ' is not a UTF8 or latin1 string
''     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ';$&&;#-    %    &    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&    '&    &I#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%,# ' is not a UTF8 or latin1 string
'%#&&&+;*RR$' is not a UTF8 or latin1 string
'R3% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/2;#J    &&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    &&%&    ;3%;    ' is not a UTF8 or latin1 string
'#     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '';4:;#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#+# ' is not a UTF8 or latin1 string
''&&    ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'&#    &'&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
'%." ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#    &'        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' & ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
' '&    ;'&;' is not a UTF8 or latin1 string
'7     ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%&    #&%    ' is not a UTF8 or latin1 string
'    &'     ' is not a UTF8 or latin1 string
'    '' is not a UTF8 or latin1 string
'*+!!!, ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'#    ' is not a UTF8 or latin1 string
', ' is not a UTF8 or latin1 string
'&            &'' is not a UTF8 or latin1 string
', ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'#JA    %        &'' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    #P        &'#&'' is not a UTF8 or latin1 string
'I& ' is not a UTF8 or latin1 string
'    &#J&' is not a UTF8 or latin1 string
',, ' is not a UTF8 or latin1 string
'    :*& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    :*&&'&' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
'&;5;#J ' is not a UTF8 or latin1 string
'&&    /&2&&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '& ' is not a UTF8 or latin1 string
'#$        &    %&' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'#J&    &'' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
'",    '!! ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        ;;&    I&' is not a UTF8 or latin1 string
'    :*'&#J ' is not a UTF8 or latin1 string
'    /"2,,,' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,,    , ' is not a UTF8 or latin1 string
'        /'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'2&         ' is not a UTF8 or latin1 string
'&&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J&'    &'[    %    ' is not a UTF8 or latin1 string
'&' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '",    !'-    . "/,    0!' is not a UTF8 or latin1 string
''10! ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J&'        &'[#' is not a UTF8 or latin1 string
'",    0!'10 "2!,    3!! ' is not a UTF8 or latin1 string
'#    # ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &#J' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    &' is not a UTF8 or latin1 string
'#B ' is not a UTF8 or latin1 string
'B!,."        ;5;        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' &#' is not a UTF8 or latin1 string
'    &'    :*%;R$' is not a UTF8 or latin1 string
'R ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ';#5    &&    &' is not a UTF8 or latin1 string
''    ;'; ' is not a UTF8 or latin1 string
'#B';     &;    ' is not a UTF8 or latin1 string
'    #     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    &&#' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
'            &    &' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&'    ' is not a UTF8 or latin1 string
'"+''4!!' ' is not a UTF8 or latin1 string
'J    ' is not a UTF8 or latin1 string
'! ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '"!+!+ ' is not a UTF8 or latin1 string
'&' is not a UTF8 or latin1 string
'! ' is not a UTF8 or latin1 string
'    &    &    ' is not a UTF8 or latin1 string
'+ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '"!+55! ' is not a UTF8 or latin1 string
'&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '+ ' is not a UTF8 or latin1 string
'&        ' is not a UTF8 or latin1 string
'"+''4!!' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'J    &&     ' is not a UTF8 or latin1 string
'    ' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'H! ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B        &'' is not a UTF8 or latin1 string
'!! ' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#        R&#' is not a UTF8 or latin1 string
'    &&&+    &&' is not a UTF8 or latin1 string
',,& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',,'&&' is not a UTF8 or latin1 string
'"+!!, ' is not a UTF8 or latin1 string
'",+ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    &    0    &'    &&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'%,#+# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%&'&        &'# ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'%'&&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '",    3!, ' is not a UTF8 or latin1 string
',!,','    678'!+' is not a UTF8 or latin1 string
'!9%:; ' is not a UTF8 or latin1 string
'        &'&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '! ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'",    ,!,','     ' is not a UTF8 or latin1 string
'    &    &&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ' is not a UTF8 or latin1 string
'"+!!', ' is not a UTF8 or latin1 string
'", ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&'    "' is not a UTF8 or latin1 string
'     ' ' is not a UTF8 or latin1 string
'-+#F     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '&' ' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
'    '' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '5    AA'    B ' is not a UTF8 or latin1 string
'%            -&/2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4    %'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '            ?F7#?@M#8#??F7#?@M#8#7###         ' is not a UTF8 or latin1 string
''    B% ' is not a UTF8 or latin1 string
'''    *    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/2 ' is not a UTF8 or latin1 string
'';ROB'RB';#    ' is not a UTF8 or latin1 string
'&&#30     ' is not a UTF8 or latin1 string
'        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
'$&#    ' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ;$*###;&&    &' is not a UTF8 or latin1 string
'&#    ' is not a UTF8 or latin1 string
'&'#'    '' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    #$&&&&&+%' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ;$-;/32;*;#' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
';*;&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        '#    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&' is not a UTF8 or latin1 string
'&%' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B'/799#799#799#82    "%/' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$%        &    &        ' ' is not a UTF8 or latin1 string
''    & ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '                &% ' is not a UTF8 or latin1 string
'';;& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '';4:;&    &    '    %%' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'#    %'    ;3;            %    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''                    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$B    #%    B    A+' is not a UTF8 or latin1 string
'# ' is not a UTF8 or latin1 string
'A'B                    &&'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%&        ;&%%;#' is not a UTF8 or latin1 string
'    ';4:;'&#J    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &'    %    #    %.    ' is not a UTF8 or latin1 string
'&&&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        #' is not a UTF8 or latin1 string
'E ' is not a UTF8 or latin1 string
':5    '' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'"    %&&' is not a UTF8 or latin1 string
''' is not a UTF8 or latin1 string
'    '&        %'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#     ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'            E,:5    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&'& ' is not a UTF8 or latin1 string
'&    +&    #' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!I    ;;    &'    ;' is not a UTF8 or latin1 string
'*R ' is not a UTF8 or latin1 string
'&RR*;#$    &    %&' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    *&#4    ' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
'&            ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ':' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
'* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'E*E ' is not a UTF8 or latin1 string
'    ;;        %         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#A ' is not a UTF8 or latin1 string
'&            'I    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ' is not a UTF8 or latin1 string
'  ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    &    &'    ' is not a UTF8 or latin1 string
';;#' is not a UTF8 or latin1 string
'        &A        &' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &' is not a UTF8 or latin1 string
'    '&/ ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        ' is not a UTF8 or latin1 string
'! ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '+!++ ' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
'!+ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &    %/ ' is not a UTF8 or latin1 string
'' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '/&2 ' is not a UTF8 or latin1 string
'J%&&%    &' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    #' is not a UTF8 or latin1 string
'4%&&' is not a UTF8 or latin1 string
',! ' is not a UTF8 or latin1 string
'/:52&#         ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&A&&%%%&' is not a UTF8 or latin1 string
'    %&' is not a UTF8 or latin1 string
'        I    #$&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'&    #' is not a UTF8 or latin1 string
'E*>E ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '-    ;:;&    %&#    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &&' ' is not a UTF8 or latin1 string
',    &     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ',$$*$* ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'H53J$35 !.&    #    '' is not a UTF8 or latin1 string
'    $$*$ ' is not a UTF8 or latin1 string
'%#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %&    !'    $*"7-&    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &        47                 ' is not a UTF8 or latin1 string
'*'&'&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &&', ' is not a UTF8 or latin1 string
'    & ' is not a UTF8 or latin1 string
'    '    ;5&    ;&    ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#&&'        &&            ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&#' is not a UTF8 or latin1 string
'    ;$$*$;&&&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
''#    &    34*    ' is not a UTF8 or latin1 string
'%    ' is not a UTF8 or latin1 string
'    %    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &    ;;    48@8#' is not a UTF8 or latin1 string
'?' is not a UTF8 or latin1 string
'&&&            &' is not a UTF8 or latin1 string
'&    & ' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$        %'    ;%    ;#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$    &%    %'    ;%    ;' is not a UTF8 or latin1 string
'#' is not a UTF8 or latin1 string
'E*E+E ' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
'        ;;        ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&%    #' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'        +&' is not a UTF8 or latin1 string
'%&#' is not a UTF8 or latin1 string
'.'            &        %' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
''&&%#    ' is not a UTF8 or latin1 string
'      ' is not a UTF8 or latin1 string
'      ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '             &' is not a UTF8 or latin1 string
'        ' is not a UTF8 or latin1 string
'&#    '    %' is not a UTF8 or latin1 string
'&# ' is not a UTF8 or latin1 string
'        #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '         &&    &' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'"&&    &    ' is not a UTF8 or latin1 string
'!! ' is not a UTF8 or latin1 string
'#    ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &    &    &' is not a UTF8 or latin1 string
'&#' is not a UTF8 or latin1 string
'4&&&' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
', ' is not a UTF8 or latin1 string
'2' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' is not a UTF8 or latin1 string
'! ' is not a UTF8 or latin1 string
'        &&' is not a UTF8 or latin1 string
',+ ' is not a UTF8 or latin1 string
'&    &&    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'E* E ' is not a UTF8 or latin1 string
'-&    &#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ', # ' is not a UTF8 or latin1 string
'    %*!:5 ' is not a UTF8 or latin1 string
'%#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%,&        ' is not a UTF8 or latin1 string
'&&,#' is not a UTF8 or latin1 string
''#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %        !' is not a UTF8 or latin1 string
'< ' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
'<-;# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '2!I/!&2 ' is not a UTF8 or latin1 string
'&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '* ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &             ' is not a UTF8 or latin1 string
'&    #    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&'    I    '&#' is not a UTF8 or latin1 string
'<' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        !&' is not a UTF8 or latin1 string
'&     &#    &' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     +    +#' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '87D ' is not a UTF8 or latin1 string
'2-$.& ' is not a UTF8 or latin1 string
'    &    &            ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&#' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
'/     ' is not a UTF8 or latin1 string
'24&$%&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'C ' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
'    &%%&% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!B6&#    &% ' is not a UTF8 or latin1 string
'4,        A"&#        %    ' is not a UTF8 or latin1 string
'B% ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    %    4&'#        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'4#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
'+ ' is not a UTF8 or latin1 string
'2' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '4& ' is not a UTF8 or latin1 string
'A,' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'B'$/B$2#A'&     ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'    %        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#' is not a UTF8 or latin1 string
'AD->E/%?7DD87E?%E/?-D<?D7E?%B ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '               & ' is not a UTF8 or latin1 string
'8 ' is not a UTF8 or latin1 string
'/ ' is not a UTF8 or latin1 string
'    *' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '2-'&    "    % ' is not a UTF8 or latin1 string
'    &&#        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    '&'/2&' is not a UTF8 or latin1 string
'# ' is not a UTF8 or latin1 string
' / 2&/ ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '2&                - ' is not a UTF8 or latin1 string
'&#' is not a UTF8 or latin1 string
'    9 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&I'&/2+!&%     ' is not a UTF8 or latin1 string
'#    %&        '&' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    !#    &&&#' is not a UTF8 or latin1 string
'                           ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '>#     ' is not a UTF8 or latin1 string
'/< # ' is not a UTF8 or latin1 string
'    !&*    &'&&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ' is not a UTF8 or latin1 string
'&    &#' is not a UTF8 or latin1 string
'    &    '&%/' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'I2#    !&    /            "    ' is not a UTF8 or latin1 string
''2     ' is not a UTF8 or latin1 string
'        &#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %    !&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''    T$U    ' is not a UTF8 or latin1 string
'#4             ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    T    '!&U            '    &' is not a UTF8 or latin1 string
'% ' is not a UTF8 or latin1 string
'    '&%#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&;&%;&&& ' is not a UTF8 or latin1 string
'&    &        T%&U&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '            &            ' ' is not a UTF8 or latin1 string
'"    &' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'D/2    #4    A    %%    % ' is not a UTF8 or latin1 string
'%2 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&        T' is not a UTF8 or latin1 string
'&U'' is not a UTF8 or latin1 string
'%    &    '    !&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '     ' is not a UTF8 or latin1 string
'            &    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '            &/2&    ' is not a UTF8 or latin1 string
'         ' is not a UTF8 or latin1 string
'    ;!&;;!&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'LJ ' is not a UTF8 or latin1 string
'    ;#    '    4:A    ' is not a UTF8 or latin1 string
'#      ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %A    &%#' is not a UTF8 or latin1 string
'< ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    !&    !&' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''&    &    !&' is not a UTF8 or latin1 string
'    '    ' ' is not a UTF8 or latin1 string
'    ;    '!&;    ' is not a UTF8 or latin1 string
'&# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '             ' is not a UTF8 or latin1 string
'#     % "7#8#8#??%7#8#8#?7 ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &#    !&%7#8#8#?' is not a UTF8 or latin1 string
'7#    % ' is not a UTF8 or latin1 string
'    %    #' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '    %%'     ' is not a UTF8 or latin1 string
';    '&;#    % ' is not a UTF8 or latin1 string
'&#        ;%&;' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&&&    %& ' is not a UTF8 or latin1 string
'%#' is not a UTF8 or latin1 string
'#     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &        %' is not a UTF8 or latin1 string
'    ' ' is not a UTF8 or latin1 string
'&&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&        '&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'#    !&    '&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '% ' is not a UTF8 or latin1 string
'    %&#&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &    &;3    !&&' is not a UTF8 or latin1 string
';#    ' ' is not a UTF8 or latin1 string
'&%A&%#' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &#4    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#' is not a UTF8 or latin1 string
'*        5        %' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %5    #$&    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&    %#    "' is not a UTF8 or latin1 string
'&' is not a UTF8 or latin1 string
'        '%L ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '- ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '3 ' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!' ' is not a UTF8 or latin1 string
'!E*+# ' is not a UTF8 or latin1 string
'$    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ': ' is not a UTF8 or latin1 string
'#J ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '        &&&&    L    ' ' is not a UTF8 or latin1 string
'    '''    ' is not a UTF8 or latin1 string
'    L ' is not a UTF8 or latin1 string
'!%*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    3    &&+'    &' is not a UTF8 or latin1 string
'&+L ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '<!!*!+! ' is not a UTF8 or latin1 string
'=*"+ ' is not a UTF8 or latin1 string
'3&#'    #        3' is not a UTF8 or latin1 string
': ' is not a UTF8 or latin1 string
'6    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!! # ' is not a UTF8 or latin1 string
'4                    ' is not a UTF8 or latin1 string
'# ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&        ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$/.2 ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'&&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'%& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'%& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '$&        A' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#$%' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '!$8+ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '         -''        A' is not a UTF8 or latin1 string
'L    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    %I''        I    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&E     A&%' is not a UTF8 or latin1 string
'          ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    '&&#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' -    .0-& ' is not a UTF8 or latin1 string
'B ' is not a UTF8 or latin1 string
'                           ' is not a UTF8 or latin1 string
'&    # ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&+    A"    %%' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'&&#' is not a UTF8 or latin1 string
'&,, ' is not a UTF8 or latin1 string
''        &&' is not a UTF8 or latin1 string
''    &&' is not a UTF8 or latin1 string
'&,&' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'3$ ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ''A&A     ' is not a UTF8 or latin1 string
'&' is not a UTF8 or latin1 string
'% ' is not a UTF8 or latin1 string
'%&&    &    ,,' ' is not a UTF8 or latin1 string
'    ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'A%E'&' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '& A%+    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'%    &        ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'I ' is not a UTF8 or latin1 string
'%    &    ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'3/?K#72#' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    &    &+    'A    &&' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&E$%,H' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'  ' is not a UTF8 or latin1 string
'*' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] 'A&#&&&&' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'6 ' is not a UTF8 or latin1 string
'&/ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#    %&&' is not a UTF8 or latin1 string
'     ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%    &    ' is not a UTF8 or latin1 string
'#* ' is not a UTF8 or latin1 string
'        &/2%#' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] ' ' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'' is not a UTF8 or latin1 string
'    &    &    ' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '#' is not a UTF8 or latin1 string
'&' is not a UTF8 or latin1 string
'& ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '    ### ' is not a UTF8 or latin1 string
'    E ' is not a UTF8 or latin1 string
'&!/ ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '%E        EJ' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
'EJA        '%&' is not a UTF8 or latin1 string
' ' is not a UTF8 or latin1 string
[/usr/bin/nepomukservicestub] '&#J&&    #' is not a UTF8 or latin1 string
[31mvoid DBusMenuImporter::slotMenuAboutToShow()[0m: Application did not answer to AboutToShow() before timeout 
[34mvoid DBusMenuImporter::slotAboutToShowDBusCallFinished(QDBusPendingCallWatcher*)[0m: Menu 0 must be refreshed 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 37 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 38 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 39 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 40 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 42 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 43 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 44 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 45 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 46 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 47 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 49 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 28 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 29 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 30 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 31 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 32 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 33 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 34 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 35 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 36 
[34mvoid DBusMenuImporter::slotAboutToShowDBusCallFinished(QDBusPendingCallWatcher*)[0m: Menu 0 must be refreshed 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 85 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 86 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 87 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 88 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 89 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 90 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 91 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 92 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 93 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 94 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 95 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 96 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 97 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 99 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 100 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 101 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 102 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 103 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 104 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 106 
[34mvoid DBusMenuImporter::sendClickedEvent(int)[0m: 100 
RandRDisplay::handleEvent - RRScreenChangeNotify win:  308  root:  308 
RandRScreen::handleEvent 
Reloaded modes 
RandRDisplay::handleEvent - RRScreenChangeNotify win:  308  root:  308 
RandRScreen::handleEvent 
X Error: BadMatch (invalid parameter attributes) 8
  Extension:    150 (RANDR)
  Minor opcode: 7 (RRSetScreenSize)
  Resource id:  0x134
Reloaded modes 
RandRDisplay::handleEvent - RRNotify win:  308 
RandRScreen::handleRandREvent - CrtcChange 
[CRTC 95 ] Event... 
       mode:  99 (current  99 ) 
       pos: ( 0 , 0 ) 
       size:  1920 x 1080 
       rotation:  2 
   Changed rotation:  2 
   Changed size:  QSize(1080, 1920) 
XRandROutput::outputChanged true true QRect(0,0 1080x1920) 
OutputScreens::outputResized 
OutputScreens::triggerRebuildScreens() 
OutputScreens::rebuildScreens() 
rebuild: emitted screenResized  0  - old  QRect(0,0 1920x1080)  - new  QRect(0,0 1080x1920) 

My boot scenario's getting pretty complicated, so I'm going to try to simply it by just using a separate /home/ partition rather than that and an additional /home/*user/MyFiles partition as I have been doing, along with a separate /boot partition, and also by deleting presently unused partitions. Then I'll do a fresh Kubuntu RC install when it comes out and immediately disable nepomuk (since there seem to be a lot of old errors there in the *.old file related to that process, and reduce what's installed to simply KDE-minimal and some extra packages, and see if that makes a difference. 

Does anyone know if it's possible and SAFE to use Ubuntu Customization Kit to reduce the number of packages installed by the Kubuntu Live CD?

---

### Post by autumnraine on 2010-04-25
Well after simplifying my partitioning scheme at doing a fresh install of the Kubuntu RC, it's more stable and no longer crashing, but the BUGS! The things I've noticed so far: 

1) The keyboard shortcuts for several items - such as the desktop pager and quick access menu, both on the panel by default - simply don't work, even with the supposed workarounds listed elsewhere in these forums. 

2) When I rotate the screen (using Krandr with the default Nouveau) the screen is not properly refit to the changed orientation - the mouse will continue going beyond the limits of the visible area, and menus at the far right of the screen will be unreadable because they pop up mostly off screen. 

3) As many people have mentioned, the panel icons, menus, pictures etc. for non-native KDE applications like OpenOffice and Skype are frequently scrambled, or however you'd describe it. 

4) Pulseaudio does not integrate properly with Phonon, even though it DOES in the recent betas of Mandriva and Fedora and is generally supposed to integrate well in KDE 4.4.2. This is due to some packaging mixups.

---

### Post by ranch hand on 2010-04-25
Sounds like normal features in KDE to me.

---

### Post by autumnraine on 2010-04-26
> **ranch hand said:**
> Sounds like normal features in KDE to me.

Very funny, but not true. None of these issues affect other distributions to the best of my knowledge. I've created a [new thread]("http://ubuntuforums.org/showthread.php?t=1462668") to highlight these issues and get people discussing them. Please go there to vote and discuss, if you're interested.

Address for those who don't like hyperlinks:
[http://ubuntuforums.org/showthread.php?t=1462668](http://ubuntuforums.org/showthread.php?t=1462668)

---

### Post by caryb on 2010-04-26
Simple question, what the hell are you using pulseaudio for in KDE/Kubuntu?

Cary

---

### Post by autumnraine on 2010-04-26
> **caryb said:**
> Simple question, what the hell are you using pulseaudio for in KDE/Kubuntu?

Cary

Because I have multiple sound cards - internal, external for audio production, wireless usb headphones that include their own card - and pulseaudio seems to be the quickest and simplest way to configure them all, toggle between them and alter their settings on the fly. If you know of a better way let me know. Pulseaudio, for all its imperfections, is also the most intensively developed sound solution for Linux and the one that will be used by most users for the foreseeable future - Phonon on its own is not there yet, if it even intends to be, Jack is more for audio production, and most of the others are no longer actively developed; ALSA is great but doesn't have the added functionality and easy configurability the others bring. So it's a mistake to think that Pulseaudio should not be used in KDE - one of the major advances of 4.4 was that it integrated with Pulseaudio. This worked rather well in Karmic Kubuntu, so it's also a significant regression.

---

