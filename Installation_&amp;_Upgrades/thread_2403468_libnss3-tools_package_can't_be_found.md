---
title: "libnss3-tools package can't be found"
date: 2018-10-11
forum: Installation &amp; Upgrades
---

### Post by dwalker-8 on 2018-10-11
I'm running Ubuntu 18,04. So I need the certutil command on my system for a custom package we have made.  On .deb systems the package that provides this tool is called libnss3-tools.  However, when I tried to install this package it comes up with the following error:

$ sudo apt-get install libnss3-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libnss3-tools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


I thought maybe the package name has changed so when I tried to run the certutil list command I get the following error telling me indeed, that the libnss3-tools package needs to be installed to use this command:

$ certutil -L -d sql:$HOME/.pki/nssdb

Command 'certutil' not found, but can be installed with:

sudo apt install libnss3-tools

Is this package found in another repo?  Ubuntu18 uses the beaver repos so I tried adding xenial to /etc/apt/sources.list and that doesn't make the package available either.  Strangely, this isn't an issue on debian 9.

---

### Post by oldos2er on 2018-10-13
It's in the universe repository:  [https://packages.ubuntu.com/search?keywords=libnss3-tools&searchon=names&suite=bionic&section=all](https://packages.ubuntu.com/search?keywords=libnss3-tools&searchon=names&suite=bionic&section=all)
Do you have universe enabled? Have you run *sudo apt update* recently?

You should remove xenial from your sources.list, mixing different versions' repositories is a bad idea.

---

### Post by dwalker-8 on 2018-10-17
Thank you so much.  That was the issue.  For some reason, unfortunately, Ubuntu doesn't include these repositories by default.

---

### Post by oldos2er on 2018-10-17
Universe is enabled by default, unless you're running Ubuntu Server, at least as far as I know. Anyway, I'm glad you fixed it. Could you please mark the thread "Solved' under Thread Tools at the top of the page? Thanks.

---

