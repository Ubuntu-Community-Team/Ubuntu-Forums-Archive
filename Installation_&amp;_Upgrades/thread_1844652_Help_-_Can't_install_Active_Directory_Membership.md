---
title: "Help - Can't install Active Directory Membership"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by jimerman on 2011-09-15
I have a computer I upgraded from Ubuntu 10.10 to 11.04.  At 10.10 everything was working great - I installed Likewise Open, joined it to my Windows Domain, great.  I upgraded it to 11.04.  Everything seemed to work fine.

Today, I noticed that "Active Directory Membership" is no longer on the System / Administration menu.  It doesn't show up under installed software on the Software Center.  I do see likewise support libraries in the installed software portion.

So, because I was having some trouble with machine accounts, I want to delete and add it back.  I thought I would just get it via Software Center, but it errors out on the install saying I need to remove Likewise Open not supported by Ubuntu.

If I do it from a terminal window, here is what I get:

///
...
Unpacking likewise-open (from .../likewise-open_6.0.0.53010-4ubuntu5.1_i386.deb) ...
Error: found /opt/likewise/data/VERSION

Please remove versions of Likewise Open and Likewise Enterprise not supported by Ubuntu before installing this package.

dpkg: error processing /var/cache/apt/archives/likewise-open_6.0.0.53010-4ubuntu5.1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 101
Errors were encountered while processing:
 /var/cache/apt/archives/likewise-open_6.0.0.53010-4ubuntu5.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

