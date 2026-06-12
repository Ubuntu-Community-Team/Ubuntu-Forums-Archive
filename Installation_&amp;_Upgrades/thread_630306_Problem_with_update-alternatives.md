---
title: "Problem with update-alternatives"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by richcoosa19 on 2007-12-03
Any time I install a package, I now get this horrid error:

Setting up procps (1:3.2.7-3ubuntu5) ...
Use of uninitialized value in length at /usr/sbin/update-alternatives line 733.
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/w for update_mode ()
dpkg: error processing procps (--configure):
 subprocess post-installation script returned error exit status 2

Although it's not always .....alternatives/w  It's always line 733 of /usr/sbin/alternatives though.

Any help would be greatly appreciated!
:confused:

---

### Post by richcoosa19 on 2007-12-03
::Bump::

...Remember me...

The problem seems to only be with procps and php5-dev.  I have tried to use:
```
sudo apt-get install --reinstall procps php5-dev
```

But I still get the exact same issue.

```
Setting up procps (1:3.2.7-3ubuntu5) ...
Use of uninitialized value in length at /usr/sbin/update-alternatives line 733.
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/w for update_mode ()
dpkg: error processing procps (--configure):
 subprocess post-installation script returned error exit status 2
Setting up php5-dev (5.2.3-1ubuntu6.1) ...
Use of uninitialized value in length at /usr/sbin/update-alternatives line 733.
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/php-config for update_mode ()
dpkg: error processing php5-dev (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libpcre3-dev (7.4-0ubuntu0.7.10.1) ...
Errors were encountered while processing:
 procps
 php5-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

