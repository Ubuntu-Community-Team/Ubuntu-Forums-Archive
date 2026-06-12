---
title: "Upgrade from 16.10 to 17.04 fails - unknown locale: en_IL"
date: 2017-04-13
forum: Installation &amp; Upgrades
---

### Post by drstrange2 on 2017-04-13
Hi,
I'm trying to upgrade from version 16.10 to 17.04.
When trying to run command "update-manager -d" - the upgrade fails because of "ValueError: unknown locale: en_IL".

Thanks in advance :)

---

### Post by jose_reyes2 on 2017-04-13
[http://www.omgubuntu.co.uk/2017/04/how-to-upgrade-to-ubuntu-17-04](http://www.omgubuntu.co.uk/2017/04/how-to-upgrade-to-ubuntu-17-04)

---

### Post by deadflowr on 2017-04-13
As the release is now open and not in development anymore, no need to run with the -d flag.
Just open the Software and Updates >> Updates >> Notify me of a new Ubuntu version is set to Any new release. 
After that, just open Software Updater and let it run.
Then an option to Upgrade should appear.

As to the locale error:
perhaps review these:
[https://help.ubuntu.com/community/Locale]("https://help.ubuntu.com/community/Locale")
[https://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue]("https://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue")

---

### Post by drstrange2 on 2017-04-13
I've attached the log that I receive after "do-release-upgrade".
```
do-release-upgrade -d
Checking for a new Ubuntu release
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
ERROR:root:gedefaultlocale() failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 399, in get_lang
    (locale_s, encoding) = locale.getdefaultlocale()
  File "/usr/lib/python3.5/locale.py", line 558, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python3.5/locale.py", line 486, in _parse_localename
    raise ValueError('unknown locale: %s' % localename)
ValueError: unknown locale: en_IL
Get:1 Upgrade tool signature [836 B]                                           
Get:2 Upgrade tool [1,268 kB]                                                  
Fetched 1,269 kB in 0s (0 B/s)                                                 
authenticate 'zesty.tar.gz' against 'zesty.tar.gz.gpg' 
extracting 'zesty.tar.gz'
can't load DistUpgradeViewText (unknown locale: en_IL)
can't load DistUpgradeViewGtk3 (unknown locale: en_IL)
can't load DistUpgradeViewKDE (No module named 'PyQt4')
can't load DistUpgradeViewText (unknown locale: en_IL)
No view can be imported, aborting

```

---

### Post by oldos2er on 2017-04-13
Did you run ```
sudo apt update && sudo apt full-upgrade
``` first? And as deadflowr said, leave off the -d.

---

### Post by orentini on 2017-04-17
exact same problem here.

---

### Post by TheYoYoMaN on 2017-04-19
Same here.
Help ?

---

### Post by oldfred on 2017-04-19
There is a bug, supposedly fixed.
[h=1][/h] spyder3: ValueError: unknown locale: en_IL 
[https://bugs.launchpad.net/ubuntu/+source/spyder/+bug/1663397](https://bugs.launchpad.net/ubuntu/+source/spyder/+bug/1663397)

Being from Illinois (post office code IL) I wondered why we were getting our own version of English? :)
[https://www.guyrutenberg.com/2016/04/16/en_il-english-locale-for-israel/](https://www.guyrutenberg.com/2016/04/16/en_il-english-locale-for-israel/)

---

### Post by oren-shm on 2017-04-22
I found generaleye's helpful advice in this post: [https://gist.github.com/smaboshe/d51b102d8a678e0b98e2](https://gist.github.com/smaboshe/d51b102d8a678e0b98e2)
> 
Try adding this line to /etc/environment and rebooting.
LC_ALL="en_US.utf8"

Fixed the problem for me.

---

### Post by epuckop on 2017-05-16
> **oren-shm said:**
> I found generaleye's helpful advice in this post: [https://gist.github.com/smaboshe/d51b102d8a678e0b98e2](https://gist.github.com/smaboshe/d51b102d8a678e0b98e2)

Fixed the problem for me.

Same here :popcorn:

---

