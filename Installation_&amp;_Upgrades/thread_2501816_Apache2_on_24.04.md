---
title: "Apache2 on 24.04"
date: 2024-10-21
forum: Installation &amp; Upgrades
---

### Post by deck on 2024-10-21
I am upgrading from 22.04 to 24.04.  I purchased a new hard drive to do this on, as my 22.04 installation is somewhat messed up.  I run a personal blog from my Desktop installation.  It is working fine in general.

I booted the 24.04 up and installed Apache2 using the command line.  When I went to copy configuration files from my old instance, I found that instead of there being an /etc/apache2 directory there is now an /etc/httpd directory.  All of the sub directories are different too.  Where is the new directory configuration documented and how does the older directory layout map to the new layout?

---

### Post by TheFu on 2024-10-21
I don't have apache running on 24.04. That release is too new for my production needs.  Maybe in 6 more months, I'll be ready to try some simple servers with 24.04.x.

[https://ubuntu.com/server/docs/how-to-install-apache2](https://ubuntu.com/server/docs/how-to-install-apache2) is what google found.  It says that /etc/apache2/ is still where configuration exists.  A quick google search says that hasn't changed, so if your 24.04 system has apache2 installed and there isn't a /etc/apache2/ directory, something else is wrong already.

Normally, you'll want to research the change log from the older apache version up to and including the changes in the new version in the new Ubuntu release.  With ever major release change, there will be release notes that explain the old syntax and the new syntax needed.  This documentation is normally found at apache.org, but you'll need to know the exact versions installed on your systems.

There's no hurry to move off 22.04 to keep support. It has support until April 2027.

---

### Post by deck on 2024-10-23
Thanks TheFu.  I am moving because I have some issues with 22.04 that would require a bare metal reinstall.  I screwed some things up.

I won't say I was on drugs but I cannot find the partition that I was looking at in the original post.  As far as general things go I am getting the 24.04 upgraded and moving some files over but I am having a slew of issues that I am going to address separately.

This thread can be considered to be closed.

---

