---
title: "Upgrade errors"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by Travelguy on 2015-07-16
Hi , 

I am trying to upgrade my system but I keep getting this error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-3.5.0-51-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/40.7 MB of archives.
After this operation, 123 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 285644 files and directories currently installed.)
Preparing to replace linux-image-3.5.0-51-generic 3.5.0-51.76 (using .../linux-image-3.5.0-51-generic_3.5.0-51.77~precise1_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.5.0-51-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-51-generic_3.5.0-51.77~precise1_amd64.deb (--unpack):
 trying to overwrite '/lib/modules/3.5.0-51-generic/kernel/net/bluetooth/bnep/bnep.ko', which is also in package linux-image-extra-3.5.0-51-generic 3.5.0-51.76
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-51-generic /boot/vmlinuz-3.5.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-51-generic /boot/vmlinuz-3.5.0-51-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.5.0-51-generic...
P: Writing config for /boot/vmlinuz-3.5.0-43-generic...
P: Writing config for /boot/vmlinuz-3.5.0-42-generic...
P: Writing config for /boot/vmlinuz-3.5.0-40-generic...
P: Writing config for /boot/vmlinuz-3.5.0-17-generic...
P: Writing config for Windows 7 (loader) on /dev/sda1...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-51-generic /boot/vmlinuz-3.5.0-51-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.5.0-51-generic_3.5.0-51.77~precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I am not sure how to fix it? Any ideas or please let me know if you need more information.

---

### Post by v3.xx on 2015-07-16
There is no mention of this, but would you run
```
df -i
```
Maybe its full

---

### Post by ian-weisser on 2015-07-16
Did you run 'sudo apt-get update' first?
It seems unlikely that linux-image and linux-image-extra would upgrade separately. They should upgrade together. Always.

---

### Post by Travelguy on 2015-07-17
Doesn't seem to be full and update seems to run without errors:
 
```

Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda6      6250496 355801 5894695    6% /
udev            495355    580  494775    1% /dev
tmpfs           505917    527  505390    1% /run
none            505917      3  505914    1% /run/lock
none            505917      6  505911    1% /run/shm
none            505917     15  505902    1% /run/user

```

---

### Post by ian-weisser on 2015-07-17
'sudo apt-get update' running without error is expected. All it does is update the dpkg database, so all the proper package upgrade together.
 
Looking at the current kernel packages...
```
$ rmadison linux-image-generic
 linux-image-generic | 3.2.0.23.25  | precise          | amd64, i386
 linux-image-generic | 3.2.0.87.101 | precise-security | amd64, i386
 linux-image-generic | 3.2.0.87.101 | precise-updates  | amd64, i386
 linux-image-generic | 3.2.0.88.102 | precise-proposed | amd64, i386
 linux-image-generic | 3.13.0.24.28 | trusty           | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.13.0.57.64 | trusty-security  | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.13.0.57.64 | trusty-updates   | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.13.0.58.65 | trusty-proposed  | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.16.0.23.24 | utopic           | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.16.0.43.43 | utopic-security  | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.16.0.43.43 | utopic-updates   | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.16.0.44.44 | utopic-proposed  | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.19.0.15.14 | vivid            | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.19.0.22.21 | vivid-security   | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.19.0.22.21 | vivid-updates    | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.19.0.23.22 | vivid-proposed   | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 4.0.0.4.6    | wily             | amd64, arm64, armhf, i386, ppc64el
```

I'm not seeing kernel 3.5 series among current releases.
That leads me to suspect that you are using 12.04.2 (which used kernel 3.5).
If true, unfortunately those kernel images have been long withdrawn - your solution is to upgrade to a newer HWE stack (see [here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"); 12.04.5 uses kernel 3.13) or to reinstall a newer version of Ubuntu (14.04 LTS or 15.04).

---

