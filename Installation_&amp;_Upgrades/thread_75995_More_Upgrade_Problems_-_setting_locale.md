---
title: "More Upgrade Problems - setting locale"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by SeanMC on 2005-10-14
Hi All,

I have upgraded to Breezy and am sat at a login prompt following reboot.

I have tried the fix and re-install of xserver but my problem appears to be with locale settings.

When I run the dpkg-reconfigure xserver-xorg I get the following;

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:

Language = "en_GB:en"
LC_ALL = (unset)
Lang = "en_GB.UTF-8"

are supported and installed on your system.

Perl: Warning: Falling back to the standard loacle ("C")

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

/usr/bin/dpkg-reconfigure: xserver-xorg is broken or not fully installed

Anyone got any suggestions please!

Sean

---

### Post by SeanMC on 2005-10-14
There must be someone out there that can help!!!

---

### Post by assan on 2005-10-14
[QUOTE=SeanMC]Hi All,

I have upgraded to Breezy and am sat at a login prompt following reboot.

I have tried the fix and re-install of xserver but my problem appears to be with locale settings.

When I run the dpkg-reconfigure xserver-xorg I get the following;

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:

Language = "en_GB:en"
LC_ALL = (unset)
Lang = "en_GB.UTF-8"

are supported and installed on your system.

Perl: Warning: Falling back to the standard loacle ("C")

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

/usr/bin/dpkg-reconfigure: xserver-xorg is broken or not fully installed

Anyone got any suggestions please!

Sean[/QUOTE]


Hi,

I have got same problem and I somehow managed to overworked it.
in terminal run aptitude.
then remove open office and then (f10) mark all packages for update. Mark for install all base system. Then run update (g) and wait. Next tie system booted normally.
I hope this will help.
Good luck :)

---

### Post by 11hjpphty76lkjj on 2006-03-02
Did anyone ever find a fix for this?

I'm trying the aptitude fix right now...

---

