---
title: "Anyone Successfully Installed 18.04/Mint 19 From a New ISO in the Last Day Or So?"
date: 2018-07-10
forum: Installation &amp; Upgrades
---

### Post by lostmoonofsaturn on 2018-07-10
Repeated installs of multiple 18.04 flavors here have all failed, with the initial post-install reboot going to the grub command line. Ditto Linux Mint 19 installs.

This is on hardware that sees frequent and routine Ubuntu installs.

What the installs have in common is the selection of the "Download updates during install" option and ISO images downloaded from releases.ubuntu.com, or Mint's mirrors, in the last 24 hours or so.

I notice a batch of posts here about what seems the same problem on new installs, while several see it after updating an existing install.  Googling turns up more.

Fedora 28 installs per normal so it doesn't seem to be a hardware issue.

---

### Post by powerjas on 2018-07-10
I have but had to turn off network cards during the install, other wise same result as you it installs but stop at the grub prompt.

---

### Post by lostmoonofsaturn on 2018-07-10
Thanks, @powerjas.  That worked.  Unplugged the ethernet cable, installed, rebooted successfully, plugged in the ethernet cable, updated, rebooted, and all is well.

Sure seems like an issue with the current install image.

---

### Post by jeremy31 on 2018-07-10
I heard a complaint from a Mint user, I think he said the issue was with an update to ubiquity, I will need to search for the comment when I get home.
Changelog shows ```
ubiquity (18.04.14.3) bionic; urgency=medium

  * Automatic update of included source packages: grub-installer
    1.128ubuntu8.18.04.1, partman-auto 134ubuntu8.1, partman-efi
    71ubuntu2.1. (LP: #1766945, LP: #1778848)

 -- Åukasz 'sil2100' Zemczak <lukasz.zemczak@ubuntu.com>  Fri, 29 Jun 2018 09:47:18 +0200
```

---

### Post by missmoondog on 2018-07-10
weird issue there, for sure, and an equally weird solution.

have installed several copies of various buntu's and 1 mint in last few days and haven't had any issues. would've never thought about disconnecting ethernet.

please mark topic as solved and thanks :)

---

### Post by oldfred on 2018-07-10
It may be an update to UEFI version of grub. And disconnecting prevents the update.

Multiple installs show /EFI/grub (Debian & others may use it, so standard grub)which with an Ubuntu install should not exist. It should be /EFI/ubuntu. And part of grub's code internally has always looked for grub.cfg in EFI/ubuntu. That grub is a 3 line configfile to find full install. 

Seems like multiple users with 18.04 are seeing this, or maybe they rolled out update to grub, but fix was only in 18.10?
       Ubuntu 18.10 Cosmic installed /EFI/grub
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743)

---

