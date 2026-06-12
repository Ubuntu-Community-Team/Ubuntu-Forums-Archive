---
title: "Unable to Log In; Gtk+ and/or dbus Error?"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by cjdahl60 on 2008-02-05
I left my Ubuntu 7.10 box running overnight. When I checked it in the morning, the lights on the keyboard were flashing. Neither the keyboard nor the mouse were active or could wake the system. I manually powered down and rebooted. When I logged in, I got an error message that said:

Your session only lasted less than 10 seconds. If you have not logged on yourself, this could mean that there is an installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem.

View Details (~/.xsession-errors file)




Details displayed when box checked:

(process:4481): Gtk-warning: This process is currently running setuid or setgid. This is not a supported use of Gtk+. You must create a helper program instead. For further details see: [www.gtk.org/setuid.html](www.gtk.org/setuid.html)

Refusing to initialize Gtk+

(process: 4485): Gtk-warning: This process is currently running setuid or setgid. This is not a supported use of Gtk+. You must create a helper programinstead. For urther details see: [www.gtk.org/setuid.html](www.gtk.org/setuid.html)

Refusing to initialize Gtk+

/etc/gdm/xsession: beginning session startup………..
Session-Manager=local/cjdahl60-desktop:/tmp/.ICE-unix/4478
Failed to start message bus: failed to read directory “etc/dbus-1/session.d” no such file or directory
dbus-daemon exited unexpectedly

error: file gsm-dbus.c: line 118 (gsm-dbus-daemon-start): assertion fialed: (dbus-daemon-pid !=0) aborting

I have since logged in fail safe terminal mode and successfully stopped and restarted the dbus process to no effect. I have also run a sudo apt-get -f install to see if there were any incomplete/aborted install programs. Everything looked OK.

Any suggestions would be greatly appreciated.

---

