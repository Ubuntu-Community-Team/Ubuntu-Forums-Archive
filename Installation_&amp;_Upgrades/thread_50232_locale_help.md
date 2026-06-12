---
title: "locale help"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by moonshot on 2005-07-19
I've tried searching, and searching, and searching for a fix to this.  I've tried some of the stuff I've found, but can't seem to fix the problem.

_The Error_ 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "C",
        LC_ALL = "en_US",
        LANG = "en_US"
    are supported and installed on your system.

_locale command output_ 
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US
LC_CTYPE="en_US"
LC_NUMERIC="en_US"
LC_TIME="en_US"
LC_COLLATE="en_US"
LC_MONETARY="en_US"
LC_MESSAGES="en_US"
LC_PAPER="en_US"
LC_NAME="en_US"
LC_ADDRESS="en_US"
LC_TELEPHONE="en_US"
LC_MEASUREMENT="en_US"
LC_IDENTIFICATION="en_US"
LC_ALL=en_US

_locale -a command output_ 

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8


Any and all help would be greatly appreciated.

---

### Post by moonshot on 2005-07-20
Bump....seems I"m not the only one having this problem.

---

