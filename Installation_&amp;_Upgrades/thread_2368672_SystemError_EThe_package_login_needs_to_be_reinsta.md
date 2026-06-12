---
title: "SystemError: E:The package login needs to be reinstalled, but I can't find an archive"
date: 2017-08-13
forum: Installation &amp; Upgrades
---

### Post by emlvz88 on 2017-08-13
I've been lurking everywhere to find a solution to this problem, but I just can't find a solution. please help.

If unfixable is there a way to at leat not see the error?

---

### Post by vocx on 2017-08-13
> **emlvz88 said:**
> I've been lurking everywhere to find a solution to this problem, but I just can't find a solution. please help.

If unfixable is there a way to at leat not see the error?
Your problem is very vague. You need to provide more information.

What did you install or what were you trying to do to cause this error message to appear? You won't get a simple solution just by posting a quick error message like that.
```

apt show login

```

```

Package: login
Version: 1:4.2-3.1ubuntu5.3
Priority: required
Essential: yes
Section: admin
Source: shadow
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Shadow package maintainers <pkg-shadow-devel@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,221 kB
Pre-Depends: libaudit1 (>= 1:2.2.1), libc6 (>= 2.14), libpam0g (>= 0.99.7.1), libpam-runtime, libpam-modules (>= 1.1.8-1)
Conflicts: amavisd-new (<< 2.3.3-8), backupninja (<< 0.9.3-5), echolot (<< 2.1.8-4), gnunet (<< 0.7.0c-2), python-4suite (<< 0.99cvs20060405-1)
Replaces: manpages-de (<< 0.5-3), manpages-tr (<< 1.0.5), manpages-zh (<< 1.5.1-1)
Homepage: http://pkg-shadow.alioth.debian.org/
Task: minimal
Supported: 5y
Download-Size: 304 kB
APT-Manual-Installed: yes
APT-Sources: http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Description: system login tools
 These tools are required to be able to login and use your system. The
 login program invokes your user shell and enables command execution. The
 newgrp program is used to change your effective group ID (useful for
 workgroup type situations). The su program allows changing your effective
 user ID (useful being able to execute commands as another user).

```

It seems the "login" program is a critical part of the system, and you somehow broke it :/

> 
If unfixable is there a way to at leat not see the error?
Lol. Don't just try to hide an error. Instead, try to actually solve it. Please provide more information about your computer, and what you were trying to do.

---

### Post by emlvz88 on 2017-08-13
I executed

     sido apt-get update
     sudo apt-get updrage
     sudo apt-get install

but the process got interrupted by accident

then tried running 

     sudo dpkg &#8211;configure -a
     sudo rm /var/lib/dpkg/info/*.postrm
     sudo rm /var/lib/dpkg/info/*.list
     sudo apt-get clean all
     sudo apt-get update
     sudo apt-get upgrade

---

### Post by emlvz88 on 2017-08-13
Package: login
Essential: yes
Status: install reinstreq unpacked
Priority: required
Section: admin
Installed-Size: 1,196 kB
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Source: shadow
Version: 1:4.1.5.1-1ubuntu9.5
Config-Version: 1:4.1.5.1-1ubuntu9
Replaces: manpages-de (<< 0.5-3), manpages-tr (<< 1.0.5), manpages-zh (<< 1.5.1-1)
Pre-Depends: libaudit1 (>= 1:2.2.1), libc6 (>= 2.7), libpam0g (>= 0.99.7.1), libpam-runtime, libpam-modules
Conflicts: amavisd-new (<< 2.3.3-8), backupninja (<< 0.9.3-5), echolot (<< 2.1.8-4), gnunet (<< 0.7.0c-2), python-4suite (<< 0.99cvs20060405-1)
Homepage: 
Original-Maintainer: Shadow package maintainers <pkg-shadow-devel@lists.alioth.debian.org>
Download-Size: unknown
APT-Manual-Installed: yes
APT-Sources: /var/lib/dpkg/status
Description: system login tools
 These tools are required to be able to login and use your system. The
 login program invokes your user shell and enables command execution. The
 newgrp program is used to change your effective group ID (useful for
 workgroup type situations). The su program allows changing your effective
 user ID (useful being able to execute commands as another user).

---

### Post by vocx on 2017-08-13
> **emlvz88 said:**
> I executed

     sido apt-get update
     sudo apt-get updrage
     sudo apt-get install

but the process got interrupted by accident

then tried running 

     sudo dpkg &#8211;configure -a
     sudo rm /var/lib/dpkg/info/*.postrm
     sudo rm /var/lib/dpkg/info/*.list
     sudo apt-get clean all
     sudo apt-get update
     sudo apt-get upgrade

So did you try reinstalling?
```

sudo apt install --reinstall login

```

---

### Post by emlvz88 on 2017-08-13
Yes I did, but i keep getting the same error

---

### Post by vocx on 2017-08-13
> **emlvz88 said:**
> Yes I did, but i keep getting the same error
What error? You have not posted fully the error.

---

