---
title: "Unable to install “Additional Drivers” after upgrade to Ubuntu 20.04 LTS"
date: 2020-12-12
forum: Installation &amp; Upgrades
---

### Post by steve2267 on 2020-12-12
**Summary**:
--------------

I am unable to install "Additional Drivers" after upgrading from Ubuntu 18.04 LTS to Ubuntu 20.04 LTS. I receive the following error message:

Unable to install "Additional Drivers": Error while installing package: installed linux-image-4.15.0-88- generic package post-removal script subprocess returned error exit status 1

System: Dell Precision 5510 Mobile Workstation, 32GB RAM, 1TB Samsung NVMe hard drive; dual-booted with Winbloze 7 Pro-64


**Details**:
----------

If I try to rip out the package 'linux-image-4.15.0-88-generic' manually, it fails. I am stuck. It also appears that I am unable to add / remove any other packages as well.

```

% sudo apt remove linux-image-4.15.0-88-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  browser-plugin-evince g++-7 gir1.2-mutter-2 libargon2-0 libavutil55 libbasicusageenvironment1 libboost-chrono1.65.1 libboost-iostreams1.65.1
  libboost-locale1.65.1 libcapnp-0.6.1 libcdio17 libdouble-conversion1 libdrm-dev libdvdread4 libebml4v5 libfluidsynth1 libgdbm5 libgfortran4 libglade2-0
  libgmime-3.0-0 libgnome-desktop-3-17 libgspell-1-1 libgtkmm-2.4-1v5 libicu60 libip4tc0 libiptc0 libisc169 libisl19 libjson-c3 libllvm9:i386 liblwres160
  libmagickcore-6.q16-3 libmutter-2-0 libmysofa0 libnfs11 libnss-myhostname libnvidia-common-435 libnvidia-compute-435 libnvidia-compute-435:i386
  libnvidia-decode-435:i386 libnvidia-encode-435 libnvidia-ifr1-435 libnvidia-ifr1-435:i386 libperl5.26 libplacebo7 libpoppler73 libpostproc54
  libprotobuf10 libproxy-tools libqpdf21 libraw16 libresid-builder0c2a libssh2-1 libtinfo-dev libtinfo5:i386 libusageenvironment3 libvlc5 libvlccore9
  libx265-146 libx86emu1 libxcb-glx0-dev libxcb-render0-dev libxcb-sync-dev libxfixes-dev libxshmfence-dev linux-headers-4.15.0-99
  linux-modules-4.15.0-99-generic nvidia-compute-utils-435 nvidia-dkms-435 nvidia-kernel-common-435 php-cli php-common php-xml php7.4-cli php7.4-common
  php7.4-json php7.4-opcache php7.4-readline php7.4-xml python-cairo python-fasteners python-gobject-2 python-gtk2 python-lockfile python-monotonic
  python-six python3-asn1crypto python3-oauth qt4-qmake socat ubuntu-web-launchers vlc-data vlc-plugin-video-output
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-4.15.0-88-generic linux-image-4.15.0-99-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 16.8 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 331573 files and directories currently installed.)
Removing linux-image-4.15.0-88-generic (4.15.0-88.88) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-88-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
using custom appearance settings
Found linux image: /boot/vmlinuz-5.4.0-58-generic
Found initrd image: /boot/initrd.img-5.4.0-58-generic
Found linux image: /boot/vmlinuz-4.15.0-128-generic
Found initrd image: /boot/initrd.img-4.15.0-128-generic
**/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: [COLOR="#FF0000"]libcrypto.so.1.0.0: cannot open shared object file: No such file or directory[/COLOR]**
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-4.15.0-88-generic (--remove):
 installed linux-image-4.15.0-88-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-4.15.0-88-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

When I check installed linux-image packages, I get the following:

```
% aptitude search linux-image | grep -v ^p
v  linux-image - 
c  linux-image-4.13.0-45-generic - 
i A linux-image-4.15.0-128-generic - Signed kernel image generic
c  linux-image-4.15.0-74-generic - 
c  linux-image-4.15.0-76-generic - 
Bd linux-image-4.15.0-88-generic - Signed kernel image generic
H  linux-image-4.15.0-99-generic - Signed kernel image generic
i A linux-image-5.4.0-58-generic - Signed kernel image generic
c  linux-image-extra-4.10.0-28-generic - 
c  linux-image-extra-4.10.0-42-generic - 
i A linux-image-generic - Generic Linux kernel image
v  linux-image-oem-5.6 - 

