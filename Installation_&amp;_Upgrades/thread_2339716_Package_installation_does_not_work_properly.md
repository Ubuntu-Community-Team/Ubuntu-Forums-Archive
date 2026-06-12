---
title: "Package installation does not work properly"
date: 2016-10-12
forum: Installation &amp; Upgrades
---

### Post by biagiopas on 2016-10-12
Hello everybody, 

linux ubuntu 16.04 LTSx64 desktop, this ubuntu istance was installed 4 mounths ago, but now somethings dont work

installation of packages does not work for me:

 - ubuntu_software_center opens, but if I write the name of the software, and I click "Install", the installation will not start :cry: 

 - installing the .deb package clicking on it, it does not work either  [-(

 - "$ sudo apt-get install PACKAGENAME" works!

//////////////////////////////////////////////////////
//////////////////////////////////////////////////////
//////////////////////////////////////////////////////

the output of $ sudo apt-get update, it seems that something is not right about the external repository (I regret, some texts are in Italian)

$  sudo apt-get update
```

Trovato:1 http://archive.canonical.com/ubuntu xenial InRelease
Trovato:2 http://it.archive.ubuntu.com/ubuntu xenial InRelease                 
Ign:3 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial InRelease    
Scaricamento di:4 http://it.archive.ubuntu.com/ubuntu xenial-updates InRelease [95,7 kB]
Scaricamento di:5 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease [23,9 kB]
Scaricamento di:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [94,5 kB]
Ign:7 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial Release      
Scaricamento di:8 http://it.archive.ubuntu.com/ubuntu xenial-backports InRelease [92,2 kB]
Scaricamento di:9 http://ppa.launchpad.net/ondrej/php/ubuntu xenial/main amd64 Packages [45,8 kB]
Scaricamento di:10 http://ppa.launchpad.net/ondrej/php/ubuntu xenial/main i386 Packages [45,9 kB]
Scaricamento di:11 http://it.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [396 kB]
Ign:12 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 Packages
Ign:13 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main i386 Packages
Ign:14 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it_IT
Ign:16 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it
Scaricamento di:17 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [390 kB]
Ign:18 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-en
Ign:19 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:20 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main DEP-11 64x64 Icons
Ign:12 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 Packages
Scaricamento di:21 http://it.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [150 kB]
Ign:13 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main i386 Packages
Scaricamento di:22 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [335 kB]
Ign:14 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main all Packages
Scaricamento di:23 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [152 kB]
Scaricamento di:24 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [331 kB]
Ign:15 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it_IT
Scaricamento di:25 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [116 kB]
Ign:16 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it
Scaricamento di:26 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [101 kB]
Ign:18 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-en
Scaricamento di:27 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [98,4 kB]
Ign:19 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:20 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main DEP-11 64x64 Icons
Ign:12 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 Packages
Ign:13 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main i386 Packages
Ign:14 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it_IT
Scaricamento di:28 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [148 kB]
Ign:16 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it
Ign:18 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-en
Ign:19 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:20 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main DEP-11 64x64 Icons
Ign:12 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 Packages
Ign:13 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main i386 Packages
Scaricamento di:29 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [62,9 kB]
Ign:14 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it_IT
Scaricamento di:30 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [80,0 kB]
Ign:16 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it
Ign:18 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-en
Ign:19 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:20 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main DEP-11 64x64 Icons
Scaricamento di:31 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62,9 kB]
Ign:12 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 Packages
Ign:13 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main i386 Packages
Ign:14 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it_IT
Scaricamento di:32 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [44,4 kB]
Ign:16 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it
Scaricamento di:33 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [44,4 kB]
Ign:18 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-en
Ign:19 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 DEP-11 Metadata
Scaricamento di:34 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [2.266 B]
Scaricamento di:35 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [4.103 B]
Ign:20 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main DEP-11 64x64 Icons
Err:12 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 Packages
  404  Not Found
Ign:13 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main i386 Packages
Ign:14 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it_IT
Ign:16 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-it
Ign:18 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main Translation-en
Ign:19 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:20 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial/main DEP-11 64x64 Icons
Recuperati 2.916 kB in 4s (692 kB/s)
Lettura elenco dei pacchetti... Fatto
W:  Target Packages (partner/binary-amd64/Packages) is configured multiple  times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target Packages (partner/binary-i386/Packages) is configured multiple  times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target Packages (partner/binary-all/Packages) is configured multiple  times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target Translations (partner/i18n/Translation-it_IT) is configured  multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target Translations (partner/i18n/Translation-it) is configured  multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target Translations (partner/i18n/Translation-en) is configured  multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target DEP-11 (partner/dep11/Components-amd64.yml) is configured  multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured  multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W: The repository 'http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Impossibile scaricare alcuni file di indice: saranno ignorati o verranno usati quelli vecchi.
W:  Target Packages (partner/binary-amd64/Packages) is configured multiple  times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target Packages (partner/binary-i386/Packages) is configured multiple  times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target Packages (partner/binary-all/Packages) is configured multiple  times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target Translations (partner/i18n/Translation-it_IT) is configured  multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target Translations (partner/i18n/Translation-it) is configured  multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target Translations (partner/i18n/Translation-en) is configured  multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target DEP-11 (partner/dep11/Components-amd64.yml) is configured  multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W:  Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured  multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91

```

///////////////////////////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////

when you try to open: System Setup >> Software and Updates
You display an error popup
the error is the same reported below

???('The permission of the setuid helper is not correct')???

the error is also log in 
/var/crash/_usr_bin_software-properties-gtk.1000.crash

////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////
 
launch software-center from the command line

$ software-center

after attempting to install a software displays a popup with error message
the terminal returns the following output with error messages

```

/usr/bin/software-center:25: PyGIWarning: Gtk was imported without  specifying a version first. Use gi.require_version('Gtk', '3.0') before  import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject
/usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29:  PyGIWarning: WebKit2 was imported without specifying a version first.  Use gi.require_version('WebKit2', '4.0') before import to ensure that  the right version gets loaded.
  from gi.repository import WebKit2 as webkit
2016-10-10 21:27:45,328 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23:  PyGIWarning: PangoCairo was imported without specifying a version  first. Use gi.require_version('PangoCairo', '1.0') before import to  ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GLib, PangoCairo
2016-10-10 21:27:45,358 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 607, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 69, in error_cb
    callback('')
   File  "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py",  line 166, in _register_active_transactions_watch
    apt_daemon = client.get_aptdaemon(bus=bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
    False),
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of  the setuid helper is not correct
2016-10-10 21:27:45,642 -  softwarecenter.region - WARNING - failed to use geoclue:  'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has  no usable Address providers'
2016-10-10 21:27:45,902 -  softwarecenter.backend.reviews - WARNING - Could not get usefulness from  server, no username in config file
2016-10-10 21:27:45,903 -  softwarecenter.plugin - INFO - activating plugin '<module  'webapps_activation' from  '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 607, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 69, in error_cb
    callback('')
   File  "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py",  line 166, in _register_active_transactions_watch
    apt_daemon = client.get_aptdaemon(bus=bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
    False),
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of  the setuid helper is not correct
2016-10-10 21:27:45,933 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2016-10-10  21:27:46,435 - softwarecenter.db.update - WARNING - failed to load file  /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle  protocol: 3
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/videoplayer.py:29:  PyGIWarning: Gst was imported without specifying a version first. Use  gi.require_version('Gst', '1.0') before import to ensure that the right  version gets loaded.
  from gi.repository import Gst
/usr/bin/software-center:184: Warning: Source ID 69 was not found when attempting to remove it
  Gtk.main()
/usr/bin/software-center:184: Warning: Source ID 148 was not found when attempting to remove it
  Gtk.main()
2016-10-10  21:27:49,101 - softwarecenter.db.update - WARNING - failed to load file  /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle  protocol: 3
2016-10-10 21:27:49,945 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 489, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1613, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
    False),
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of  the setuid helper is not correct
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 489, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1613, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
    False),
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of  the setuid helper is not correct
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of  the setuid helper is not correct
2016-10-10 21:27:58,230 -  softwarecenter.backend - WARNING - _on_trans_error: 'DBusException('The  permission of the setuid helper is not correct',)' 'None' 'amule'

```

////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////

someone had the same error but no solution can be found

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1218701](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1218701)
software-properties-gtk crashed with dbus.exceptions.DBusException in call_blocking(): org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of the setuid helper is not correct 

////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////

I tried to install both: software-center, and ubuntu-software, 
with negative results, now I uninstalled them both

////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////

please, do you have suggestions to solve the problem ??? thanks from now

---

### Post by biagiopas on 2016-10-12
as suggested on this forum
[https://ubuntuforums.org/showthread.php?t=2274349&page=2&p=13269148#post13269148](https://ubuntuforums.org/showthread.php?t=2274349&page=2&p=13269148#post13269148)

 - manually removed the external repository

 - Clean the apt cache
sudo rm -r /var/lib/apt/lists/*

sudo apt-get update
sudo apt-get upgrade

apt-get update , now  does not display any error!!!

 - reinstalled  software-center

However, the error occurs again

the panel "Software and Updates" does not open, and software-center does not install ... the error is the same as before

//////////////////////////////////////////////////////////////////////////
//////////////////////////////////////////////////////////////////////////
//////////////////////////////////////////////////////////////////////////

launch software-center from the command line

$ software-center
```

/usr/bin/software-center:25:  PyGIWarning: Gtk was imported without specifying a version first. Use  gi.require_version('Gtk', '3.0') before import to ensure that the right  version gets loaded.
  from gi.repository import Gtk, GObject
/usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29: PyGIWarning: WebKit2 
was  imported without specifying a version first. Use  gi.require_version('WebKit2', '4.0') before import to ensure that the  right version gets loaded.
  from gi.repository import WebKit2 as webkit
2016-10-12 16:27:34,745 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23:  PyGIWarning: PangoCairo was imported without specifying a version  first. Use gi.require_version('PangoCairo', '1.0') before import to  ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GLib, PangoCairo
2016-10-12 16:27:34,774 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 607, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 69, in error_cb
    callback('')
   File  "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py",  line 166, in _register_active_transactions_watch
    apt_daemon = client.get_aptdaemon(bus=bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
    False),
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of  the setuid helper is not correct
2016-10-12 16:27:34,912 -  softwarecenter.region - WARNING - failed to use geoclue:  'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has  no usable Address providers'
2016-10-12 16:27:35,171 -  softwarecenter.backend.reviews - WARNING - Could not get usefulness from  server, no username in config file
2016-10-12 16:27:35,172 -  softwarecenter.plugin - INFO - activating plugin '<module  'webapps_activation' from  '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 607, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 69, in error_cb
    callback('')
   File  "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py",  line 166, in _register_active_transactions_watch
    apt_daemon = client.get_aptdaemon(bus=bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
    False),
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of  the setuid helper is not correct
2016-10-12 16:27:35,203 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py:190:  Warning: Source ID 70 was not found when attempting to remove it
  Gtk.main_iteration()
2016-10-12  16:27:36,000 - softwarecenter.db.update - WARNING - failed to load file  /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle  protocol: 3
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/videoplayer.py:29:  PyGIWarning: Gst was imported without specifying a version first. Use  gi.require_version('Gst', '1.0') before import to ensure that the right  version gets loaded.
  from gi.repository import Gst
/usr/bin/software-center:184: Warning: Source ID 147 was not found when attempting to remove it
  Gtk.main()
2016-10-12  16:27:38,686 - softwarecenter.db.update - WARNING - failed to load file  /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle  protocol: 3
2016-10-12 16:27:39,248 - softwarecenter.fixme - WARNING -  logs to the root logger:  '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410,  '_introspect_error_handler')'
2016-10-12 16:27:39,247 - dbus.proxies -  ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials:  dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply:  Message recipient disconnected from message bus without replying
2016-10-12 16:27:39,688 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0

```

try to install amule ... click [install]

```

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 489, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1613, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
    False),
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of  the setuid helper is not correct
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 489, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1613, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1701, in get_aptdaemon
    False),
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of  the setuid helper is not correct
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of  the setuid helper is not correct
2016-10-12 16:29:24,510 -  softwarecenter.backend - WARNING - _on_trans_error: 'DBusException('The  permission of the setuid helper is not correct',)' 'None' 'amule'


```

---

### Post by biagiopas on 2016-10-13
maybe I'm going in the direction of solving,
few days ago, I did something stupid, sudo chmod 777 /usr/lib/, 
Then I remedied crudely, with sudo chmod 755 /usr/lib/,
Now I should find a way to set,  for each file/folder in /usr/lib/, its own correct permissions

---

