---
title: "Add/Remove programs"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by vasimakhtar on 2006-06-21
Hi,
I am not able to run Add/Remove program. The window of Add/Remove program start checks all dependencies and suddenly went off without showing any list of installed programs.
Any help will be appreciated.
thanks

---

### Post by iball on 2006-06-21
[QUOTE=vasimakhtar]Hi,
I am not able to run Add/Remove program. The window of Add/Remove program start checks all dependencies and suddenly went off without showing any list of installed programs.
Any help will be appreciated.
thanks[/QUOTE]

Try running synaptic from a command line:
```
sudo synaptic
```.

This way, any errors should be displayed in the terminal window.  Can you post any errors here, and then we may be able to help you further.

--Ian

---

### Post by vasimakhtar on 2006-06-21
Hi Ian,
Thanks. and when I run Sudo synaptic it opens a window. That is fine. But I am not able to run from Add/Remove program.
thanks

---

### Post by iball on 2006-06-21
I didn't realise Add / Remove programs was not synaptic, but "gnome-app-install".

Try running "sudo gnome-app-install" from the terminal, and post any error messages.

--Ian

---

### Post by vasimakhtar on 2006-06-22
Thanks. Hereunder is the error message.

root@vasimakhtar://etc/apt# sudo gnome-app-install
warning: could not initiate dbus

** (gnome-app-install:7623): WARNING **: return value of custom widget handler was not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:7623): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:7623): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:7623): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 200, in __init__
    time_source = os.stat("/etc/apt/sources.list")[stat.ST_MTIME]
OSError: [Errno 2] No such file or directory: '/etc/apt/sources.list'
root@vasimakhtar://etc/apt#

---

### Post by rcarring on 2006-06-22
Do you have a sources.list on your system/

Do a whereis from terminal thus:

```

whereis sources.list

```

If you get a 
```

sources.list:

```

 response then you need to create a sources.list

---

### Post by daren on 2006-06-26
Hi
Im having the same problem and showing the same errors ](*,) 
If i do...

> 
whereis sources.list

I get...
> sources:

But dont understand what to do next, sorry :-k 

Daz.

---

### Post by iball on 2006-06-26
Try ```
locate sources.list
```
It should be /etc/apt/sources.list.

If it does exist, try "ls -l /etc/apt/sources.list".  The output should look like:
```
-rw-r--r-- 1 root root 1800 2006-06-04 17:56 /etc/apt/sources.list

```

If it does not exist, then create it, make sure that it has correct permissions:
```
sudo touch /etc/apt/sources.list
sudo chown root /etc/apt/sources.list
sudo chgrp root /etc/apt/sources.list
sudo chmod 644 /etc/apt/sources.list
```

And add the following contents to it:
```
deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb http://au.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe multiverse

deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

I hope this helps
--Ian

---

