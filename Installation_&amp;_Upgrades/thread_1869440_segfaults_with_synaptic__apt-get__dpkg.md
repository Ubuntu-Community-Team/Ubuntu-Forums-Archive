---
title: "segfaults with synaptic / apt-get / dpkg"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by MoM_ on 2011-10-25
Hello,

lately, possibly after some broken update with synaptic, i do receive segmentation faults whenever installing or upgrading anything with synaptic or apt-get.
the segfaults seem to originate from dpkg --configure.

the following shows a possible set of calls:
```

mom@Harmony:~> sudo apt-get update
[..]
Reading package lists... Done
mom@Harmony:~> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  acpid libpam-modules libpam-modules-bin libpam-runtime libpam0g libsyncdaemon-1.0-1 linux-libc-dev opera
  python-ubuntuone-client software-center ubuntuone-client ubuntuone-client-gnome unity unity-common
  update-manager update-manager-core whois
17 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0 B/17,8 MB of archives.
After this operation, 63,5 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Segmentation fault
Setting up tzdata (2011l-0ubuntu0.11.04) ...
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script was killed by signal (Segmentation fault)
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
mom@Harmony:~> sudo apt-get -f install tzdata
Reading package lists... Done
Building dependency tree
Reading state information... Done
tzdata is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev ttf-dejavu-extra libpthread-stubs0 python-newt x11proto-kb-dev xtrans-dev
  x11proto-input-dev libgif4 libxt-dev libxau-dev ca-certificates-java libx11-dev libxcb1-dev
  x11proto-core-dev libxdmcp-dev libpthread-stubs0-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Segmentation fault
Setting up tzdata (2011l-0ubuntu0.11.04) ...
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script was killed by signal (Segmentation fault)
Setting up man-db (2.5.9-4) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script was killed by signal (Segmentation fault)
Errors were encountered while processing:
 tzdata
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
mom@Harmony:~> sudo dpkg --configure tzdata
Setting up tzdata (2011l-0ubuntu0.11.04) ...
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script was killed by signal (Segmentation fault)
Errors were encountered while processing:
 tzdata

```

I am using Ubuntu 11.04 natty x64.
I would be really glad if anyone could help me solving my problem.

thanks in advance
MoM

---

### Post by raja.genupula on 2011-10-26
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade


do them one by one.
all the best.

---

### Post by MoM_ on 2011-10-26
Hello Raja,

thank you for your answer and for helping me.

My problem, unfortunately, is not solved that way.
The result of "apt-get install -f" equals the one without "fix".
As far as I understand, apt-get's fixing option does only fix broken dependencies - in my case already a manual call to "dpkg --configure <anything>" leads to segfaults and so whatever action of apt-get or synaptic leads to segmentation faults.

any further ideas?

thank you
MoM

---

### Post by dino99 on 2011-10-26
try:

sudo apt-get purge tzdata
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

