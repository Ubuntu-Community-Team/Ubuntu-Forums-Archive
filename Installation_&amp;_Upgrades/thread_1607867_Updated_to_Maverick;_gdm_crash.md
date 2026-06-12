---
title: "Updated to Maverick; gdm crash"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by dockingman on 2010-10-28
I just updated to Maverick and now some applications crash Gnome when starting. The session is logged out and the login screen appears. It happened to me at least when starting the VirtualBox application (the GUI only; a headless server VM runs perfectly), and some Python scripts that use TkInter to present a GUI.

The following Python script (from [http://www.pythonware.com/library/tkinter/introduction/hello-tkinter.htm](http://www.pythonware.com/library/tkinter/introduction/hello-tkinter.htm)), for example, crashes gdm:

```
from Tkinter import *
root = Tk()
w = Label(root, text="Hello, world!")
w.pack()
root.mainloop()
```

I traced the error to the gdm-simple-greeter; I get the following in /var/log/gdm/:0-greeter.log:

```
gdm-simple-greeter[6685]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1200034 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1200034 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
gdm-simple-greeter[6685]: WARNING: Unable to lookup user name penglebi: Success
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1200034 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
```

Other log files showing diagnostic errors are the following (the crash happened at 15:40:10, these are the first messages appearing after that time):
/var/log/syslog:
```
Oct 28 15:40:10 ICMS11 NetworkManager[1087]: <error> [1288273210.314545] [nm-man
ager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could no
t get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Oct 28 15:40:10 ICMS11 NetworkManager[1087]: <warn> error requesting auth for or
g.freedesktop.NetworkManager.enable-disable-network: (6) Remote Exception invoki
ng org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop
/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.E
rror.NameHasNoOwner: Remote Exception invoking org.freedesktop.DBus.GetConnectio
nUnixUser() on / at name org.freedesktop.DBus: org.freedesktop.DBus.Error.NameHa
sNoOwner: Could not get UID of name ':1.180': no such name
Oct 28 15:40:10 ICMS11 NetworkManager[1087]: <warn> error requesting auth for or
g.freedesktop.NetworkManager.sleep-wake: (6) Remote Exception invoking org.freed
esktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/
Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.Error.NameHas
NoOwner: Remote Exception invoking org.freedesktop.DBus.GetConnectionUnixUser() 
on / at name org.freedesktop.DBus: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.180': no such name
Oct 28 15:40:10 ICMS11 NetworkManager[1087]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (6) Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.Error.NameHasNoOwner: Remote Exception invoking org.freedesktop.DBus.GetConnectionUnixUser() on / at name org.freedesktop.DBus: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.180': no such name
Oct 28 15:40:10 ICMS11 NetworkManager[1087]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (6) Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.Error.NameHasNoOwner: Remote Exception invoking org.freedesktop.DBus.GetConnectionUnixUser() on / at name org.freedesktop.DBus: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.180': no such name
Oct 28 15:40:10 ICMS11 NetworkManager[1087]: <warn> error requesting auth for org.freedesktop.NetworkManager.use-user-connections: (6) Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.Error.NameHasNoOwner: Remote Exception invoking org.freedesktop.DBus.GetConnectionUnixUser() on / at name org.freedesktop.DBus: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.180': no such name
Oct 28 15:40:10 ICMS11 NetworkManager[1087]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (6) Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.Error.NameHasNoOwner: Remote Exception invoking org.freedesktop.DBus.GetConnectionUnixUser() on / at name org.freedesktop.DBus: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.180': no such name
Oct 28 15:40:10 ICMS11 NetworkManager[1087]: <error> [1288273210.324848] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Oct 28 15:40:10 ICMS11 acpid: client 5642[0:0] has disconnected
Oct 28 15:40:10 ICMS11 acpid: last message repeated 2 times
Oct 28 15:40:10 ICMS11 acpid: client connected from 6645[0:0]
Oct 28 15:40:10 ICMS11 acpid: 1 client rule loaded
Oct 28 15:40:11 ICMS11 acpid: client connected from 6645[0:0]
Oct 28 15:40:11 ICMS11 acpid: 1 client rule loaded
Oct 28 15:40:11 ICMS11 acpid: client connected from 6645[0:0]
Oct 28 15:40:11 ICMS11 acpid: 1 client rule loaded
Oct 28 15:40:12 ICMS11 NetworkManager[1087]: <error> [1288273212.272321] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Oct 28 15:40:12 ICMS11 rtkit-daemon[1813]: Successfully made thread 6694 of process 6694 (n/a) owned by '105' high priority at nice level -11.
Oct 28 15:40:12 ICMS11 rtkit-daemon[1813]: Supervising 1 threads of 1 processes of 1 users.
Oct 28 15:40:12 ICMS11 gdm-simple-greeter[6685]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Oct 28 15:40:12 ICMS11 gdm-simple-greeter[6685]: WARNING: Unable to lookup user name penglebi: Success
Oct 28 15:40:12 ICMS11 rtkit-daemon[1813]: Successfully made thread 6703 of process 6694 (n/a) owned by '105' RT at priority 5.
Oct 28 15:40:12 ICMS11 rtkit-daemon[1813]: Supervising 2 threads of 1 processes of 1 users.
Oct 28 15:40:12 ICMS11 rtkit-daemon[1813]: Successfully made thread 6704 of process 6694 (n/a) owned by '105' RT at priority 5.
Oct 28 15:40:12 ICMS11 rtkit-daemon[1813]: Supervising 3 threads of 1 processes of 1 users.
Oct 28 15:40:14 ICMS11 pulseaudio[6694]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 8.
Oct 28 15:40:14 ICMS11 pulseaudio[6694]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
```

Any suggestions will be appreciated!

---

### Post by phr0ze on 2010-10-28
Same thing happened to me. Once I moved the mouse into the Virtualbox window I GDM crashed.

Found the answer. Uncheck the Xinerama (or whatever it's called) check box on the Nvidia control panel and use twinview instead.

---

### Post by dockingman on 2010-10-28
Great! That solved it.

Just in case someone else needs it:

 - Go to System/Administration/NVIDIA X Server Settings
 - Go to X Server Display Configuration
 - Uncheck the "Enable Xinerama" checkbox
 - Click on the "Configure..." button next to the "Configuration" line; select TwinView
 - Log out and back in

---

### Post by iblag on 2011-03-07
I have an Intel video card and I am getting this exact same error.  I have an updated Maverick installation with gdm version 2.30.5-0ubuntu4.  My /etc/X11/xorg.conf is the default (unconfigured) file.

---

### Post by lister171254 on 2011-05-01
Same problem here with Nvidia card, but don't have the option metioned in the fix/workaround

---

### Post by shoguevara on 2011-07-29
Same problem. Xinerama is not active(separate X screen mode). Ubuntu 10.10 desktop x64, nvidia ION chipset.

---

### Post by Ghostman_132 on 2011-12-31
I have exact same problem but I have intel integrated videocard. How can I fix this? I can't run my virtual machine and sometimes it also do that when I am using vnc.

The error message:  Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow

using Ubuntu 10.10

---

### Post by javadba on 2012-02-20
I have this precise problem too. But i can NOT get into gnome AT ALL.  have to drop to Root shell.  So .. which configuration files are required to be manually edited to get out of this really bad situation.

I have a DELL Inspiron that is explicitly supported by Ubuntu. This really sucks, it seems any nvidia laptop should never get anywhere near ubuntu.

Thing is, i'm not even sure if going to a different distro will resolve these errors,.

---

