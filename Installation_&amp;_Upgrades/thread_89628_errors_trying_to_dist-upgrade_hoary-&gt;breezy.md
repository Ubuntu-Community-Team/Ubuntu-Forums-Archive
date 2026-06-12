---
title: "errors trying to dist-upgrade hoary-&gt;breezy"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by Zed on 2005-11-13
Following the [instructions on the wiki](https://wiki.ubuntu.com/BreezyUpgradeNotes), I updated my sources.list (exactly as the wiki page has it), did an apt-get update and apt-get dist-upgrade. The dist-upgrade reported an error after running a long time. I tried again, hoping something had just downloaded incorrectly. It reported

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnucash: Depends: libofx2 but it is not installed
  libgl1-mesa-dri: Depends: libgl1-mesa (= 6.3.2-0ubuntu6breezy1) but it is not installed
  nautilus: Depends: nautilus-data (>= 2.12.1-0ubuntu1.1) but 2.10.0-0ubuntu9 is installed
  ubuntu-desktop: Depends: libesd-alsa0 but it is not installed
                  Depends: libgl1-mesa but it is not installed
  x-window-system-core: Depends: libgl1-mesa but it is not installed
E: Unmet dependencies. Try using -f.

Following its advice and trying apt-get -f dist-upgrade, I get:

Unpacking libofx2 (from .../libofx2_1%3a0.8.0-3ubuntu8_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb (--unpack):
 trying to overwrite `/usr/share/libofx/dtd/opensp.dcl', which is also in package libofx0c102
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone have any suggestions how to proceed?

Thanks.

---

### Post by heimo on 2005-11-13
disclaimer: This may make the things even worse (or hopefully: solve the problems). 

I would try:

```
sudo mv /var/lib/dpkg/info/libofx2.* /tmp/
sudo apt-get --purge remove libofx2 (ONLY if it doesn't remove tons of other stuff)
sudo apt-get install libofx2
sudo apt-get install -f
sudo dpkg --configure -a

```

---

### Post by Zed on 2005-11-13
Thanks, but no go.

libofx2 isn't installed. I tried removing libofx0c102, but it won't let me do apt-get --purge remove or apt-get remove -- I get the same error I reported for apt-get dist-upgrade. "... E: Unmet dependencies. Try using -f."

---

