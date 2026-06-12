---
title: "WARNING updateStatus"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jmore9 on 2010-04-12
Anyone know what the following means :

WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2'

---

### Post by 23meg on 2010-04-12
Where exactly are you getting this?

---

### Post by Nightstrike2009 on 2010-04-12
I am not sure know but it seems to be a language file for english/american locale, try to download it again some times things just get stuck. :-)

---

### Post by dino99 on 2010-04-12
have often experience this, i think that your server is busy or overloaded about these languages packages.
Anyway nothing to worry about, try later.

---

### Post by conradin on 2010-04-12
Is that a vailid repo for updating lucid? (I see karmic in that repo)

I tried the syntax modified for lucid but it was still failing for me. You can have a look in this directory (below) for the file you need. Perhaps the name has changed.
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/](http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/)

---

### Post by jmore9 on 2010-04-12
when i tried to upgrade to 10.04 from 9.10 i got the following :

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

I have since filed a bug on this.  I used the update manager -d and thats what i got.  I saw that in some of the logs there were error messages stating that there was no " update site " i guess you call it.

But it ( update manager ) downloaded the update files and then tried to get the files from the update downloads ? which failed.

I also could not find any broken packages on this system .  I did a complete reinstall just to be sure.

---

### Post by jaco223 on 2010-04-12
I've been getting the same error when invoking sudo apt-get update. I haven't touched my
sources.list file. This has been going on nearly a month and a half for me.

---

### Post by jaco223 on 2010-04-12
Here's where I get it.

---

### Post by jmore9 on 2010-04-12
Just for kicks here is some more of the log :

2010-04-12 12:12:01,023 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,117 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,117 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,118 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,119 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,130 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,131 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,131 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,221 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,285 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,296 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,297 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,407 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,407 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,408 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2' 
2010-04-12 12:12:01,408 WARNING updateStatus: dlFailed on 'http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2' 

I havn't got a clue whats going on.

---

### Post by cpmman on 2010-04-12
Is your output:-

```
me@lappy:~$ locale
LANG=en_US.utf8
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=

```If not then your language preferences are wrongly set. There is no en_US translation because it is en_US.utf8 as standard.

I learned the hard way as a en_GB living in es.

---

### Post by jmore9 on 2010-04-12
This is what i get :

jeff@jeff-desktop:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
jeff@jeff-desktop:~$

---

