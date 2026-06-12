---
title: "gnome-settings-daemon problem"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by Luxx on 2007-11-07
I thought I had successfully installed UbuntuStudio 7.10, starting with Ubuntu 7.04, upgrading to 7.10 and then adding Studio. It was done this way because I had no way to burn an ISO image to a DVD, but could burn ISO image under 700MB to a CD. It seemed to be working fine, but when I booted this morning I got the following message:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
----------------------------------------------------
Trying to run "gnome-settings-daemon &" in terminal gave the following result:

jim@ubuntu:~$ 
jim@ubuntu:~$ gnome-settings-daemon &
[1] 6729
jim@ubuntu:~$ 
** (gnome-settings-daemon:6729): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-uoLFkptCSw: Connection refused

(gnome-settings-daemon:6729): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-uoLFkptCSw: Connection refused

(gnome-settings-daemon:6729): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192

** (gnome-screensaver:6737): WARNING **: failed to register with the message bus
----------------------------------------------------
The system seems to be working with some visual annoyances. Firefox has blocks of black, color or weird images appearing, usually in the upper left-hand corner. Text size and screen resolution changed when I put "gnome-settings-daemon &" into terminal, but not consistently. Text in the terminal and text editor enlarged, some web browser tabs showed larger text, some showed very small text. Also the Exit icon in the top right-hand corner changed from a little green man to a door with a red arrow. Changes were temporary. Theme is switching from UbuntuStudio to Ubuntu and back.

Still pretty new to Linux, less than a month in. I haven't come across anything in searches that seems to help. Grateful for any suggestions on how this can be resolved.

---

### Post by whayong on 2007-11-07
I have the same "gnome-settings-daemon" error after logging in.  I first got it after doing sudo apt-get install linux-rt.  I thought installing ubuntustudio would fix it, wrong, it's still there so it has to be something with the linux-rt kernel.

---

### Post by spur on 2007-11-07
I had this error message and occasionally it still pops up, but a reboot makes it go.
I suggest looking for a conflicting program/process as that would create the error message you get.

---

### Post by Luxx on 2007-11-07
I went to System/Preferences/Sessions and added gnome-settings-daemon in the Name field and the Command field. I wasn't sure this was the way to do it, but it seems to be fixed. I still have the weird blocks in the web browser and the desktop. I'm wondering if my graphics card isn't supported by the newer version.

---

