---
title: "Software center not connecting"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by qzpac on 2013-09-28
I am using Ubuntu 11.04. I can't install chinese chess software from the Ubuntu Software Center or from terminal. I am getting errors such as: **Requires installation of untrusted packages: The action would  require the installation of packages from not authenticated sources. **Any install that I'm trying through the Software Center is telling me the error text in bold.

[h=2]Additional information:[/h]  Here's a paste from apt-get update:

Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B725097B3ACC3965
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>i try to use sudo apt-get update from terminal but nothing to donwload or update.  Any advise how to install chinese chess in ubuntu 11.04?

---

### Post by ibjsb4 on 2013-09-28
11.04 is no longer supported, you need install 12.04

---

### Post by whitesmith on 2013-09-28
See [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) for an explanation of what you need to do when an Ubuntu release reaches EOL.

---

### Post by qzpac on 2013-09-28
I just want to install chinese chess in ubuntu 11.04 without upgrading.  Is this possible? Not to take out space/memory.  Do you know of any free chinese chess for ubuntu 11.04?

---

### Post by grahammechanical on 2013-09-28
The software sources or repositories for 11.04 have been closed but they still exist somewhere else. You have to edit your sources lists to point to this different location for the old 11.04 repositories. This link will explain what to do.

[http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html](http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html)

Regards.

---

