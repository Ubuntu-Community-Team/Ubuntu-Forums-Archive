---
title: "Cannot install/upgrade/uninstall MythTV on Dapper"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by OmahaVike on 2007-10-15
Have MythTV completely installed -- for about a half year.  Worked great!

Something has gone amiss with Myth, so now trying to uninstall it completely and start from scratch.  Apt will no longer function, because it's trying to upgrade the broken package.

The results of apt-get install -f:
```

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  mythtv-backend
Suggested packages:
  mythtv-debug
The following packages will be upgraded:
  mythtv-backend
1 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
1 not fully installed or removed.
Need to get 0B/815kB of archives.
After unpacking 119kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mythtv-backend.
(Reading database ... 110633 files and directories currently installed.)
Preparing to replace mythtv-backend 0.20-0.2ubuntu2~dapper1 (using .../mythtv-backend_0.20.2-0ubuntu0.6.10.1~dapper1_i386.deb) ...
Stopping MythTV server: mythbackend invoke-rc.d: initscript mythtv-backend, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping MythTV server: mythbackend invoke-rc.d: initscript mythtv-backend, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mythtv-backend_0.20.2-0ubuntu0.6.10.1~dapper1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting MythTV server: mythbackendmythbackend: error while loading shared libraries: libmythtv-0.20.so.0: cannot open shared object file: No such file or directory
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/mythtv-backend_0.20.2-0ubuntu0.6.10.1~dapper1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm not interested in keeping any of the config files for Myth intact, I simply want it all gone and (more importantly) apt working again.

ANY and all assistance is greatly appreciated.

Thanks!

---

### Post by OmahaVike on 2007-10-15
[SOLVED]

Found a solution here:  [http://blog.var.cc/blog/archive/2004/02/]("http://blog.var.cc/blog/archive/2004/02/")

Essentially, my mythtv-backend was hosed.  dselect wouldn't even get me out of it.

1)  Edit:  /var/lib/dpkg/info/[packagename].prerm
2)  change top two lines:
```

#!/bin/sh
set -e

```
to
```

#!/bin/sh
set -e
exit 0 

```
3)  dpkg --force-all -r [packagename]
4)  just to be sure...    apt-get install -f 

voila!  Hope this helps *somebody* out there.

---

