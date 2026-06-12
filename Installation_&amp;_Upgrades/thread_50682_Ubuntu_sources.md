---
title: "Ubuntu sources"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by locutus24 on 2005-07-21
Not sure if this is the correct area? Could someone please post a copy of there sources list, cause when i went to the ubuntu wiki to resetup my sources since i did a reformat, i can not get any programs like mplayer, even though i added the correct sources and did apt-get update to check what i added. 
So please just post your sources list cause this is driving me crazy

---

### Post by darkmatter on 2005-07-21
Sure thing
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://ca.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

#deb ftp://ftp.nerim.net/debian-marillat/ stable main
#deb ftp://ftp.nerim.net/debian-marillat/ unstable main
#deb ftp://ftp.nerim.net/debian-marillat/ testing main

#Primary Mirror (5/17/2005) overloaded
#deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
#deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

## Backports
#deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
#deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hoary universe
#deb http://security.ubuntu.com/ubuntu/ hoary-security universe
deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
deb http://security.ubuntu.com/ubuntu/ hoary-security multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

## Enlightenment DR 17
#deb http://ubuntu.nooms.de/ hoary/
```

Those should work nicely for you.  ;-)

---

### Post by locutus24 on 2005-07-21
Well thank you very much, that fixed all the errors i got when i did an apt update.  :smile:

---

