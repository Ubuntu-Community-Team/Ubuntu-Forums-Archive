---
title: "broken package prevents any install"
date: 2017-02-19
forum: Installation &amp; Upgrades
---

### Post by Raphael_Poli on 2017-02-19
Hello,
I use Ubuntu 16.04 LTS
I have a broken package of kernel 4.4.0-51 that is unused, and blocks all installation process.
when I try to reinstall it I get this:
```

Selecting previously unselected package linux-image-4.4.0-51-generic.
(Reading database ... 334756 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-51-generic_4.4.0-51.72_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Done.
Unpacking linux-image-4.4.0-51-generic (4.4.0-51.72) ...
Selecting previously unselected package linux-image-extra-4.4.0-51-generic.
Preparing to unpack .../linux-image-extra-4.4.0-51-generic_4.4.0-51.72_amd64.deb ...
Unpacking linux-image-extra-4.4.0-51-generic (4.4.0-51.72) over (4.4.0-51.72) ...
Setting up linux-image-4.4.0-51-generic (4.4.0-51.72) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.4.0-51.72 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.4.0-51.72 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Fatal: open /dev/disk/by-id/: Is a directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-51-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-51-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-51-generic:
 linux-image-extra-4.4.0-51-generic depends on linux-image-4.4.0-51-generic; however:
  Package linux-image-4.4.0-51-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-51-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                       Errors were encountered while processing:
 linux-image-4.4.0-51-generic
 linux-image-extra-4.4.0-51-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-4.4.0-51-generic (4.4.0-51.72) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.4.0-51.72 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.4.0-51.72 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Fatal: open /dev/disk/by-id/: Is a directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-51-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-51-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-51-generic:
 linux-image-extra-4.4.0-51-generic depends on linux-image-4.4.0-51-generic; however:
  Package linux-image-4.4.0-51-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-51-generic (--configure):
 dependency problems - leaving unconfigured
```


Someone told me to create empty files with the indicated name to enable removal of the package, but it seems to search for a disk?
Can you help?

---

### Post by QIII on 2017-02-19
Hello!

Let's see if making sure the kernel is completely updated helps.

```
sudo apt update
```
```
sudo apt dist-upgrade
```

dist-upgrade does not upgrade to a newer release.  It upgrades all of the packages (including the kernel) to the latest available for the release you have installed, making "intelligent" choices about what to update.

Let us know if that helps.

---

