---
title: "Gnome problems after upgrade to 8.04"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by robsic on 2008-04-28
Hi,
The upgrade to 8.04 seem to have broken some Gnome-related stuff.
I did the upgrade with update-manager, remotely through a gdm session. Everything ran smoothly, every package was downloaded and the upgrade began. 

When it stopped for Samba configuration, the dialog window (where you can specify what to do with smb.conf) freezed, and took "forever" to render. I killed the dialog and the upgrade went on, only to stop with the same behaviour for the rest of the package configuration dialogs (Proftpd, apache, amongst others).

I didn't kill those like I did with the Samba dialog, but waited out and got through them. After the last dependency fix, I rebooted the machine and found that the GDM session login was much slower, and that neither nautilus or the Gnome-panel was loaded.

I killed the gdm session and tested some X-applications individually with ssh/X11-forwarding and gnome-control-center, gedit, nautilus for instance, would take several minutes to load, if they load at all. Evolution loaded, but the rendering was really slow. On the other hand, synaptic or xterm would load immediately, which leads me to believe that the problem is Gnome-related.

I downgraded the installation to 7.10, and have also tried to reinstall all gnome-related stuff, but the problem persists, with the exception for Evolution which now loads and renders like it should.

My next step would be a fresh install of 7.10, if anyone here cannot give a hint on what's going on.

I'm sorry for the long post, but very grateful for any answer.

BR/Robert

EDIT:
I finally got gdm to work, but the session hangs just after I login (blank screen). This is the output from syslog:

Apr 28 22:51:29 a1 gdm[10326]: DEBUG: Attempting to parse key string: daemon/Def
aultPath=/bin:/usr/bin
Apr 28 22:51:29 a1 gdm[10326]: DEBUG: Attempting to parse key string: daemon/Bas
eXsession=/etc/gdm/Xsession
Apr 28 22:51:29 a1 gdm[10326]: DEBUG: Running /etc/gdm/Xsession default for user
an on 192.168.0.4:0
Apr 28 22:51:39 a1 gdm[10243]: DEBUG: Timeout occurred for sending message SESSP
ID 10243 10326
Apr 28 22:51:39 a1 gdm[10243]: DEBUG: slave_waitpid: waiting on 10326
Apr 28 22:51:44 a1 gdm[10243]: DEBUG: Attempting to parse key string: xdmcp/Ping
IntervalSeconds=15


And this is the output from .xsession-errors:

gdm[10326]: DEBUG: Attempting to parse key string: daemon/DefaultPath=/bin:/usr/bin
gdm[10326]: DEBUG: Attempting to parse key string: daemon/BaseXsession=/etc/gdm/Xsession
gdm[10326]: DEBUG: Running /etc/gdm/Xsession default for robban on 192.168.0.4:0
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/A1:/tmp/.ICE-unix/10326
W: main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
A1.robban.545$ more .xsession*
gdm[10326]: DEBUG: Attempting to parse key string: daemon/RemoteGreeter=/usr/lib
/gdm/gdmlogin
gdm[10326]: DEBUG: Attempting to parse key string: daemon/PreSessionScriptDir=/e
tc/gdm/PreSession/
gdm[10326]: DEBUG: Forking extra process: /etc/gdm/PreSession/Default
gdm[10327]: DEBUG: Attempting to parse key string: xdmcp/Enable=false
gdm[10327]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/g
dm
gdm[10327]: DEBUG: Attempting to parse key string: daemon/RootPath=/sbin:/usr/sb
in:/bin:/usr/bin

(process:10329): Gtk-WARNING **: This process is currently running setuid or set
gid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:10333): Gtk-WARNING **: This process is currently running setuid or set
gid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp
 -u /var/run/utmp -x "/var/lib/gdm/192.168.0.4:0.Xservers" -h "192.168.0.4" -l "
192.168.0.4:0" "user"
gdm[10326]: DEBUG: Attempting to parse key string: daemon/DefaultPath=/bin:/usr/
bin
gdm[10326]: DEBUG: Attempting to parse key string: daemon/BaseXsession=/etc/gdm/
Xsession
gdm[10326]: DEBUG: Running /etc/gdm/Xsession default for user on 192.168.0.4:0
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput
.d/default.
SESSION_MANAGER=local/A1:/tmp/.ICE-unix/10326
W: main.c: WARNING: called SUID root, but not in group 'pulse-rt'.

---

### Post by robsic on 2008-04-28
Anyone...?

---

### Post by conorsulli on 2008-06-19
This is of no help but I generally just have to reinstalll ubuntu because of faulty upgrades. It is irritating.

---

### Post by dldeskins on 2008-09-30
Has anyone been able to do a repair of gnome? 

I too have this problem after and update.  Anyone?

---

