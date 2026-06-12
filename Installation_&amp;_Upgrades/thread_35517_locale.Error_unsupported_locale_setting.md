---
title: "locale.Error: unsupported locale setting"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by macewan on 2005-05-19
Before I look into what I've apparently screwed up with locales - any quick suggestions?


```
Fetched 1964kB in 4s (460kB/s)
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 35, in ?
    import apt_listchanges
  File "/usr/lib/site-python/apt_listchanges.py", line 24, in ?
    locale.setlocale(locale.LC_ALL,'')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en",
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...
Selecting previously deselected package xmms.
(Reading database ... 163477 files and directories currently installed.)
Unpacking xmms (from .../xmms_1.2.10-2ubuntu1_i386.deb) ...
Setting up console-data (2002.12.04dbs-48ubuntu11) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en",
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en",
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Looking for keymap to install:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en",
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
NONE
Usage: install-keymap [ keymap_file | NONE | KERNEL ]
dpkg: error processing console-data (--configure):
 subprocess post-installation script returned error exit status 1
Setting up xmms (1.2.10-2ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en",
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Errors were encountered while processing:
 console-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Heading off to work at the moment - prethanks for any suggestions  :grin:

---

### Post by wrtrdood on 2005-07-12
Dunno if you got this fixed or not but I had a similar problem and managed to cure it by running:

sudo dpkg-reconfigure locales

---

### Post by Aijaz Akhtar on 2005-07-13
I had similar problems. I used Syneptic to add translation modules and added Hindi, Bengali and Urdu. But nothing works, it asks me to â€˜install language supportâ€™. What exactly is the language pack under translation, and where I can get the language support installed? I have Unicode fonts of all the languages, how can I install them. So far I could not get any interface where I can install new fonts, or will copying fonts in user/x11/xkb/fonts (or wherever is the fonts folder) will do? And also I would, like to add openoffice l10n packages. Are they available in the install CD? In Live CD, the Hindi interface seemed all right but I am not getting that!!

---

### Post by macewan on 2005-07-13
[QUOTE=Aijaz Akhtar]I had similar problems. I used Syneptic to add translation modules and added Hindi, Bengali and Urdu. But nothing works, it asks me to â€˜install language supportâ€™. What exactly is the language pack under translation, and where I can get the language support installed? I have Unicode fonts of all the languages, how can I install them. So far I could not get any interface where I can install new fonts, or will copying fonts in user/x11/xkb/fonts (or wherever is the fonts folder) will do? And also I would, like to add openoffice l10n packages. Are they available in the install CD? In Live CD, the Hindi interface seemed all right but I am not getting that!![/QUOTE]
 Wish I could help but I don't know the answer.

---

### Post by anil_robo on 2005-12-22
Hi, I've written a little how-to on Hindi and similar languages in Ubuntu here:
[http://ubuntuforums.org/showthread.php?t=102778&highlight=hindi](http://ubuntuforums.org/showthread.php?t=102778&highlight=hindi)

---

