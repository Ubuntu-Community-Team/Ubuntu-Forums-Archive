---
title: "Software center not working after 12.04 upgrade"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by Nolind on 2012-05-02
Since upgading to 12.04 The Software center does not work. All the packages are there in package manager and I can install from there but with software center I just get a blank white window and the circular hourglass thingy. 

I tried reinstalling via the terminal but it made no difference. It seems to be trying to connect but failing. I'm not getting any error messages or dialogue boxes.:confused:

---

### Post by jerrrys on 2012-05-02
In terminal:

sudo apt-get update

and try the software center again

---

### Post by Nolind on 2012-05-02
Tried that. No change.   I also tried reinstall software-center via apt-get.  no change. :-(

---

### Post by Nolind on 2012-05-03
I tried opening software-center from terminal and it just repeats this;

File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-05-03 13:52:09,747 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-05-03 13:52:09,746 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 154, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-05-03 13:52:09,982 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-05-03 13:52:09,982 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 154, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-05-03 13:52:10,226 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-05-03 13:52:10,226 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 154, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-05-03 13:52:10,468 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-05-03 13:52:10,468 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 154, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-05-03 13:52:10,470 - softwarecenter.ui.gtk3.app - INFO - closing before the regular main loop was run
nolin@nolin-desktop:~$

---

### Post by MarkoF on 2012-09-02
From today I have similar problem. This is what I see in terminal:

DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-02 14:36:17,485 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-02 14:36:17,485 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-02 14:36:17,698 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-02 14:36:17,698 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-02 14:36:17,938 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-02 14:36:17,938 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-02 14:36:18,150 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-02 14:36:18,150 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-02 14:36:18,151 - softwarecenter.ui.gtk3.app - INFO - closing before the regular main loop was run

---

### Post by marinara on 2012-09-06
see this thread, post output of the apt-show-versions command
[http://ubuntuforums.org/showthread.php?t=1330757](http://ubuntuforums.org/showthread.php?t=1330757)

---

### Post by MarkoF on 2012-09-13
> **marinara said:**
> see this thread, post output of the apt-show-versions command
[http://ubuntuforums.org/showthread.php?t=1330757](http://ubuntuforums.org/showthread.php?t=1330757)

This is what that program gives me:

software-center 5.2.5 install ok installed
software-center 5.2.5 precise de.archive.ubuntu.com
software-center/precise uptodate 5.2.5

Now, I am a total beginner when it comes to Linux, so I don't know how to remove repositories of ppa (don't even know what that even is actually), so I can't try the full process described in the thread you linked.

---

### Post by marinara on 2012-09-13
how did you install software-center on lubuntu?

---

### Post by MarkoF on 2012-09-14
I don't understand. I'm using Ubuntu 12.04 LTS which came with Software Center.

EDIT: oh, I am very sorry! Only now have I seen that there is an 'l' in the name of the thread. Please forgive me for confusion. I googled my problem, and Nolind's post was the only that described a problem similar to the one I'm experiencing, so I posted without really looking. :-(  Still, I would very much appreciate any help that you can give me.

---

### Post by marinara on 2012-09-14
please create a new thread

---

### Post by MarkoF on 2012-09-16
OK, I will. Thank you!

---

### Post by mrule on 2013-03-30
Where is the new thread? I am seeing a similar problem and this is the only thread that Google seems to be able to dig up?

---

