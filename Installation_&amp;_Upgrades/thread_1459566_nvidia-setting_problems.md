---
title: "nvidia-setting problems"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by kieran_uk on 2010-04-21
When trying to conigure via nvidia-setting using root (sudo) and then saving to config file I get the ' Unable to open X config file '/etc/X11/xorg.conf' for writing.' in a message box - below is what i get on terminal:

```
Traceback (most recent call last):
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 75, in <module>
    operation_status = main(options)
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 51, in main
    exit_code = conf.backupAndWriteXorgConf([options.backup_filename, options.filename])
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 649, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 244, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: backupAndWriteXorgConf is not a valid method of interface com.ubuntu.ScreenResolution.Mechanism


ERROR: Unable to open X config file '/etc/X11/xorg.conf' for writing.

```Tried sudo nvidia-xconfig before nvidia-settings (used to work a treat before) and even removing the xorg.conf and the backups too to start afresh and still getting the above errors!

Drivers: 195.36.15
 GFX Card: nvidia geforce 8800GTX (768mb) PCI-E
Monitors: Samsung Syncmaster 2494hw & Samsung Syncmaster 2232bw  (both DVI)

Thanks in advance and regards, Kieran.

---

### Post by dabl on 2010-04-21
Since nvidia-settings is a graphical package (runs in X), to start it in root mode you should not start it with "sudo", which is for character mode (terminal/CLI) packages. Use gksudo (for Gnome) or kdesudo (for KDE).  So, Alt-F2 "gksudo nvidia-settings" is the way to launch it.

That may or may not be directly relevant to the failure you observed.

---

### Post by doas777 on 2010-04-21
usually that means that you have an line that is malformed or unrecognized by the nvidia-xconfig. the easiest answer is to backup and remove /etc/X11/xorg.conf

---

### Post by kieran_uk on 2010-04-21
Tried gksudo nvidia-settings and still wont save xorg.conf and even sudo rm /etc/X11/xorg.conf* to remove the config files inc. backups and then sudo nvidia-xconfig afterwards to remake the config files - yet again same errors!! :/

Oh well life is a trial lol :D

Regards Kieran.

---

### Post by kieran_uk on 2010-04-21
Solved the problem by restoring from a clonezilla image, now working perfectly - being a long suffering windows power-user clonezilla/ghost images became my friend years ago, got me out of hot water countless times! :lol:

A kind thank-you for all who tried to help me.

Kind Regards, Kieran. :D

---

### Post by zim2dive on 2010-04-22
I've got the same problem... but no Clonezilla backup to roll back to...

[http://www.nvnews.net/vbulletin/showthread.php?t=150126](http://www.nvnews.net/vbulletin/showthread.php?t=150126)

so you rolled back your nvidia driver with the Clonezilla rollback?

Did you re-upgrade the driver and no longer see the issue?

EDIT: I could start a new thread, or could you mark yours back as unsolved?

---

### Post by taur on 2010-04-28
[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/477309](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/477309)

It seems to be a known bug, the fix mentioned in the comments did not work for me

---

### Post by zim2dive on 2010-04-29
> **taur said:**
> [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/477309](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/477309)

It seems to be a known bug, the fix mentioned in the comments did not work for me

thanks.  good to know its not just me :)

---

