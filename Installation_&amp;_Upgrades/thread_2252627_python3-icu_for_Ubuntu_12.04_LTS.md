---
title: "python3-icu for Ubuntu 12.04 LTS"
date: 2014-11-13
forum: Installation &amp; Upgrades
---

### Post by francwalter on 2014-11-13
Hello

I need to install the package python3-icu on my Ubuntu 12.04 LTS server (without any GUI), but don't find any package source.
The sources are only for Ubuntu 14.04, not for 12.04

Can I just use a package source for 14 in my sources.list to install this python3-icu?
Which package source would this be?

Is there a general search for package sources for a particular package?
I found this [ubuntu packages site]("http://packages.ubuntu.com/trusty/python3-icu"), but I dont find the packages source for each package :(

Thankyou

frank

---

### Post by ian-weisser on 2014-11-13
Add a 14.04/14.10 repository to your 12.04 system ONLY if you want to break your system quite horribly.
Don't do it.
Don't do it.
Don't do it.

You can download individual packages from packages.ubuntu.com and try to install them.
You will need to also manually trace, download, and install any relevant dependencies. Not difficult, but perhaps a bit tedious.
Backporting in this manner is not a supported use of Ubuntu packages, and might still break your system. (though it's much more likely to be easily fixable).
You can also manually install the python code from pypi or a tarball instead of a .deb package.

There are advantages and disadvantages to each way of installing the software, and you (the admin) are responsible for knowing how to maintain and uninstall whatever method you choose. In other words, the normal way of doing business when not using package management.

For the Source package, see Launchpad.net: [https://code.launchpad.net/ubuntu/trusty/+source/pyicu](https://code.launchpad.net/ubuntu/trusty/+source/pyicu)

---

### Post by francwalter on 2014-11-13
> **ian-weisser said:**
> Add a 14.04/14.10 repository to your 12.04 system ONLY if you want to break your system quite horribly.
Don't do it...
OK, not at all an option, this is a productive server, no risk to take.
Thanks!

---

