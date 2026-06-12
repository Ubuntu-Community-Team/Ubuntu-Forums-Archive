---
title: "Probs w/update-manager, software-center &amp; aptdaemon"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by joelk on 2013-06-15
Ubuntu 12.04.2 AMD 64-bit, which is up to date running 3.2.0-45 kernel. I have thee problems that I think are all releated and I don't remember when these problems first started but it was probably several weeks ago. I believe the problem started after a routine update as I have not installed any new packages in months.

The first problem is that nothing happens when I click the "Install Updates" button in Update Manager. The second problem is that Software Center just produces an all white window. The third problem is that aptdaemon won't start.

But I can run apt-get commands manually to get my system up to date. For example all of these commands work fine.

```

$ sudo apt-get clean
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade
```

Synaptic also reports that there are no broken packages or missing dependencies.

I have spent many hours searching for a solution to these problems on Ubuntu forums, an others, but no luck so far. I have tried reinstalling dozens of packages including aptdaemon, software-center, update-manager and python2.7. I am almost a point where I would consider reinstalling Ubunutu, but I want to give this a few more tries.

Now some details. First here is what happens when I try to run aptd.

```

joelk@joelk-ubuntu-amd64:~
Thu Jun 13, 20:34:09 $ sudo aptd -td --replace
[sudo] password for joelk: 
20:54:13 AptDaemon [INFO]: Initializing daemon
Traceback (most recent call last):
  File "/usr/sbin/aptd", line 28, in <module>
    aptdaemon.core.main()
  File "/usr/lib/python2.7/dist-packages/aptdaemon/core.py", line 2203, in main
    daemon = AptDaemon(options, bus=bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/core.py", line 1407, in __init__
    from . import pkcompat
  File "/usr/lib/python2.7/dist-packages/aptdaemon/pkcompat.py", line 55, in <module>
    import aptdaemon.networking
ValueError: bad marshal data (unknown type code)
joelk@joelk-ubuntu-amd64:~
Thu Jun 13, 20:54:13 $ 
```

Here is what happens when I try to run to start Software Center from the command line.

```

joelk@joelk-ubuntu-amd64:~
Sun Jun 02, 06:49:53 $ software-center
2013-06-02 06:50:16,973 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-06-02 06:50:16,978 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-06-02 06:50:17,350 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-06-02 06:50:17,476 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-06-02 06:50:17,823 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 607, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 69, in error_cb
    callback('')
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 607, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 69, in error_cb
    callback('')
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
```

And then this next section repeats endlessly until I close the Software Center window...

```

dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2013-06-02 06:50:18,467 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2013-06-02 06:50:18,466 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
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
```

Along with all of the package reinstallations and apt-get commands I listed previously here are some other things I have tried.

```

$ sudo apt-get -f install
$ sudo apt-get --fix-broken install
$ sudo dpkg --configure --pending
$ rm ~/.cache/software-center -R; unity --reset &
$ sudo dpkg --configure --pending
```

I also tried adding "/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1" to the Startup applications.

This dpkg-reconfigure command just hangs.

```

$ sudo dpkg-reconfigure -a 
```

Any other ideas?

---

### Post by dino99 on 2013-06-15
a few questions:
- is there some packages installed from ppa(s) ? if so, as it seems python is conflicting, use ppa-purge
- is it a cleaned system ? if not, use : clean/autoclean/autoremove/gtkorphan/bleachbit

and of course the logs might help you find some usefull warnings/errors.

---

### Post by joelk on 2013-06-15
No PPAs. I am not one who likes to live on the edge. I have tried cleaning the system many times, but I had not yet used gtkorphan or bleachbit. So I tried those but unfortunately they made no difference.

I have looked through the logs, but unless you know what your are looking for, it's like looking for the proverbial needle in the haystack. I looked but I didn't find anything more than what I saw from the command line. But since I don't know what the root problem is here I admit I could have missed a key clue.

---

### Post by matt_symes on 2013-06-15
Hi

Try reinstalling aptdaemon

```
sudo apt-get install --reinstall aptdaemon
```

What is the output of these commands (I'm iinterested in why dpkg is hanging)

```
sudo dpkg -C
```

```
sudo apt-get check
```

Kind regards

---

### Post by joelk on 2013-06-15
Hmm I thought I had tried reinstalling aptdaemon, but maybe not. Won't hurt to do it again. Unfortunately it did not make any difference.

```

joelk@joelk-ubuntu-amd64:~
Sat Jun 15, 20:34:38 $ sudo apt-get check
[sudo] password for joelk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
joelk@joelk-ubuntu-amd64:~
Sat Jun 15, 20:34:57 $ sudo dpkg -C
joelk@joelk-ubuntu-amd64:~
Sat Jun 15, 20:35:08 $ 

```

It's not dpkg that is hanging, it's dpkg-reconfigure. And it appears it's only the "-a'" argument that has problems. I treid running dpkg-reconfigure on several individual packages and it appeared to work fine.

---

### Post by matt_symes on 2013-06-16
Hi

I think, and i say think as i have never had this problem, this may be due to corrupted pyc files.

There have been report about this for a while now and the errors messages differ slightly but they all point to pyc corruption and, after a system update, that would make sense as that is when the python files are compiled.

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1014244](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1014244)
[https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1093071](https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1093071)
[https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/1058884](https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/1058884)

The above bug reports are all related and the fix seems to be to recompile the .py files to pyc.

First though check there are no hardware problems and check you have space on your root partition.

Run fsck and SMART test on the drive from a LiveCD/USB. Check for errors in dmesg.

Post the output back here of 

```
df -h
```

If they all look good then recompiling the python files for apt-daemon may be the way forward.

Kind regards

---

### Post by joelk on 2013-06-16
Corruption caused by hardware was I thought I also had. I earlier checked my boot hard drive and it's fine. Using your idea I decided to re-install the "python-aptdaemon" package and now all is well! Thanks for the help!

---

### Post by matt_symes on 2013-06-16
Hi

Excellent :). I'm glad it fixed.

Thanks for posting back confirmation that reinstalling that package worked. 

It'll help others and i also know for sure that it is a fix for that problem.

I'll mark this thread as solved for you.

Kind regards

---

