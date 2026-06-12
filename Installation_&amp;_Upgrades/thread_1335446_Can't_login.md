---
title: "Can't login"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by sorenseng on 2009-11-23
I've been running 9.04 with no problems for months.  I upgraded to 9.10 and after downloading updates and rebooting I could not login.  The system would accept my password, repaint the screen to a progress bar screen, and then return to login.  Safe mode also did not work.  Xterm did.

Since I did not have much data on the system, I decided to do a fresh installation from scratch.  I downloaded the new iso, upgraded with no issues, and ran into the same exact issue.  Gnome would not log me in, nor safe mode, but xterm would.  CNTL-ALT-F1 would bring up a terminal session and I could log into that.  .xsession-errors is loaded with stuff beyond my ability to debug.

I noticed a number of similar posts to mine, one of which stated that he simply banged in his credentials a half a dozen times until it let him in.  I tried that, and lo and behold I am now logged in.  But I'm seriously concerned that if I log out or reboot I won't be able to get back in.  Here is the current content of the .xession-errors file, I would greatly appreciate any suggestions.  Thanks in advance for any help.

Greg

---

### Post by sorenseng on 2009-11-23
greg@greg-desktop:~$ more .xsession-errors.old
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X1
1/xinit/xinput.d/default.
greg@greg-desktop:~$ more .xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X1
1/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-9zJaZL/socket
SSH_AUTH_SOCK=/tmp/keyring-9zJaZL/socket.ssh

(gnome-settings-daemon:2424): GLib-CRITICAL **: g_propagate_error:
 assertion `src != NULL' failed
Unable to find a synaptics device.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback
 /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/gr
eg/.config/metacity/sessions/107a76d7a827033c761259001681631916000
00023610022.ms: Failed to open file '/home/greg/.config/metacity/s
essions/107a76d7a827033c76125900168163191600000023610022.ms': No s
uch file or directory

(nautilus:2479): Eel-CRITICAL **: eel_preferences_get_boolean: ***
ertion `preferences_is_initialized ()' failed
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3

(polkit-gnome-authentication-agent-1:2503): GLib-GObject-WARNING *
*: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2503): GLib-CRITICAL **: g_on
ce_init_leave: assertion `initialization_value != 0' failed
** (gnome-panel:247: DEBUG: Adding applet 0.
** (gnome-panel:247: DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:247: DEBUG: Adding applet 1.
** (gnome-panel:247: DEBUG: Adding applet 2.

** (nautilus:2479): WARNING **: No marshaller for signature of sig
nal 'UploadFinished'

** (nautilus:2479): WARNING **: No marshaller for signature of sig
nal 'DownloadFinished'

** (nautilus:2479): WARNING **: No marshaller for signature of sig
nal 'ShareCreateError'
Initializing nautilus-gdu extension
** (gnome-panel:247: DEBUG: Adding applet 3.
** (gnome-panel:247: DEBUG: Adding applet 4.

(gnome-panel:247: Gtk-WARNING **: gtk_widget_size_allocate(): at
tempt to allocate widget with width -3 and height 24
** (gnome-panel:247: DEBUG: Adding applet 5.
** (gnome-panel:247: DEBUG: Adding applet 6.
** (gnome-panel:247: DEBUG: Adding applet 7.
** (gnome-panel:247: DEBUG: Adding applet 8.
** (gnome-panel:247: DEBUG: Adding applet 9.
** (gnome-panel:247: DEBUG: Adding applet 10.
evolution-alarm-notify-Message: Setting timeout for 19084 12590208
00 1259001716
evolution-alarm-notify-Message:  Mon Nov 23 19:00:00 2009

evolution-alarm-notify-Message:  Mon Nov 23 13:41:56 2009

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW mes
sage with a timestamp of 0 for 0x3200003 (Authentica)
Window manager warning: meta_window_activate called by a pager wit
h a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW mes
sage with a timestamp of 0 for 0x3200003 (Authentica)
Window manager warning: meta_window_activate called by a pager wit
h a 0 timestamp; the pager needs to be fixed.
greg@greg-desktop:~$

---

### Post by sorenseng on 2009-11-24
Having played with this a little more, I have discovered that no matter how many times I try to log into gnome, it will always fail until I log into an xterm first.  If I just type exit at the shell prompt and switch the next login attempt back to gnome, it works.

I'll try to post more details shortly.  Thanks.

Greg

---

### Post by sorenseng on 2009-11-24
I have done a number of reboots and login attempts, via gnome, xterm, and a serial terminal session (CTRL-ALT-F1).  The only pattern that allows me to login is this:

Gnome - a failed login attempt.

Xterm - a successful login attempt, type "exit" at the prompt (or muck about in the shell for a while, it doesn't matter).

Gnome - a successful login attempt.

I can have ten failed gnome attempts in a row, once I do a single xterm, gnome will work.  Strangely enough, if I do two (or more) xterms in a row before coming back to gnome, it will not let me in.  Terminal logins have no effect.  After a reboot, trying an xterm first and then a gnome will not work.  The pattern to get in has to be:

Gnome, failed, xterm, successful, then gnome is successful.

I hope this is useful to someone.  I can work around this way indefinitely now that I know the pattern, but it is tedious.  I'd be happy to do whatever testing or reporting anyone would like me to if it helps generate a patch.

Thanks and regards,

Greg

---

