---
title: "Upgrade 8.04 to 8.10 - apt error, trying to overwrite file in another package..."
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by balleyne on 2008-11-06
I've been having a ton of problems upgrading from 8.04 to 8.10 on one of my machines. I had to stop and resume the process several times for various reasons. I'm *almost* there, but I still have about 100 updates pending, but the upgrade process keeps failing because there's an unmet dependency. apt tells me to run 'apt-get -f install' to fix it, but I keep getting the same error. Output below.

Help please?


```
balleyne@library-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libopencdk10-dev ispell ibritish libmtp7
  linux-ubuntu-modules-2.6.24-18-generic eclipse-sdk g++-4.2 libopenexr2ldbl
  libcamel1.2-11 libtotem-plparser10 libgtkhtml3.16-cil libsmbios1 libxosd2
  cryptsetup libemail-date-perl libx264-57 libvlc0 libemail-simple-perl
  libtime-piece-perl dhcdbd libwpd-stream8c2a libhunspell-1.1-0 bluez-audio
  libkonq4 libemail-abstract-perl libdbus-qt-1-1c2 libkarma0
  libstdc++6-4.2-dev libmime-perl libmime-lite-perl libedataserver1.2-9
  libmodule-pluggable-perl libgucharmap6 vlc-plugin-pulse
  linux-restricted-modules-2.6.20-16-generic iamerican
  linux-image-2.6.20-16-generic libntfs-3g23
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-firmware
The following NEW packages will be installed:
  linux-firmware
0 upgraded, 1 newly installed, 0 to remove and 127 not upgraded.
2 not fully installed or removed.
Need to get 0B/3365kB of archives.
After this operation, 7397kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 224444 files and directories currently installed.)
Unpacking linux-firmware (from .../linux-firmware_1.2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-firmware_1.2_all.deb (--unpack):
 trying to overwrite `/lib/firmware/v4l-cx2341x-dec.fw', which is also in package ivtv-firmware
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-firmware_1.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by balleyne on 2008-11-12
Anyone?

---

### Post by port801 on 2009-11-01
I'm seeing this same issue now in an upgrade from 9.04 to 9.10. I just did an upgrade using the "alternate" CD and now I'm getting this all over the place. 

I wonder if it could be related to this:

[https://bugs.launchpad.net/ubuntu/+source/ltp/+bug/92944](https://bugs.launchpad.net/ubuntu/+source/ltp/+bug/92944)

Which was supposedly fixed.

---

