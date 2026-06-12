---
title: "Edgy -&gt; Feisty upgrade woes"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by belgrave on 2007-04-22
Hi,

been trying since release to get my Edgy (AMD64) system upgraded. Here's what's been happening:
[LIST=1]
[*]Tried the standard upgrade through the update manager... this results in: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
[*]Late Friday night, an update for the update manager came through. I thought this might have been to fix problems, so I installed it. Since then, update manager no longer gives me the distro upgrade option. (using command line to force gives same bzip errors as above)
[*]Downloaded the alternate ISO, burned it and tried upgrading from that. Network upgrade gives same errors as above, non network upgrade give MD5 checksum errors on a whole heap of stuff.
[/LIST]

any help is desperately appreciated - I'm currently trying an upgrade from the ISO mounted on looback, just in case the burn was bad.

---

### Post by belgrave on 2007-04-22
mounted iso upgrade seems to be progressing well, except for:

2007-04-22 06:57:23,312 ERROR got an error from dpkg for pkg: '/media/iso//pool/main/x/xorg/x11-common_7.2-0ubuntu11_amd64.deb': 'conflicting packages - not installing x11-common

hmmmm.... any help on that one is appreciated as well

---

