---
title: "Need help errors while upgrading!"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by stealth75711 on 2006-12-04
Preconfiguring packages ...
(Reading database ... 61281 files and directories currently installed.)
Preparing to replace openoffice.org2-calc 1.9.129-0.1ubuntu4 (using .../openoffice.org2-calc_1.9.129-0.1ubuntu4.1_i386.deb) ...
Unpacking replacement openoffice.org2-calc ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org2-calc_1.9.129-0.1ubuntu4.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice2/program/libsc680li.so')
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org2-calc_1.9.129-0.1ubuntu4.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
admin@zamis:~$


# I got the following errors does anyone know whats wrong?

---

### Post by stealth75711 on 2006-12-04
Recommended packages:
  libmudflap0-dev curl libggi-target-x libggi-target libmail-sendmail-perl
  libcompress-zlib-perl libmikmod2
The following NEW packages will be installed:
  aalib1 binutils build-essential debconf-utils debhelper dpkg-dev fakeroot
  g++ g++-4.0 gcc gcc-3.3-base gcc-4.0 gettext html2text intltool-debian jackd
  libc6-dev libdirectfb-0.9-22 libfaad2-0 libggi2 libgii0 libgii0-target-x
  libglib1.2 libgtk1.2 libgtk1.2-common libjack0.80.0-0 liblame0 libmad0
  libpolyp0 libpostproc0 libstdc++5 libstdc++6-4.0-dev libsvga1 libungif4g
  libxvidcore4 linux-kernel-headers make mozilla-mplayer mplayer-386
  po-debconf xmms
0 upgraded, 41 newly installed, 0 to remove and 1 not upgraded.
Need to get 12.9MB/21.7MB of archives.
After unpacking 77.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.



# now it says this unusual abort command when i go to install
packages!

---

### Post by taurus on 2006-12-04
Try to use capital y instead of lower case y!

---

