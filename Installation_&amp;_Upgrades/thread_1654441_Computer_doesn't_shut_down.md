---
title: "Computer doesn't shut down"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by asker2 on 2010-12-28
I have installed Linux Mint 10 on a HP Pro Book 4720s, see here:
[http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=4145330&lang=en&cc=us](http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=4145330&lang=en&cc=us)

After the installation I wanted to shut down the PC and used the button in the menu.
Then appears the Linux Mint Screen and nothing happens. 

I could just shut down the PC by pressing the power button for a few seconds, but that isn't a solution.

What can I do?

---

### Post by dino99 on 2010-12-28
check for maintenace, into a terminal:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

This problem might have logged some usefull errors, watch:

- .xsession-errors into /home (ctrl+h to unhide it)
- system admin logviewer

To force a shutdown:

sudo shutdown now

---

### Post by asker2 on 2010-12-28
The xsession errors:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=de_DE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-SjMyuC
GNOME_KEYRING_CONTROL=/tmp/keyring-SjMyuC
GNOME_KEYRING_CONTROL=/tmp/keyring-SjMyuC
SSH_AUTH_SOCK=/tmp/keyring-SjMyuC/ssh

(polkit-gnome-authentication-agent-1:2145): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2145): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: adding killswitch idx 1 state KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
** Message: applet now removed from the notification area
** (nm-applet:2144): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2144): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-open-terminal extension
ping: unknown host google.com
** Message: applet now embedded in the notification area
Starting gtk-window-decorator

(gtk-window-decorator:2271): GConf-CRITICAL **: gconf_client_set_string: assertion `val != NULL' failed
I/O warning : failed to load external entity "/home/niklas/.compiz/session/1039b61fe989fcf1c612935552066822000000020600025"
ping: unknown host google.com
** (nm-applet:2144): DEBUG: foo_client_state_changed_cb
** (nm-applet:2144): DEBUG: foo_client_state_changed_cb
```

What exactly do you want to know from log viewer?

---

### Post by dino99 on 2010-12-28
there is no error there, only comments :), errors are writen as such.

maybe you have the same issue:
[http://www.lockergnome.com/linux/2010/05/18/ubuntu-10-04-shutdown-problem-fix/](http://www.lockergnome.com/linux/2010/05/18/ubuntu-10-04-shutdown-problem-fix/)

---

### Post by asker2 on 2010-12-28
I could solve the problem.
One reason was the HD Audio Sound, another reason the ACPI.

It is in German, but it should help:
[http://wiki.ubuntuusers.de/herunterfahren#Problemloesungen](http://wiki.ubuntuusers.de/herunterfahren#Problemloesungen)

Thanks for your help, maybe you can look at my other topic

---

