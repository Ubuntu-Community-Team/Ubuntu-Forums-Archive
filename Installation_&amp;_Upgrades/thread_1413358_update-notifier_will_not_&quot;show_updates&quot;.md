---
title: "update-notifier will not &quot;show updates&quot;"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by s7726 on 2010-02-22
The update notifier displays as usual but it will no longer "show updates" either when double clicked or when right clicked and the option is highlighted. the other options in the context menu function as normal.

```
s7726@blackbox:~$ update-notifier --debug-updates

(process:3463): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
(update-notifier:3463): update-DEBUG: update_check()

(update-notifier:3463): update-DEBUG: /usr/lib/update-notifier/apt-check returned 2 (security: 0)

(process:3484): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 107, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 119, in __init__
    logging.exception("setlocale failed")
NameError: global name 'logging' is not defined

```
The part after '2' is returned from apt-check occurred when I tried to double click the icon.

Thanks

Gavin

---

### Post by zooounds on 2010-03-22
I have the same problem. This is my output:

```
$ update-notifier --debug-updates
(update-notifier:4273): update-DEBUG: update_check()

(update-notifier:4273): update-DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)

```

---

### Post by zooounds on 2010-03-22
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

---

### Post by s7726 on 2010-03-22
I'm a terrible community member.

Sorry I fixed this a while ago.

```
sudo dpkg-reconfigure locales
```

That got it done for me. Hope it helps

---