```


I am stuck. How do I rip this package out or fix what is wrong? I haven't done any package management myself. All I did was an "upgrade" from 18.04 LTS to 20.04 LTS via the Software Update widget.

TIA.

---

### Post by CelticWarrior on 2020-12-12
Welcome.

Doing what you intend to do manually is, simply put, not recommended.
What users typically and correctly do instead is the sequence:
```
sudo apt update
sudo apt full-upgrade
sudo apt autoremove #this one deals specifically will old kernels
```

---

### Post by steve2267 on 2020-12-13
Hi,  thank you for the reply.

Can you expound on what you mean by "*Doing what you intend to do manually is, simply put, not recommended.*"?  What do you mean by "what you intend to do"?  Are you referring to my attempt to remove the old kernel image via the command **sudo apt remove linux-image-4.15.0-88-generic** ?

What I attempted to do was upgrade the system by clicking the mouse a few times and letting this GUI automagically handle the update.  But it appears to have left an old kernel package in a bad state, and now my package management appears to be broken and won't let me add or remove any other packages.

Here are the results of my running the three commands you gave:[INDENT]
[FONT=Courier New]```
% **sudo apt update**
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [109 kB]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease                            
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]           
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [24.3 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB] 
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [56.6 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [237 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [205 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe DEP-11 64x64 Icons [204 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata [1,768 B]
Fetched 1,054 kB in 2s (675 kB/s)                       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```
```
% **sudo apt full-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  browser-plugin-evince g++-7 gir1.2-mutter-2 libargon2-0 libavutil55 libbasicusageenvironment1 libboost-chrono1.65.1
  libboost-iostreams1.65.1 libboost-locale1.65.1 libcapnp-0.6.1 libcdio17 libdouble-conversion1 libdrm-dev libdvdread4
  libebml4v5 libfluidsynth1 libgdbm5 libgfortran4 libglade2-0 libgmime-3.0-0 libgnome-desktop-3-17 libgspell-1-1
  libgtkmm-2.4-1v5 libicu60 libip4tc0 libiptc0 libisc169 libisl19 libjson-c3 libllvm9:i386 liblwres160 libmagickcore-6.q16-3
  libmutter-2-0 libmysofa0 libnfs11 libnss-myhostname libnvidia-common-435 libnvidia-compute-435 libnvidia-compute-435:i386
  libnvidia-decode-435:i386 libnvidia-encode-435 libnvidia-ifr1-435 libnvidia-ifr1-435:i386 libperl5.26 libplacebo7 libpoppler73
  libpostproc54 libprotobuf10 libproxy-tools libqpdf21 libraw16 libresid-builder0c2a libssh2-1 libtinfo-dev libtinfo5:i386
  libusageenvironment3 libvlc5 libvlccore9 libx265-146 libx86emu1 libxcb-glx0-dev libxcb-render0-dev libxcb-sync-dev
  libxfixes-dev libxshmfence-dev linux-headers-4.15.0-99 linux-modules-4.15.0-99-generic nvidia-compute-utils-435
  nvidia-dkms-435 nvidia-kernel-common-435 php-cli php-common php-xml php7.4-cli php7.4-common php7.4-json php7.4-opcache
  php7.4-readline php7.4-xml python-cairo python-fasteners python-gobject-2 python-gtk2 python-lockfile python-monotonic
  python-six python3-asn1crypto python3-oauth qt4-qmake socat ubuntu-web-launchers vlc-data vlc-plugin-video-output
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-4.15.0-88-generic linux-image-4.15.0-99-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 16.8 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 331573 files and directories currently installed.)
Removing linux-image-4.15.0-88-generic (4.15.0-88.88) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-88-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
using custom appearance settings
Found linux image: /boot/vmlinuz-5.4.0-58-generic
Found initrd image: /boot/initrd.img-5.4.0-58-generic
Found linux image: /boot/vmlinuz-4.15.0-128-generic
Found initrd image: /boot/initrd.img-4.15.0-128-generic
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.0.0: cannot open shared object file: No such f
ile or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
[B]dpkg: error processing package linux-image-4.15.0-88-generic (--remove):
 installed linux-image-4.15.0-88-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-4.15.0-88-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]
```
%```
 **sudo apt autoremove**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  browser-plugin-evince g++-7 gir1.2-mutter-2 libargon2-0 libavutil55 libbasicusageenvironment1 libboost-chrono1.65.1
  libboost-iostreams1.65.1 libboost-locale1.65.1 libcapnp-0.6.1 libcdio17 libdouble-conversion1 libdrm-dev libdvdread4
  libebml4v5 libfluidsynth1 libgdbm5 libgfortran4 libglade2-0 libgmime-3.0-0 libgnome-desktop-3-17 libgspell-1-1
  libgtkmm-2.4-1v5 libicu60 libip4tc0 libiptc0 libisc169 libisl19 libjson-c3 libllvm9:i386 liblwres160 libmagickcore-6.q16-3
  libmutter-2-0 libmysofa0 libnfs11 libnss-myhostname libnvidia-common-435 libnvidia-compute-435 libnvidia-compute-435:i386
  libnvidia-decode-435:i386 libnvidia-encode-435 libnvidia-ifr1-435 libnvidia-ifr1-435:i386 libperl5.26 libplacebo7 libpoppler73
  libpostproc54 libprotobuf10 libproxy-tools libqpdf21 libraw16 libresid-builder0c2a libssh2-1 libtinfo-dev libtinfo5:i386
  libusageenvironment3 libvlc5 libvlccore9 libx265-146 libx86emu1 libxcb-glx0-dev libxcb-render0-dev libxcb-sync-dev
  libxfixes-dev libxshmfence-dev linux-headers-4.15.0-99 linux-image-4.15.0-88-generic linux-image-4.15.0-99-generic
  linux-modules-4.15.0-99-generic nvidia-compute-utils-435 nvidia-dkms-435 nvidia-kernel-common-435 php-cli php-common php-xml
  php7.4-cli php7.4-common php7.4-json php7.4-opcache php7.4-readline php7.4-xml python-cairo python-fasteners python-gobject-2
  python-gtk2 python-lockfile python-monotonic python-six python3-asn1crypto python3-oauth qt4-qmake socat ubuntu-web-launchers
  vlc-data vlc-plugin-video-output
0 upgraded, 0 newly installed, 95 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 387 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 331573 files and directories currently installed.)
Removing linux-image-4.15.0-88-generic (4.15.0-88.88) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-88-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
using custom appearance settings
Found linux image: /boot/vmlinuz-5.4.0-58-generic
Found initrd image: /boot/initrd.img-5.4.0-58-generic
Found linux image: /boot/vmlinuz-4.15.0-128-generic
Found initrd image: /boot/initrd.img-4.15.0-128-generic
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.0.0: cannot open shared object file: No such f
ile or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
[B]dpkg: error processing package linux-image-4.15.0-88-generic (--remove):
 installed linux-image-4.15.0-88-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-4.15.0-88-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
```[/FONT]
[/INDENT]

---

