---
title: "Problem upgrading Ubuntu Gnome 14 64 bit can't fetch libx@tr@cker and related files"
date: 2016-03-23
forum: Installation &amp; Upgrades
---

### Post by beautypeakwebdesig on 2016-03-23
I just installed Ubuntu Gnome 14 64 bit and keep having a problem upgrading the following:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa/libxatr@cker2_10.1.3-0ubuntu0.6_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa/libxatr@cker2_10.1.3-0ubuntu0.6_amd64.deb)
  Connection failed [IP: 91.189.92.200 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/tr@cker-utils_0.16.5-0ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/tr@cker-utils_0.16.5-0ubuntu0.1_amd64.deb)
  Connection failed [IP: 91.189.91.23 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/tr@cker-miner-fs_0.16.5-0ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/tr@cker-miner-fs_0.16.5-0ubuntu0.1_amd64.deb)
  Connection failed [IP: 91.189.91.15 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/tr@cker-extract_0.16.5-0ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/tr@cker-extract_0.16.5-0ubuntu0.1_amd64.deb)
  Connection failed [IP: 91.189.91.24 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/tr@cker_0.16.5-0ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/tr@cker_0.16.5-0ubuntu0.1_amd64.deb)
  Connection failed [IP: 91.189.91.13 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/gir1.2-tr@cker-0.16_0.16.5-0ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/gir1.2-tr@cker-0.16_0.16.5-0ubuntu0.1_amd64.deb)
  Connection failed [IP: 91.189.92.200 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/libtr@cker-miner-0.16-0_0.16.5-0ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/libtr@cker-miner-0.16-0_0.16.5-0ubuntu0.1_amd64.deb)
  Connection failed [IP: 91.189.91.23 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/libtr@cker-extract-0.16-0_0.16.5-0ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/libtr@cker-extract-0.16-0_0.16.5-0ubuntu0.1_amd64.deb)
  Connection failed [IP: 91.189.91.15 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/libtr@cker-sparql-0.16-0_0.16.5-0ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tr@cker/libtr@cker-sparql-0.16-0_0.16.5-0ubuntu0.1_amd64.deb)
  Connection failed [IP: 91.189.91.24 80]


This problem has been occurring since yesterday, and happens if I try to upgrade through Synaptic or the terminal using apt-get upgrade. I have tried using both the US and Main Ubuntu repository. As you cn see, it is only files in the /tr@cker/ folder that are not downloading. 


Is there an alternative location to directly download these files? Is anyone else having this problem? Thanks.

---

### Post by beautypeakwebdesig on 2016-03-23
FYI the problem relates to all upgrade files with the term tr a cker in their name, but my ISP is using OpenDNS due to software piracy issues and it is apparently blocking anything with the word tr a cker in it, including posts to this forum. Yes, this is probably the root of the problem, but if someone could point me to someplace I could download the package without tr a cker in the name I would really appreciate it.

---