### Post by Raphael_Poli on 2017-02-26
The same problem seems to happen.
I'm getting even more problems with the false files I'll try to remove them.
Thanks for the try.
```
Setting up firefox-locale-en (51.0.1+build2-0ubuntu0.16.04.2) ...
Setting up libjavascriptcoregtk-4.0-18:amd64 (2.14.5-0ubuntu0.16.04.1) ...
Setting up libwebkit2gtk-4.0-37:amd64 (2.14.5-0ubuntu0.16.04.1) ...
Setting up libwebkit2gtk-4.0-37-gtk2:amd64 (2.14.5-0ubuntu0.16.04.1) ...
Setting up gir1.2-javascriptcoregtk-4.0:amd64 (2.14.5-0ubuntu0.16.04.1) ...
Setting up gir1.2-webkit2-4.0:amd64 (2.14.5-0ubuntu0.16.04.1) ...
Setting up iucode-tool (1.5.1-1ubuntu0.1) ...
Setting up mysql-common (5.7.17-0ubuntu0.16.04.1) ...
Setting up libmysqlclient20:i386 (5.7.17-0ubuntu0.16.04.1) ...
Setting up libpcsclite1:amd64 (1.8.14-1ubuntu1.16.04.1) ...
Setting up libssh2-1:amd64 (1.5.0-2ubuntu0.1) ...
Setting up libvncclient1:amd64 (0.9.10+dfsg-3ubuntu0.16.04.1) ...
Setting up libxpm4:i386 (1:3.5.11-1ubuntu0.16.04.1) ...
Setting up libxpm4:amd64 (1:3.5.11-1ubuntu0.16.04.1) ...
Setting up linux-firmware (1.157.8) ...
update-initramfs: Generating /boot/initrd.img-4.8.10-040810-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915
Fatal: open /dev/disk/by-id/: Is a directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Fatal: open /dev/disk/by-id/: Is a directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-64-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-64-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-64-generic:
 linux-image-extra-4.4.0-64-generic depends on linux-image-4.4.0-64-generic; however:
  Package linux-image-4.4.0-64-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-64-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-64-generic; however:
  Package linux-image-4.4.0-64-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-64-generic; however:
  Package linux-image-extra-4.4.0-64-generic is not configured yet.
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-4.4.0-64 (4.4.0-64.85) ...
Setting up linux-headers-4.4No apport report written because the error message indicates its a followup error from a previous failure.
                                                      No apport report written because MaxReports is reached already
                                    .0-64-generic (4.4.0-64.85) ...
Setting up linux-headers-generic (4.4.0.64.68) ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.64.68); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-4.4.0-64-generic:
 linux-signed-image-4.4.0-64-generic depends on linux-image-4.4.0-64-generic (= 4.4.0-64.85); however:
  Package linux-image-4.4.0-64-generic is not configured yet.

dpkg: error processing package linux-signed-image-4.4.0-64-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-generic:
 linux-signed-image-generic depends on linux-signed-image-4.4.0-64-generic; however:
  Package linux-signed-image-4.4.0-64-generic is not configured yet.
 linux-signed-iNo apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                         mage-generic depends on linux-image-extra-4.4.0-64-generic; however:
  Package linux-image-extra-4.4.0-64-generic is not configured yet.
 linux-signed-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.

dpkg: error processing package linux-signed-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-signed-image-generic (= 4.4.0.64.68); however:
  Package linux-signed-image-generic is not configured yet.

dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-4.4.0-62 (4.4.0-62.83) ...
Setting up linux-headers-4.4.0-62-generic (4.4.0-62.83) ...
Setting up linux-image-4.4.0-51-generic (4.4.0-51.72) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.4.0-51.72 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.4.0-51.72 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Fatal: open /dev/disk/by-id/: Is a directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-51-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-51-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-4.4.0-62-generic (4.4.0-62.83) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Fatal: open /dev/disk/by-id/: Is a directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-62-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-62-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-51-generic:
 linux-image-extra-4.4.0-51-generic depends on linux-image-4.4.0-51-generic; however:
  Package linux-image-4.4.0-51-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-51-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.4.0-53-generic (4.4.0-53.74) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.4.0-53.74 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.4.0-53.74 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Fatal: open /dev/disk/by-id/: Is a directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-53-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-53-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-4.4.0-53-generic (--configure):
 package linux-image-extra-4.4.0-53-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-62-generic:
 linux-image-extra-4.4.0-62-generic depends on linux-image-4.4.0-62-generic; however:
  Package linux-image-4.4.0-62-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-62-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Setting up linux-libc-dev:amd64 (4.4.0-64.85) ...
dpkg: dependency problems prevent configuration of linux-signed-image-4.4.0-62-generic:
 linux-signed-image-4.4.0-62-generic depends on linux-image-4.4.0-62-generic (= 4.4.0-62.83); however:
  Package linux-image-4.4.0-62-generic is not configured yet.

dpkg: error processing package linux-signed-image-4.4.0-62-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-tools-common (4.4.0-64.85) ...
No apport report written because MaxReports is reached already
                                                              Setting up linux-tools-4.4.0-62 (4.4.0-62.83) ...
Setting up linux-tools-4.4.0-62-generic (4.4.0-62.83) ...
Setting up linux-tools-4.4.0-64 (4.4.0-64.85) ...
Setting up linux-tools-4.4.0-64-generic (4.4.0-64.85) ...
Setting up linux-tools-virtual (4.4.0.64.68) ...
Setting up python-crypto (2.6.1-6ubuntu0.16.04.2) ...
Setting up python-samba (2:4.3.11+dfsg-0ubuntu0.16.04.3) ...
Setting up samba-common-bin (2:4.3.11+dfsg-0ubuntu0.16.04.3) ...
Setting up thunderbird (1:45.7.0+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-gnome-support (1:45.7.0+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-locale-en (1:45.7.0+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-locale-en-us (1:45.7.0+build1-0ubuntu0.16.04.1) ...
Setting up oxideqt-codecs:amd64 (1.20.4-0ubuntu0.16.04.1) ...
Setting up imagemagick-common (8:6.8.9.9-7ubuntu5.4) ...
Setting up libmagickcore-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.4) ...
Setting up libmagickwand-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.4) ...
Setting up fonts-opensymbol (2:102.7+LibO5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up uno-libs3 (5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up ure (5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up tcpdump (4.9.0-1ubuntu1~ubuntu16.04.1) ...
Installing new version of config file /etc/apparmor.d/usr.sbin.tcpdump ...
Setting up imagemagick-6.q16 (8:6.8.9.9-7ubuntu5.4) ...
Setting up imagemagick (8:6.8.9.9-7ubuntu5.4) ...
Setting up libmagickcore-6.q16-2-extra:amd64 (8:6.8.9.9-7ubuntu5.4) ...
Setting up libreoffice-common (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Installing new version of config file /etc/bash_completion.d/libreoffice.sh ...
Setting up libreoffice-style-galaxy (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-style-breeze (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libnss3-nssdb (2:3.26.2-0ubuntu0.16.04.2) ...
Setting up libnss3:amd64 (2:3.26.2-0ubuntu0.16.04.2) ...
Setting up chromium-browser (55.0.2883.87-0ubuntu0.16.04.1263) ...
Setting up chromium-browser-l10n (55.0.2883.87-0ubuntu0.16.04.1263) ...
Setting up flashplugin-installer (24.0.0.221ubuntu0.16.04.1) ...
Setting up liboxideqtcore0:amd64 (1.20.4-0ubuntu0.16.04.1) ...
Setting up liboxideqtquick0:amd64 (1.20.4-0ubuntu0.16.04.1) ...
Setting up liboxideqt-qmlplugin:amd64 (1.20.4-0ubuntu0.16.04.1) ...
Setting up libreoffice-core (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-base-core (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-calc (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-gtk (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-gnome (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-writer (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-draw (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-impress (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-ogltrans (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-pdfimport (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up python3-uno (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-math (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:5.1.6~rc2-0ubuntu1~xenial1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for initramfs-tools (0.122ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-4.8.10-040810-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915
Fatal: open /dev/disk/by-id/: Is a directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-firmware
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-generic
 linux-generic
 linux-signed-image-4.4.0-64-generic
 linux-signed-image-generic
 linux-signed-generic
 linux-image-4.4.0-51-generic
 linux-image-4.4.0-62-generic
 linux-image-extra-4.4.0-51-generic
 linux-image-4.4.0-53-generic
 linux-image-extra-4.4.0-53-generic
 linux-image-extra-4.4.0-62-generic
 linux-signed-image-4.4.0-62-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Raphael_Poli on 2017-02-26
all the packages that create errors are old packages that I don't use anymore.

---

### Post by ian-weisser on 2017-02-26
There's only one important error, and it seems obvious in the error messages:
> Fatal: open /dev/disk/by-id/: Is a directory

Fix whatever you did to /dev/disk/

Creating dummy files to facilitate removal is a useful trick...but only if you read and understand the error messages.
Another approach, easier to understand, is to reinstall the offending packages so you can remove them properly.

---

### Post by Raphael_Poli on 2017-02-26
Yes I did see that this line was important. But I did nothing to this directory.
Thanks for your great consideration.
regards,

---

### Post by Impavidus on 2017-02-26
> **Raphael_Poli said:**
> Hello,
I use Ubuntu 16.04 LTS
I have a broken package of kernel 4.4.0-51 that is unused, and blocks all installation process.
when I try to reinstall it I get this:
```
(...)
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Fatal: open /dev/disk/by-id/: Is a directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
(...)
```


Someone told me to create empty files with the indicated name to enable removal of the package, but it seems to search for a disk?
Can you help?

/dev/disk/by-id/ is *supposed* to be a directory. Nothing wrong with your file system, but it seems there's something wrong with /etc/kernel/postinst.d/zz-runlilo, which is a post-install script executed after installing a new kernel. But that script shouldn't be there by default, as Ubuntu systems usually use /etc/kernel/postinst.d/zz-update-grub, which updates grub for us. That tells us you may have the lilo boot loader installed, which is no longer maintained. Using that instead of grub isn't really recommended.

---

### Post by Raphael_Poli on 2017-02-27
Hello Impavidus, Thanks for your reply!
Could you please tell me how to remove the lilo boot?
by the way I'm surprised I could have an old boot system as I installed the lastest ubuntu last year.
I'm a little afraid to remove lilo boot, by the way, in case my computer don't boot at all after that ;)
regards,
Raphael

---

### Post by Impavidus on 2017-02-27
That may depend a bit on your system. Is it bios or uefi? Dual booting with another Linux or with Windows? Secure boot enabled or not? Have you installed from one of the official install .isos or one you picked up somewhere else? I think the official .isos all use grub, unofficial .isos may be different.

I'm still on a bios system, so if your's is different I don't really know. But I'm sure there are enough people around here who know.

---

### Post by Raphael_Poli on 2017-02-28
I think my system is bios. How can I check for sure?
I don't have dual boot, I just have linux.
I don't know what is secure boot.
I don't remember where I found the iso.
But I know I changed the kernel with "grub customizer" and it seemed to work fine.

---

### Post by Impavidus on 2017-02-28
Can you give the output of this command?```
dpkg --list 'grub*' 'lilo*'
```

---

### Post by Raphael_Poli on 2017-02-28
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  grub           0.97-29ubunt amd64        GRand Unified Bootloader (Legacy 
ii  grub-common    2.02~beta2-3 amd64        GRand Unified Bootloader (common 
un  grub-coreboot  <none>       <none>       (no description available)
ii  grub-customize 5.0.6-0ubunt amd64        Grub Customizer - A graphical Gru
un  grub-efi       <none>       <none>       (no description available)
rc  grub-efi-amd64 2.02~beta2-3 amd64        GRand Unified Bootloader, version
un  grub-efi-amd64 <none>       <none>       (no description available)
un  grub-efi-ia32  <none>       <none>       (no description available)
un  grub-efi-ia64  <none>       <none>       (no description available)
un  grub-emu       <none>       <none>       (no description available)
un  grub-ieee1275  <none>       <none>       (no description available)
un  grub-legacy    <none>       <none>       (no description available)
un  grub-legacy-do <none>       <none>       (no description available)
un  grub-linuxbios <none>       <none>       (no description available)
un  grub-pc        <none>       <none>       (no description available)
un  grub-xen       <none>       <none>       (no description available)
un  grub-yeeloong  <none>       <none>       (no description available)
un  grub2          <none>       <none>       (no description available)
un  grub2-common   <none>       <none>       (no description available)
ii  lilo           1:24.2-1     amd64        LInux LOader - the classic OS boo

```

