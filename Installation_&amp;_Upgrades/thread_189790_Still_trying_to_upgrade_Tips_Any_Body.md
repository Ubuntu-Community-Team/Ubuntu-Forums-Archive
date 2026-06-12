---
title: "Still trying to upgrade: Tips Any Body?"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by lakelovers on 2006-06-05
I lost my xserver after an upgrade failure. I'm now backup on Breezy though my screen resolution is very low and xserver fails when I try to raise the resolution. That's another story. I'm still determined to get Dapper up and running. My problems have been  unmet dependencies. I've researched and posted a number of times but can't find the key to my solution. I'm posting my source list again. Are there errors that I don't see?

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

---

### Post by SkyNet2029 on 2006-06-05
Unless you got an error that specifically stated that 'apt couldn't stat '  the repository, then its not a sources error. Check out this link [http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2") for a double check against this clean sources.list for Dapper though.

You should be able to use aptitude to fix your unmet dependencies issues (as well as be able to 'eyeball' just what those dependency issues are)like this
```
$sudo aptitude
```
from a terminal/Konsole/geTTY. 
Then just update your package list and choose 'Find Broken' from the menu (F-10). This will show you exactly what the issues are. From there you should be able to fix as you need.

---

### Post by lakelovers on 2006-06-05
I have no idea what I did differently, but I just got a successful Dapper upgrade. What a relief!! I did get one error but it doesn't seem to effect the operation. The error: Could not load /con/con:000-write not found. Also, when I open the desktop I get a note that an icon cannot be found. Apparently, neither of these are critical, or I'll find out down the line. Any ideas?

**Edit**
I just installed Openoffice Writer and got this error
"E: backuppc: subprocess post-installation script returned error exit status 1"
What does this mean and how can I fix it?

---

