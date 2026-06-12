---
title: "My software-Center not opening"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by chinex004 on 2010-12-29
I cant seem to open my software centre. I can even install .deb applications. I tried sudo software-centre and this is what i got

ned@ned-buddy:~$ sudo software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 149, in __init__
    self.history = get_apt_history()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 178, in get_apt_history
    apt_history = AptHistory()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 83, in __init__
    self.rescan()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 99, in rescan
    self._scan(self.history_file)
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 116, in _scan
    trans = Transaction(stanza)
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 59, in __init__
    "%Y-%m-%d  %H:%M:%S")
  File "/usr/lib/python2.6/_strptime.py", line 270, in <module>
    _TimeRE_cache = TimeRE()
  File "/usr/lib/python2.6/_strptime.py", line 188, in __init__
    self.locale_time = LocaleTime()
  File "/usr/lib/python2.6/_strptime.py", line 70, in __init__
    self.lang = _getlang()
  File "/usr/lib/python2.6/_strptime.py", line 29, in _getlang
    return locale.getlocale(locale.LC_TIME)
  File "/usr/lib/python2.6/locale.py", line 497, in getlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_NG

---

### Post by matt_symes on 2010-12-29
Hi

Open a terminal and type

```
cat /etc/default/locale
```

Post the results back here.

Also type

```
locale
```

and post the results back.

Kind regards

---

### Post by chinex004 on 2010-12-29
ned@ned-buddy:~$ cat /etc/default/locale
LANG="en_NG"


ned@ned-buddy:~$ locale
LANG=en_NG
LC_CTYPE="en_NG"
LC_NUMERIC="en_NG"
LC_TIME="en_NG"
LC_COLLATE="en_NG"
LC_MONETARY="en_NG"
LC_MESSAGES="en_NG"
LC_PAPER="en_NG"
LC_NAME="en_NG"
LC_ADDRESS="en_NG"
LC_TELEPHONE="en_NG"
LC_MEASUREMENT="en_NG"
LC_IDENTIFICATION="en_NG"
LC_ALL=

---

### Post by matt_symes on 2010-12-29
Hi

You are in Nigeria? I believe your locale should look more like this....

```
en_NG.UTF-8
```

....but, i am just trying to confirm this and how to set it for you.

BTW: Is this a new install or an upgrade? Has this just started happening?

Kind regards

---

### Post by chinex004 on 2010-12-29
I just got the new 10.10 cd from a friend and installed it some days ago. I have been having this problem and i just finished doing a full update.

---

### Post by matt_symes on 2010-12-29
Hi

No problem. Could you open a terminal and type

```
locale -a
```

The -a switch will display all the locales available on your system, not just the one you are using. Post the results back.

Kind regards

---

### Post by chinex004 on 2010-12-29
ned@ned-buddy:~$ locale -a
C
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
ia
POSIX
zh_CN.utf8
zh_HK.utf8
zh_SG.utf8
zh_TW.utf8

---

### Post by matt_symes on 2010-12-29
Hi

```
en_NG
en_NG.utf8
```Good. Lets try changing your locale to en_NG.utf8.

You need to edit the file /etc/default/locale.

Open a terminal and type

```
sudo nano /etc/default/locale
```enter your password. You will not see it echoed to the screen as you type it. This is normal and for security.

change LANG="en_NG" to LANG="en_NG.UTF-8".

Press ctrl + o (small O) to save the file and ctrl x to exit. 

I am not sure if a reboot is required but do it anyway and try the software centre again.

Kind regards

---

### Post by chinex004 on 2010-12-29
Thanks. Worked perfectly.

---

### Post by matt_symes on 2010-12-29
Hi

No problem. Could you mark the thread as solved to help others searching for a solution to the same problem.

Kind regards

---

### Post by hackNperl on 2011-01-02
I am having this same problem.  I added linux mint repositories and installed mint-menu because i liked it.  Ever since I have not been able to open Ubuntu Software Center.

---

### Post by matt_symes on 2011-01-02
Hi

Post the output of

cat /etc/apt/sources.list

Kind regards

---

