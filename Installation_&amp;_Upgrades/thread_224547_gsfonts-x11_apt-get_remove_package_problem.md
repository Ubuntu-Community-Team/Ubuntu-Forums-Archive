---
title: "gsfonts-x11 apt-get remove package problem"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by burwaco on 2006-07-28
Hello everyone,

I try to do apt-get update && apt-get upgrade, but someting goes wrong with the gsfonts-x11 package. When I try to remove it manually is says:

```

burwaco@devbox:~$ sudo apt-get remove gsfonts-x11
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gsfonts-x11
0 upgraded, 0 newly installed, 1 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 119kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 77886 files and directories currently installed.)
Removing gsfonts-x11 ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: error processing gsfonts-x11 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 gsfonts-x11
E: Sub-process /usr/bin/dpkg returned an error code (1)
burwaco@devbox:~$

```

Any ideas anyone ?

Also, here at work I'm behind a proxy, and I couldn't figure out how to configure apt-get with the proxy, so I downloaded the gsfonts-x11_0.20_all.deb package and installed it that way, but got an error then. And now it won't uninstall at all...


*edit*

And this stupid gsfonts-x11 package interfears with everything, I can't install/upgrade anything no more...

```

burwaco@devbox:~$ sudo apt-get install freecraft
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  fcmp
Suggested packages:
  crafted
The following packages will be REMOVED:
  gsfonts-x11
The following NEW packages will be installed:
  fcmp freecraft
0 upgraded, 2 newly installed, 1 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 9053kB of archives.
After unpacking 15.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com dapper/universe fcmp 1.18.20030311-2 [8373kB]
Get:2 http://au.archive.ubuntu.com dapper/universe freecraft 1:1.18-2.2 [680kB]
Fetched 9053kB in 5m42s (26.5kB/s)
(Reading database ... 77886 files and directories currently installed.)
Removing gsfonts-x11 ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: error processing gsfonts-x11 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 gsfonts-x11
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

A solution, please !

---

### Post by mrcsparker on 2006-07-31
Install the new xfonts-utils.  It will fix your problems.

---

### Post by burwaco on 2006-08-01
Doesn't help either...

```

burwaco@devbox:~$ sudo apt-get install xfonts-utils
Password:
Reading package lists... Done
Building dependency tree... Done
xfonts-utils is already the newest version.
The following packages will be REMOVED:
  gsfonts-x11
0 upgraded, 0 newly installed, 1 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 119kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 77886 files and directories currently installed.)
Removing gsfonts-x11 ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exitdpkg: error processing gsfonts-x11 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 gsfonts-x11
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by burwaco on 2006-08-01
Ok, it looks like I found a solution.

After trying all dpkg --force options, nothing worked, so I wanted to know where apt read the fact that it had to remove gsfonts-x11.

I found this file: /var/lib/dpkg/status witch contains info on all the packages installed on your system. (it appears so)

so...

```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup 

```

I edited the file as root and scrolled to this section...

```

Package: gsfonts-x11
Status: deinstall ok half-installed
Priority: optional
Section: x11
Installed-Size: 116
Maintainer: Roland Rosenfeld <roland@debian.org>
Architecture: all
Version: 0.20
Depends: gsfonts (>= 6.0-2), xutils (>= 4.1.0-12), xfonts-utils
Conflicts: gsfonts (<< 6.0-2)
Conffiles:
 /etc/X11/fonts/Type1/gsfonts-x11.scale 99c6fce657cf452619a6ffb708ae4b3c
 /etc/X11/fonts/Type1/gsfonts-x11.alias f61d8b707eb67bf5b6d0aaa9f1906208
Description: Make Ghostscript fonts available to X11
 This packages makes the 35 Postscript fonts from the gsfonts package
 available to your X server under their "urw" names and via
 fonts.alias with the official "adobe" names, too.
 .
 This package does not contain any fonts itself but allows to reuse
 the ghostscript fonts as X11 screen fonts.

```

and commented it out. apt didn't like tjhat very much, so I removed the above code completely from the file. apt didn't mind about remioving packages no more !

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gsfonts-x11

```

System upgraded, apt is happy, I'm happy.

---

### Post by hotani on 2006-10-04
so close, yet.... It didn't work. I'm still stuck with a gdm-less system and a very botched edgy upgrade. 

If I could go back - no, I wouldn't try it again. Dapper was working so well. :(

---

### Post by elfgoh on 2006-10-28
> **hotani said:**
> so close, yet.... It didn't work. I'm still stuck with a gdm-less system and a very botched edgy upgrade. 

If I could go back - no, I wouldn't try it again. Dapper was working so well. :(

Hi, this should be a more elegant solution from [http://ubuntuforums.org/showthread.php?t=213711](http://ubuntuforums.org/showthread.php?t=213711)

Just change 

**update-fonts-dir --x11r7-layout misc**

to 

**update-fonts-dir misc**

Then reinstall the package

HTH

---

### Post by hotani on 2006-10-28
Thanks, but I ended up doing a clean install on that system. All is working fine now.

---

