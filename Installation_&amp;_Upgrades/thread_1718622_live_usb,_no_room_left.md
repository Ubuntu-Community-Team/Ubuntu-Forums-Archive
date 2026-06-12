---
title: "live usb, no room left"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by anv on 2011-03-31
I used 2 gb usb key to have ubuntu 10.10 live in it. some 400 mb is not used for installation. If I try to remove unnecessary parts, which I believed would free disc space, did opposite. now I have 0 b free. I also tried to remove synaptic and it didn't let me have just aptitude but offered to install KDE instead with some apt tool from that desktop. these two problems needs to resolve.

---

### Post by dabl on 2011-03-31
2GB is not enough space for Linux with XFCE.  I have Debian Sid XFCE installed on an EEE PC on a 3.3 GB partition, and if I keep it really clean it uses about 2.6GB (with only one kernel available to boot).

You could install the ISO on that 2GB stick, as a "Live CD".  In other words, no installing software, no updating.

Alternatively you could probably install Slax and KDE 3.5 on that stick.

---

### Post by anv on 2011-03-31
I have done the ISO (700 MB) install. with some extra space + app 400 MB not used at all.

---

### Post by C.S.Cameron on 2011-03-31
All of the system files are part of a squash file.
They can't be modified or deleted, (easily).
Changes are stored in a persistence file named casper-rw.
Updating will quickly fill casper-rw, even on a large drive.
casper-rw can be cleaned with Computer Janitor.

---

### Post by anv on 2011-04-01
I installed Janitor, (also .gtk) it probably is inbuilt in Ubuntu_Live but not in Xubuntu. I didn't manage to get any changes under GTK and from commandline it did this:

```
ubuntu@ubuntu:~$ sudo computer-janitor clean --all
ERROR:dbus.proxies:Introspect error on :1.60:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.68" (uid=0 pid=4628 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.60" (uid=0 pid=4462 comm="/usr/bin/python))
ERROR:dbus.connection:Unable to set arguments (set([]),) according to signature None: <type 'exceptions.TypeError'>: Don't know how which D-Bus type to use to encode type "set"
Traceback (most recent call last):
  File "/usr/sbin/computer-janitor", line 35, in <module>
    main()
  File "/usr/share/computerjanitor/computerjanitorapp/cli/main.py", line 312, in main
    options.arguments.func(options.arguments)
  File "/usr/share/computerjanitor/computerjanitorapp/cli/main.py", line 293, in clean
    timeout=3600)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 132, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 556, in call_async
    message.append(signature=signature, *args)
TypeError: Don't know how which D-Bus type to use to encode type "set"
```

EDIT: ahaa [LINK]("http://ubuntuforums.org/showpost.php?p=10279669&postcount=2") you have been here earlier :D ok still I can't see anything on Janitor but if this is what need to do mount and clean that .../apt/.. folder it´s fine for me

Final Edit: just noticed that there was in casper-rw /var/log/kernel.log and some others with size around 100 megs...  removing three of those log files freed around 390 megs space might be good to mention, if others struggle with this same thing.

---

