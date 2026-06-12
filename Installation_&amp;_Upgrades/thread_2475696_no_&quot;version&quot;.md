---
title: "no &quot;version&quot;"
date: 2022-06-04
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-06-04
I just tried to check the version on a program.  Turns out I don't have the version program.  I looked up how to install version and most of the replies wanted me to update my ubuntu (20.04.4)  so, how do I install "version"?

---

### Post by Bashing-om on 2022-06-04
jgw; Hey

Many times an app will honor the 'v' flag.
as in
> 
 mousepad -v
Mousepad 0.4.2

Copyright (c) 2007
	The Xfce development team. All rights reserved.

Please report bugs to <http://bugzilla.xfce.org/>.
sysop@2004x-c:~$ 

//

sysop@2004x-c:~$ apt list version
Listing... Done
sysop@2004x-c:~$ 

where "version" does not exist in the focal repo.

[INDENT]my bit to try and help
[/INDENT]

---

### Post by jgw on 2022-06-04
Thank you for the reply!

I fear I might be going crazy!  I decided to misuse version.  I wanted to enter "version --program name"  which was crazy and I apologize for having bothered anybody on this one.  Makes no sense and embarrasing but I will survive.

---

### Post by Bashing-om on 2022-06-04
jgw  :D

All good

-that's the way we learn new things-

---

### Post by sudodus on 2022-06-05
An alternative is to use **[FONT=Courier New]apt-cache policy[/FONT]** for the program package, which is often but far from always the same as the program. (Some packages contain several programs, some packages simply have a slightly modified name.)

Example:
```

apt-cache policy fdisk

dpkg -S ddrescue
apt-cache policy gddrescue

```

This method can be useful to find the package:
```

$ dpkg -S $(which mv)
coreutils: /bin/mv

mv --version
# and
apt-cache policy coreutils

```
should give matching results. If they differ, I think **[FONT=Courier New]apt-cache policy[/FONT]** gives a more reliable result. I have seen several examples, where the internal version output is lagging behind, for example the Ubuntu Startup Disk Creator. In 18.04.6 we can find:
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.6 LTS
Release:	18.04
Codename:	bionic

$ usb-creator-gtk --version

(usb-creator-gtk:21170): dbind-WARNING **: 19:24:08.280: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
[COLOR="#cc0000"]**0.3.3**[/COLOR]

$ apt-cache policy usb-creator-gtk 
usb-creator-gtk:
  Installerad: [COLOR="#cc0000"]**0.3.5**[/COLOR]ubuntu18.04.2
  Kandidat:    0.3.5ubuntu18.04.2
  Versionstabell:
 *** 0.3.5ubuntu18.04.2 500
        500 http://se.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.3.5ubuntu18.04.1 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
     0.3.5 500
        500 http://se.archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```

---

