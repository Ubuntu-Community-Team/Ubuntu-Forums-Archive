---
title: "Software &amp; Updates Crashes and Will Not Open"
date: 2016-06-22
forum: Installation &amp; Upgrades
---

### Post by Maxattax97 on 2016-06-22
I am unable to open the Software & Updates configuration window in System Settings. The best I have been able to do to understand what is going on is the following output after opening System Settings from terminal and clicking Software & Updates:

    ```
max@Maxattax-Ubuntu:~$ sudo unity-control-center 
    /usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gdk was imported without specifying a version first. Use gi.require_version('Gdk', '3.0') before import to ensure that the right version gets loaded.
      from gi.repository import GObject, Gdk, Gtk, Gio, GLib
    /usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
      from gi.repository import GObject, Gdk, Gtk, Gio, GLib
    Traceback (most recent call last):
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
        return self.get_name_owner(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
        's', (bus_name,), **keywords)
      File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
        message, timeout)
    dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'com.ubuntu.SoftwareProperties': no such name
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/usr/bin/software-properties-gtk", line 101, in <module>
        app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
      File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 141, in __init__
        proxy = bus.get_object("com.ubuntu.SoftwareProperties", "/")
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
        follow_name_owner_changes=follow_name_owner_changes)
      File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 248, in __init__
        self._named_service = conn.activate_name_owner(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 180, in activate_name_owner
        self.start_service_by_name(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 278, in start_service_by_name
        'su', (bus_name, flags)))
      File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
        message, timeout)
    dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program com.ubuntu.SoftwareProperties: Permission denied
```

The same error occurs when executing [FONT=courier new]software-properties-gtk[/FONT] (because AFAIK, it is one and the same).


Software Updater has been having some similar issues, and often crashes with this error:

    ```
max@Maxattax-Ubuntu:~$ sudo update-manager 
    /usr/bin/update-manager:28: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
      from gi.repository import Gtk
    /usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Dbusmenu was imported without specifying a version first. Use gi.require_version('Dbusmenu', '0.4') before import to ensure that the right version gets loaded.
      from gi.repository import Dbusmenu, Unity
    /usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Unity was imported without specifying a version first. Use gi.require_version('Unity', '7.0') before import to ensure that the right version gets loaded.
      from gi.repository import Dbusmenu, Unity
    Traceback (most recent call last):
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
        return self.get_name_owner(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
        's', (bus_name,), **keywords)
      File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
        message, timeout)
    dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/usr/lib/python3/dist-packages/defer/__init__.py", line 487, in _inline_callbacks
        result = gen.send(result)
      File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1613, in _run_transaction_helper
        daemon = get_aptdaemon(self.bus)
      File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
        False),
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
        follow_name_owner_changes=follow_name_owner_changes)
      File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 248, in __init__
        self._named_service = conn.activate_name_owner(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 180, in activate_name_owner
        self.start_service_by_name(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 278, in start_service_by_name
        'su', (bus_name, flags)))
      File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
        message, timeout)
    dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program org.debian.apt: Permission denied
    Traceback (most recent call last):
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
        return self.get_name_owner(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
        's', (bus_name,), **keywords)
      File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
        message, timeout)
    dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/usr/lib/python3/dist-packages/defer/__init__.py", line 487, in _inline_callbacks
        result = gen.send(result)
      File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1613, in _run_transaction_helper
        daemon = get_aptdaemon(self.bus)
      File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
        False),
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
        follow_name_owner_changes=follow_name_owner_changes)
      File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 248, in __init__
        self._named_service = conn.activate_name_owner(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 180, in activate_name_owner
        self.start_service_by_name(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 278, in start_service_by_name
        'su', (bus_name, flags)))
      File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
        message, timeout)
    dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program org.debian.apt: Permission denied
    Traceback (most recent call last):
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
        return self.get_name_owner(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
        's', (bus_name,), **keywords)
      File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
        message, timeout)
    dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1584, in on_error
        error.raise_exception()
      File "/usr/lib/python3/dist-packages/defer/__init__.py", line 130, in raise_exception
        raise self.value.with_traceback(self.traceback)
      File "/usr/lib/python3/dist-packages/defer/__init__.py", line 487, in _inline_callbacks
        result = gen.send(result)
      File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1613, in _run_transaction_helper
        daemon = get_aptdaemon(self.bus)
      File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
        False),
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
        follow_name_owner_changes=follow_name_owner_changes)
      File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 248, in __init__
        self._named_service = conn.activate_name_owner(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 180, in activate_name_owner
        self.start_service_by_name(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 278, in start_service_by_name
        'su', (bus_name, flags)))
      File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
        message, timeout)
    dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program org.debian.apt: Permission denied
    Traceback (most recent call last):
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
        return self.get_name_owner(bus_name)
      File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
        's', (bus_name,), **keywords)
      File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
        message, timeout)
    dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/usr/lib/python3/dist-packages/defer/__init__.py", line 483, in _inline_callbacks
        result = gen.throw(excep)
      File "/usr/lib/python3/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py", line 65, in update
        trans = yield self.client.update_cache(defer=True)
    dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program org.debian.apt: Permission denied
```

