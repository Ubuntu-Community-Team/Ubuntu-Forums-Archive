---
title: "stop apt-get from trying to install a package"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by eisublime on 2008-07-24
I'm trying to upgrade my 6.06 LTS server install of Ubuntu to the new shiny 8.04 LTS version, however it tries to upgrade samba during the process and fails.  If i try sudo apt-get install -f I get 
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  samba
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
74 not fully installed or removed.
Need to get 0B/3404kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 58125 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.3 (using .../samba_3.0.22-1ubuntu3.8_amd64.deb) ...
Unpacking replacement samba ...
/var/lib/dpkg/info/samba.postrm: line 22: update-inetd: command not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 22: update-inetd: command not found
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.8_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 22: update-inetd: command not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

If I try sudo apt-get install update-inetd I get 
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package update-inetd

When I looked at the available packages for Dapper, it looks like update-inetd isn't one of them, so I need to do one of two things I guess.  Either get update-inetd installed somehow (which I can't figure out how to do) or get apt-get to stop trying to upgrade samba.  Can anyone help me figure out how to do either of those things?

Thanks

---

### Post by jtniehof on 2008-07-24
You may be able to sidestep the issue by uninstalling samba, doing the upgrade, and then reinstalling samba. Double-check your config files after doing so, though.

---

### Post by eisublime on 2008-07-24
I've been considering trying that, I'd prefer to not have to though obviously.  There's no way actually address the issue though?  I even downloaded the source for update-inetd but there's no configure script, so I'm not sure how to install it.

---

### Post by jtniehof on 2008-07-24
> **eisublime said:**
> There's no way actually address the issue though?
[Pinning]("https://help.ubuntu.com/community/PinningHowto") is the preferred way to keep one particular package from upgrading. It can be a big ugly complicated mess, however, 

I find it very odd that the old postrm script (that is, the script from 6.06) tries to call something that doesn't exist (a package search for update-inetd on Dapper pulls up nothing.)

I presume you've grabbed the source tarball of update-inetd. The actual program you need is a Perl script, so it doesn't need to be compiled. You can untar the download, move update-inetd to /usr/sbin, and make it executable (chmod ugo+x update-inetd.) Then try upgrading samba again...and axe the update-inetd script right after that. (Anything that needs it should install it in the course of the upgrade.) No warranty, YMMV, etc. :) but good luck.

---

### Post by eisublime on 2008-07-25
Interesting, thanks for explaining update-inetd, I was definitely confused about why I couldn't compile it - that explains it.

---

