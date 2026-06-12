---
title: "Busted system -- libofx2"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by dudinatrix on 2005-10-16
I tried upgrading through Synaptec, and eventually got to an error:
 
Unpacking libofx2 (from .../libofx2_1%3a0.8.0-3ubuntu8_i386.deb) ...
dpkg: error  processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb (--unpack):
 trying to overwrite '/usr/share/libofx/dtd/opensp.dcl', which is also packaged in libofx0c102
 
I can't do anything, everything I try results in this error now.  What can I do?
 
As a last resort, how do I go about reformatting with a clean Breezy installation, while maintaining my dual boot with Windows XP?  I already have a backup, I just don't know how to maintain my partitions and all that.

---

### Post by John Jason Jordan on 2005-10-16
[QUOTE=dudinatrix]I tried upgrading through Synaptec, and eventually got to an error:
 
Unpacking libofx2 (from .../libofx2_1%3a0.8.0-3ubuntu8_i386.deb) ...
dpkg: error  processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb (--unpack):
 trying to overwrite '/usr/share/libofx/dtd/opensp.dcl', which is also packaged in libofx0c102
 
I can't do anything, everything I try results in this error now.  What can I do?[/QUOTE]

I've had the same problem. Eventually I eliminated the problem by using Settings > Filters and checking the box for Broken. Even then you have to hit Delete first before you do OK. (Not the clearest user interface.) Until you finally excise it you won't be able to do a lot of installing/uninstalling. That's because Synaptic is a bit brain dead when you have multiple items to install or uninstall. It continues until it gets to the first problem, then aborts, leaving the remaining changes marked, but unperformed. Thus, the Apply button remains active, yet clicking on it just repeats the error process.

But after installing/uninstalling more things, the problem comes back. I have no idea what libofx2 does, but a pox on its clan. As far as I can tell it is not required for any program I have installed.

---

### Post by emmet on 2005-10-17
I had exactly the same problem.

I traced it back to the upgrade of GnuCash. My solution was actually to uninstall the old library (along with GnuCash) and then continue with the upgrade.

Not the most elegant method, but it worked in the end. A little scary when it happens though....

Cheers

Emmet

---

### Post by John Jason Jordan on 2005-10-18
[QUOTE=emmet]I had exactly the same problem.

I traced it back to the upgrade of GnuCash. My solution was actually to uninstall the old library (along with GnuCash) and then continue with the upgrade.

I later discovered the same thing. It was GnuCash. I just uninstalled GnuCash and the problem went away. After finishing the upgrade I reinstalled GnuCash. Luckily the reinstallation had no problem finding my data files. All is back to normal. Well, except for wifi, which Breezy broke and I still haven't got working again. :(

---

