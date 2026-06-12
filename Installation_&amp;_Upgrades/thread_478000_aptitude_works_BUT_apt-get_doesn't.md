---
title: "aptitude works BUT apt-get doesn't"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2007-06-18
I was trying to install libdvdcss using these instructions:

sudo su -c 'echo deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free >> /etc/apt/sources.list'
sudo su -c 'echo deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free >> /etc/apt/sources.list'
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install libdvdcss2 w32codecs gstreamer0.10-pitfdll
echo "done"

BUT the sudo apt-get update fails with this:

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
  404 Not Found [IP: 81.169.138.125 80]
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
  404 Not Found [IP: 81.169.138.125 80]
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
  404 Not Found [IP: 81.169.138.125 80]
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
  404 Not Found [IP: 81.169.138.125 80]
Fetched 3B in 1s (2B/s)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  404 Not Found [IP: 81.169.138.125 80]
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  404 Not Found [IP: 81.169.138.125 80]
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  404 Not Found [IP: 81.169.138.125 80]
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  404 Not Found [IP: 81.169.138.125 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

AND WHEN I RUN sudo aptitude update, it works. Then the same for when I use apt-get to install the packages, it fails with this:

The following NEW packages will be installed:
  libdvdcss2 w32codecs
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 14.3MB of archives.
After unpacking 34.5MB of additional disk space will be used.
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free libdvdcss2 1.2.9-2medibuntu2+build1
  404 Not Found [IP: 81.169.138.125 80]
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free w32codecs 20061022-0medibuntu1+build1
  404 Not Found [IP: 81.169.138.125 80]
Failed to fetch [http://medibuntu.sos-sts.com/repo/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb)  404 Not Found [IP: 81.169.138.125 80]
Failed to fetch [http://medibuntu.sos-sts.com/repo/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1+build1_i386.deb)  404 Not Found [IP: 81.169.138.125 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

BUT when I use aptitude install, it works. Can anyone explain this???

---

