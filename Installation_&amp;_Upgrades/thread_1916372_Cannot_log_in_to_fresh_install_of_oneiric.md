---
title: "Cannot log in to fresh install of oneiric"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by quadproc on 2012-01-27
I have been happily running Ubuntu 10.10 and recently decided to add oneiric (11.10) to this system but it doesn't work: When I try to log in, the system just comes back to the login window.

Here are some details: ATI 4870x2 graphics cards, 64 bit Asus P6T SE motherboard, 6 GB RAM, system runs fine on 10.10.  I created a new partition to hold the 11.10 installation.  The Live CD of 11.10 works OK.  The installation from the Live CD to the new partition went OK although it did seem to be slower than usual.  I wanted to be able to use gnome, at least to start with, so I used a terminal to download the gnome compatibility package.

I keep my /home on a different disk drive in its own partition.  Therefore, I first tried the new installation on the default /home that the installation provided and it seemed to work as the Live CD worked.  Then I added the line to /etc/fstab to mount the /home drive by UUID, and I changed the default /home directory from the new installation to old_home.  I created a new /home directory (empty) so that the fstab entry would have a place for the /home partition.

Now, when I boot 11.10 from the disk I get a smallish login window in which I can select one of four options by clicking on the gear: none of them work.  When I select the gnome option I get a few lines of text in the upper left corner but this gets blanked out long before I can read the text, and then I get the same login window.  When I attempt the other three selections I get similar behavior although the design of the screen is slightly different between Unity and Gnome.

Apparently, there is some error occurring in the login process, or just after it.  But I have no idea what the problem is.  Any thoughts?  Thanks.

quadproc

---

### Post by james2b on 2012-01-28
That can be a ownership and permission issue caused by the root user taking ownership of your /home folder and that .Xauthority file as well some times. So I had a like issue which was solved by typing the commands to change /home to your user in run level 3 text mode, or a terminal console. See this thread here at this forum; [http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-cannot-login-and-cannot-shut-down-907558/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-cannot-login-and-cannot-shut-down-907558/)

---

### Post by 2F4U on 2012-01-28
If you can get to a shell (Ctrl-Alt-F1) and then login, you can take a look into .xsession-errors in your home folder.

---

### Post by quadproc on 2012-01-28
Thanks for the suggestions.  I have learned a bit more about the problem but I am still stumped.  

Getting a terminal works; using that, I was able to examine the .xsession-errors file and I learned that it has about a screenful of things in it; the file is below.  I removed a couple of things from my startup task list and found that the errors associated with those tasks went away.  However, there is still something very wrong and I think that I am somehow skirting around the edge of the actual problem.

One thing that I did notice was that my /home partition does get mounted and this means that I do have access to my usual working directory.  I do not seem to have permission or ownership problems with the /home partition/directory.

Here is the present contents of the xsession-errors file:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-BOHZPh
SSH_AUTH_SOCK=/tmp/keyring-BOHZPh/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-BOHZPh
SSH_AUTH_SOCK=/tmp/keyring-BOHZPh/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-BOHZPh
SSH_AUTH_SOCK=/tmp/keyring-BOHZPh/ssh

(polkit-gnome-authentication-agent-1:1862): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1862): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
Starting gtk-window-decorator
Initializing nautilus-gdu extension

(nautilus:1861): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1861): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
I/O warning : failed to load external entity "/home/bob/.compiz/session/10a306cc4a48fbb64e132777183044037600000017660030"
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
** Message: applet now embedded in the notification area
Unable to find a synaptics device.

** (gnome-settings-daemon:1814): WARNING **: Got less number of items in credentials hash table than expected!
** (update-notifier:2059): DEBUG: aptdaemon on bus: 0
** (update-notifier:2059): DEBUG: Skipping reboot required
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(nautilus:1861): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:1861): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(gnome-power-manager:1813): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Shutting down nautilus-gdu extension

--- Hash table keys for warning below:
--> inode/directory
--> Bob Hale
--> bob
--> l2081

(nautilus:1861): Eel-WARNING **: "unique eel_ref_str" hash table still has 4 elements at quit time (keys above)

(nautilus:1861): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time
** Message: applet now removed from the notification area
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```This log file differs from the log file from the older release primarily in the Fatal IO error 11 messages.

quadproc

---

### Post by quadproc on 2012-01-28
Problem apparently solved - I found a .Xauthority file in the /home/user directory which was owned by root (and also was group root).  Removing this file forced the system to create a new .Xauthority file with the correct user.

Thanks for your help.

quadproc

---