---

### Post by Impavidus on 2017-03-01
It seems grub-efi-amd64 has been installed in the past, which suggests an uefi system. But grub legacy is installed too, along with lilo. I don't have an uefi system myself, so I'm not entirely sure what to do and an error here can make your computer unbootable. I think you have to uninstall grub and lilo and install grub-efi-amd64, but wait for someone else to confirm.

Maybe [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") can fix this. But I suggest you wait for someone else to tell you what to do.

---

### Post by Raphael_Poli on 2017-03-01
Thank you Impavidus for investigating with me.

---

### Post by patrickdug on 2017-03-01
I am getting the same error when I try to run the update:  

Check if you are using third-party repositories. If so, disable them, because they are a common source of problems.
Furthermore, run the following command in a Terminal: apt-get install -f

When I try to run that command I get:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I tried running the other commands suggested previously to no avail.  They just return more errors.

I'm not a programmer, I'm a user, click an icon and things work.  This constant battle with install errors is frustrating.  I run Ubuntu on two older computers (so I don't need Windoz). I'm only running one application on my Ubuntu systems, BOINC.

---

### Post by Raphael_Poli on 2017-03-02
I still get 
Fatal: open /dev/disk/by-id/: Is a directory
with install -f

---

### Post by tbenst on 2017-03-07
I've seen a number of very similar errors recently:
[https://ubuntuforums.org/showthread.php?t=2351895](https://ubuntuforums.org/showthread.php?t=2351895)
[https://ubuntuforums.org/showthread.php?t=2353606](https://ubuntuforums.org/showthread.php?t=2353606)
[https://ubuntuforums.org/showthread.php?t=2353633](https://ubuntuforums.org/showthread.php?t=2353633)

For the lock problem, you can try `sudo killall dpkg` or `sudo killall apt-get` followed by `sudo dpkg --configure -a`. If you see any problems with `update-initramfs`, which appears to be the underlying cause in several cases, please mark [this bug]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1667512") as affecting you to try and raise attention. Unfortunately I've seen similar bugs dating back to [2010]("https://ubuntuforums.org/showthread.php?t=1611122"). I would not advise restarting until you have an afternoon to burn, as some users have resorted to a fresh install after failing to resolve the issue.

---

### Post by Impavidus on 2017-03-07
patrickdug and tbenst: I'm not convinced you've got the same problem. This is not about update-initramfs hanging, it's about an error message from a script that shouldn't be there in the first place.

OP: It seems the people who really know everything about grub don't read this thread. I suggest you make sure you've got a live disk and verify the live disk works. Now, I don't know about grub-customizer, but I can't find it in the repositories. That software may have done something wrong. I suggest you remove it. Run these two commands to double-check your system's configuration:```
uname -a
ls /boot
```The first should list something with x86_64 if your system is indeed 64 bit (as I expect), the second should show an EFI directory. If that's the case, then I ***think*** you have to uninstall lilo, grub and grub-customizer and install grub-efi-amd64. With a bit of luck, that will allow you to clean up with```
sudo apt update
sudo apt install -f
sudo apt upgrade
sudo apt autoremove
```With some luck you can now reboot into the latest kernel. But if you're not so lucky, it may not boot at all. If so, boot from your live disk and try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), which should be able to fix grub.

---

### Post by patrickdug on 2017-03-07
I ran the first two commands and they appeared to have worked, the 'error' flag is gone, however when I try to run the last two commands I get the following errors messages:

sudo apt upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

sudo apt autoremove
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

no idea, this is all gibberish to me but at least the error flag is gone, for now!

---