Overall, it seems like Python and GTK are vomiting all over the place, but I don't know how to fix it...

There have been various other related issues such as being unable to install packages from the Software Center, or a variety of crashes from trying to update on startup.

I have already tried [reinstalling software center]("https://askubuntu.com/questions/359349/ubuntu-13-04-cant-open-software-updates-software-sources") with no luck, and am afraid to attempt [this solution]("https://askubuntu.com/questions/383234/not-able-to-install-from-ubuntu-software-center?rq=1") as the people in the comments say it's a bad idea. I have come here after finding a lack of answers everywhere else.

---

### Post by Maxattax97 on 2016-06-23
Interestingly, I've encountered another error that is very similar in [FONT=courier new]nvidia-settings[/FONT]. Error output is shown below when trying to save xorg.conf settings.

```
max@Maxattax-Ubuntu:~$ sudo nvidia-settings ** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no
Package xorg-server was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
    return self.get_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
    's', (bus_name,), **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'com.ubuntu.ScreenResolution.Mechanism': no such name


During handling of the above exception, another exception occurred:


Traceback (most recent call last):
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 75, in <module>
    operation_status = main(options)
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 42, in main
    conf = get_xkit_service()
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 33, in get_xkit_service
    service_object = dbus.SystemBus().get_object(SERVICE_NAME, OBJECT_PATH)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program com.ubuntu.ScreenResolution.Mechanism: Permission denied


ERROR: Unable to open X config file '/etc/X11/xorg.conf' for writing.
```

And later, when trying to update [FONT=courier new]pip[/FONT], I find this error:

```
max@Maxattax-Ubuntu:~$ sudo pip install --upgrade pip
The directory '/home/max/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
```

---

### Post by Maxattax97 on 2016-10-23
Solution found, [see here]("https://askubuntu.com/questions/789966/software-updates-crashes-and-will-not-open").

> I had the same issue, Ubuntu 16.04, 64-bit and a reinstall of all the supporting packages:


sudo aptitude reinstall apt apt-utils aptdaemon aptdaemon-data update-manager update-manager-core dbus
solved the issue. For note, a temporary workaround was to run sudo aptd in another terminal before running update-manager, and then update-manager was able to connect to aptd over dbus.


Unfortunately, I can't determine which package was the precise fix now that my issue is solved but if you try reinstalling each one-by-one, you can report back. A number of packages are/were broken on my system by a failed install resulting in odd issues like this one because of missing files, permissions and scripts; reinstalling packages is fixing these problems.

- davidjb

-----
I reinstalled them one by one and it seems dbus was the culprit. Thank you so much, I have been having this problem for months and it is finally resolved! I can't express my gratitude enough!

&#8211; Maxattax
-----


---

