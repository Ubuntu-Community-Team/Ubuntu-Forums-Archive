---
title: "kubuntu upgrade to edgy from dapper, xqbiff issue"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by tritesnikov on 2007-04-02
Hi all,

I'm trying to upgrade my kubuntu install to edgy from dapper following the instructions on this page

[http://kubuntu.org/announcements/6.10-release.php](http://kubuntu.org/announcements/6.10-release.php)

I had an initial prompt that made me move everything out of /usr/X11R6/bin, which consisted of w9wm and xqbiff. The prompt told me to move these out and then restart the upgrade. So I did.


However, when I run 'sudo apt-get -f dist-upgrade', the operative error message in the crapload of output seems to be:

Unpacking replacement x11-common ...
Replacing files in old package xinit ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6.2_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package xqbiff


and then at the end I get

Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


after which I get a prompt back.

I have tried to remove xqbiff through 'apt-get remove xqbiff', 'apt-get -f remove xqbiff' and have also tried other things to no avail.

Anyone have any suggestions?

---

### Post by tritesnikov on 2007-04-02
Well, I'm stupid. A little 'dpkg -r' action was all I needed.

---

