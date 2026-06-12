---
title: "Windows Mobile 6.1 sync w/ Ubuntu 9.1 help"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by emptybeer on 2009-12-21
I want to switch to Ubuntu from XP, but my WM phone is holding me back b/c of sync issues.  I installed synce.  Everything appears to work fine until I try the actual sync using 

Below is what I get.  Thanks in advance for any help.

ubuntu@ubuntu:~$ msynctool --sync synce-sync
Synchronizing group "synce-sync" 
DEBUG:SynCE:Connect() called
Member 2 of type evo2-sync just connected
Member 1 of type synce-opensync-plugin just connected
All clients connected or error
DEBUG:SynCE:get_changeinfo() called
DEBUG:SynCE:slow sync requested for Contacts
DEBUG:SynCE:slow sync requested for Calendar
DEBUG:SynCE:slow sync requested for Tasks
INFO:SynCE:initiating device synchronization
Member 2 of type evo2-sync just sent all changes
Traceback (most recent call last):
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 152, in get_changeinfo
    self._TriggerSync()
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 117, in _TriggerSync
    self.engine.Synchronize()
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.synce.SyncEngine.Error.NoBoundPartnership: 
Member 1 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
Member 1 of type synce-opensync-plugin just disconnected
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
DEBUG:SynCE:finalize() called
Error while synchronizing: Unable to read from one of the members
ubuntu@ubuntu:~$

---

### Post by jgrocha on 2009-12-25
Hi,

I noticed that connection problems can originate that error.

Try to do:
sudo /etc/init.d/firestarter stop
(and try to get rid of firestarter)
or, if you use ufw, try to disable it:
sudo ufw disable

Merry Christmas!

---

### Post by jgrocha on 2010-01-02
Update

"dbus.exceptions.DBusException: org.synce.SyncEngine.Error.NoBoundPartnership"

The message seems related with the partnership.
Check if the partnership do exist.

Regards,

Jorge

---

