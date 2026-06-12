---
title: "dpkg: unrecoverable fatal error problem"
date: 2014-03-29
forum: Installation &amp; Upgrades
---

### Post by darrendxcv23 on 2014-03-29
i get an error when installing or removing something

sudo apt-get install wine1.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libclutter-gst-1.0-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libosmesa6 wine-gecko2.24 wine-mono4.5.2 wine1.7-i386
Suggested packages:
  dosbox
Recommended packages:
  wine1.5-i386
The following packages will be REMOVED:
  wine1.2 wine1.4 wine1.4-common wine1.4-i386
The following NEW packages will be installed:
  libosmesa6 wine-gecko2.24 wine-mono4.5.2 wine1.7 wine1.7-i386
0 upgraded, 5 newly installed, 4 to remove and 86 not upgraded.
Need to get 0 B/104 MB of archives.
After this operation, 114 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 files list file for package `nitrux-icon-theme' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

need some help

nevermind fixed already.

---

### Post by MrBrandon on 2014-03-29
> **darrendxcv23 said:**
> i get an error when installing or removing something
nevermind fixed already.

Don't do this for christs sake. Tell us what you did to solve the issue. I'm having the same problem and when searching and I find someone with the same issue only to find "fixed it! haha!" and no solution it drives me mad.

---

### Post by devil2099 on 2014-03-29
[FONT=system][COLOR=#333333]If you're having problems updating in Ubuntu do this:
[/COLOR]
[COLOR=#333333]Remove the file [FONT=palatino linotype]nitrux-icon-theme.list [/FONT]in [FONT=palatino linotype]/var/lib/dpkg/info/[/FONT], and update your package cache. [/COLOR][COLOR=#000000]The packages have been fixed so remove that file, remove the package (use apt-get purge), update the package cache and re-install.[/COLOR][/FONT]

---

### Post by MrBrandon on 2014-03-29
That did it, thank you.

---

