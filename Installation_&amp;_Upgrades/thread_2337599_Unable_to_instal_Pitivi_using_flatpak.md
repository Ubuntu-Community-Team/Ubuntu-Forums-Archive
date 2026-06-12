---
title: "Unable to instal Pitivi using flatpak"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by gmsalomao2 on 2016-09-20
After I tried to install Pitivi using flatpak over an older version installed via .deb file, the program didn't open. So I treid to uninstall both from flatpak and from .deb. Then flatpak kept saying there was no "Pitivi master" to uninstall, so I searched for files with "pitivi" on their names and deleted them all.
Now, when I try to install Pitivi, I get this error. Don't know what to do.

```
~$ curl https://git.gnome.org/browse/pitivi/plain/build/flatpak/pitivi-flatpak -Sso pitivi-flatpak && \
>    chmod +x pitivi-flatpak && \
>   ./pitivi-flatpak --branch=stable --update
Updating org.gnome.Platform
Updating runtime org.gnome.Platform, branch 3.20
No updates.
Updating related: org.gnome.Platform.Locale
No updates.
Updating org.gnome.Platform.Locale
Updating runtime org.gnome.Platform.Locale, branch 3.20
No updates.
Installing org.pitivi.Pitivi
error: GPG signatures found, but none are in trusted keyring
Traceback (most recent call last):
  File "./pitivi-flatpak", line 613, in <module>
    app_flatpak.run()
  File "./pitivi-flatpak", line 416, in run
    self.update_all()
  File "./pitivi-flatpak", line 557, in update_all
    m.update()
  File "./pitivi-flatpak", line 291, in update
    return self.install()
  File "./pitivi-flatpak", line 287, in install
    comment="Installing %s" % self.name)
  File "./pitivi-flatpak", line 128, in flatpak
    return subprocess.check_call(command)
  File "/usr/lib/python3.5/subprocess.py", line 581, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['flatpak', 'install', '--user', 'pitivi', 'org.pitivi.Pitivi', 'stable']' returned non-zero exit status 1

```

---

### Post by gmsalomao2 on 2016-09-20
After deleting **~/.local/share/flatpak** and **~/.var** I could reinstall Pitivi.
But now I got many errors and even clicking the button to create a new project crashes Pitivi instantly.

> ~$ curl [https://git.gnome.org/browse/pitivi/plain/build/flatpak/pitivi-flatpak](https://git.gnome.org/browse/pitivi/plain/build/flatpak/pitivi-flatpak) -Sso pitivi-flatpak && \
>    chmod +x pitivi-flatpak && \
>   ./pitivi-flatpak --branch=stable --update
Updating org.gnome.Platform
Updating runtime org.gnome.Platform, branch 3.20
No updates.
Updating related: org.gnome.Platform.Locale
No updates.
Updating org.gnome.Platform.Locale
Updating runtime org.gnome.Platform.Locale, branch 3.20
No updates.
Installing org.pitivi.Pitivi

6 delta parts, 29 loose fetched; 115240 KiB transferred in 214 seconds                                                                                
Running org.pitivi.Pitivi (stable)
Couldn't set locale. /app/share/locale unsupported locale setting

** (gst-plugin-scanner:3): CRITICAL **: Couldn't g_module_open libpython. Reason: /usr/lib/libpython3.4m.so: cannot open shared object file: No such file or directory

** (gst-plugin-scanner:3): CRITICAL **: Couldn't g_module_open libpython. Reason: /usr/lib/libpython3.4m.so: cannot open shared object file: No such file or directory

(gst-plugin-scanner:3): Clutter-WARNING **: Locale not supported by C library.
Using the fallback 'C' locale.
libGL error: failed to open drm device: No such file or directory
libGL error: failed to load driver: i965

(pitivi:2): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Gtk-Message: Failed to load module "unity-gtk-module"

** (pitivi:2): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-lKYgqqdDj5: Connection refused
Missing soft dependency:
- pycanberra not found on the system
    -> enables sound notifications when rendering is complete
Missing soft dependency:
- GnomeDesktop not found on the system
    -> file thumbnails provided by GNOME's thumbnailers

(pitivi:2): Gtk-WARNING **: Allocating size to GtkToggleToolButton 0x38e9770 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
Traceback (most recent call last):
  File "./pitivi-flatpak", line 613, in <module>
    app_flatpak.run()
  File "./pitivi-flatpak", line 432, in run
    self.app.run_app(self.args)
  File "./pitivi-flatpak", line 302, in run_app
    comment="Running %s (%s)" % (self.name, self.branch))
  File "./pitivi-flatpak", line 128, in flatpak
    return subprocess.check_call(command)
  File "/usr/lib/python3.5/subprocess.py", line 581, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['flatpak', 'run', '--branch=stable', 'org.pitivi.Pitivi']' returned non-zero exit status 1

---

