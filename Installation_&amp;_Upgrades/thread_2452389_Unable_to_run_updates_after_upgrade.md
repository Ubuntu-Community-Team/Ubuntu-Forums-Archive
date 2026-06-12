---
title: "Unable to run updates after upgrade"
date: 2020-10-21
forum: Installation &amp; Upgrades
---

### Post by petertrowles on 2020-10-21
During an upgrade from 16.04 to 18.04 I got 4 error messages or warnings. The upgrade seemed to complete and the system now boots and runs ok but I am now unable to run any package updates. The error messages during the upgrade were:
[LIST]
[*]systemd-shim package not installed post removal script subprocess returned error exit status 2
[*]/var/cache/apt/archives/systemd_237-3ubuntu10.39_amd64.deb post removal script subprocess returned error exit status 2
[*]systemd-sysv_237-3ubuntu10.39_amd64.deb post removal script subprocess returned error exit status 2
[*]The upgrade was aborted. Your system could be in an unstable state. A recovery will now run (dpkg -configure -a)
[/LIST]

But it seems like the upgrade was not aborted because the System Information now shows the OS to be Ubuntu 18.04.4 LTS.

Now when I run Software Updater I get this message:
[LIST]
[*]Not all updates can be installed. Run a partial upgrade to install as many updates as possible
[/LIST]
There are two buttons: Partial Upgrade and Continue.

If I click Continue I get this:
[LIST]
[*]Software Index is broken. It is impossible to install or remove any software right now. Please use Synaptic or sudo apt-get install -f to fix this issue.
[/LIST]
If I then run Synaptic the package systemd-shim is marked to be removed. When I then click Apply I get:
[LIST]
[*]Error systemd-shim. installed systemd-shim package post removal script subprocess returned error exit status 2
[/LIST]

If I click Partial Upgrade in the Software Updater it starts to go through the process but I then get:
[LIST]
[*]Could not install systemd-shim
[/LIST]
I click Close and other upgrades seem to continue, then right at the end I get:
[LIST]
[*]Could not install the upgrades. The upgrade has aborted. A recovery will now run (dpkg -configure -a). The upgrade has completed but there were errors.
[/LIST]

I'd be very grateful for any suggestions to get me out of this situation.

Thanks.

---

### Post by ActionParsnip on 2020-10-21
What is the full output of:
```

sudo lsb_release -a; uname -a; sudo apt-get update; sudo apt-get -f install

```

Thanks

---

### Post by petertrowles on 2020-10-21
> **ActionParsnip said:**
> What is the full output of:
```

sudo lsb_release -a; uname -a; sudo apt-get update; sudo apt-get -f install

```

Thanks

Here is the full output - Thanks.

```
sudo lsb_release -a; uname -a; sudo apt-get update; sudo apt-get -f install
[sudo] password for peter: 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic
```
```
Linux peter-1015PE 4.15.0-99-generic #100-Ubuntu SMP Wed Apr 22 20:32:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
Hit:1 [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:3 [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:4 [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu) bionic-security InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cgmanager consolekit cpp-5 efibootmgr esound-common evolution-data-server-online-accounts gcc-5-base gcc-5-base:i386 gcc-6-base gcc-6-base:i386
  gnupg-agent gtk3-engines-unico hardening-includes imagemagick-common libaccounts-glib0 libaccounts-qt5-1 libaio1 libass5 libaudcore3 libaudgui3
  libaudiofile1 libaudtag2 libavcodec-ffmpeg56 libavfilter-ffmpeg5 libavformat-ffmpeg56 libavresample-ffmpeg2 libavutil-ffmpeg54 libbind9-140 libbinio1v5
  libboost-filesystem1.58.0 libboost-filesystem1.65.1 libboost-system1.58.0 libcamel-1.2-54 libcapnp-0.5.3 libcapnp-0.6.1 libcgmanager0 libchromaprint0
  libck-connector0 libcomerr2:i386 libdata-alias-perl libdns-export162 libdns162 libebook-1.2-16 libedataserver-1.2-21 libefivar0 libesd0 libfcitx-gclient0
  libfcitx-qt0 libfwup0 libfwupd1 libgnome2-0 libgnome2-bin libgtkglext1 libgweather-3-6 libical1a libidn11:i386 libido3-0.1-0 libisc-export160 libisc160
  libisccc140 libisccfg140 libisl15 libjasper1 libjpeg9 libllvm6.0 libllvm6.0:i386 liblouis9 liblouisutdml6 liblwres141 libmimic0 libmirclient9
  libmircommon7 libmircore1 libmirprotobuf3 libmpfr4 libnma-common libopencv-calib3d2.4v5 libopencv-contrib2.4v5 libopencv-core2.4v5
  libopencv-features2d2.4v5 libopencv-flann2.4v5 libopencv-highgui2.4v5 libopencv-imgproc2.4v5 libopencv-legacy2.4v5 libopencv-ml2.4v5
  libopencv-objdetect2.4v5 libopencv-video2.4v5 libopenjpeg5 libpackagekit-glib2-16 libpcre16-3 libpng12-0:i386 libpoppler58 libpostproc-ffmpeg53 libprocps4
  libprotobuf-lite10 libprotobuf-lite9v5 libpython3.5 libpython3.5-minimal libpython3.5-stdlib libqt5opengl5 libqt5sql5 libqt5sql5-sqlite libqt5xml5
  libsignon-extension1 libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsodium18 libsrtp0 libswresample-ffmpeg1 libswscale-ffmpeg3 libtbb2
  libtxc-dxtn-s2tc0:i386 libudev1:i386 libunistring0 libvpx3 libwebp5 libwebpdemux1 libwebrtc-audio-processing-0 libwildmidi1 libwps-0.4-4 libx264-148
  libx265-79 libxapian22v5 libxfont1 libxtables11 linux-headers-4.4.0-177 linux-headers-4.4.0-177-generic linux-image-4.4.0-177-generic
  linux-modules-4.4.0-177-generic linux-modules-extra-4.4.0-177-generic lubuntu-artwork-16-04 python-ndg-httpsclient python-pyasn1 python3-bs4
  python3-html5lib python3-lxml python3-pycurl python3-webencodings python3.5 python3.5-minimal rename signon-plugin-password signon-ui signon-ui-service
  signon-ui-x11 signond xserver-xorg-video-neomagic xserver-xorg-video-openchrome xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  systemd-shim
0 to upgrade, 0 to newly install, 1 to remove and 296 not to upgrade.
1 not fully installed or removed.
After this operation, 71.7 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 228451 files and directories currently installed.)
Removing systemd-shim (9-1bzr4ubuntu1) ...
Removing 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' with
  different file '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd', not allowed
dpkg: error processing package systemd-shim (--remove):
 installed systemd-shim package post-removal script subprocess returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by CelticWarrior on 2020-10-21
Try 

```
sudo apt update && sudo apt full-upgrade
```

Any change?

---

### Post by petertrowles on 2020-10-22
> **CelticWarrior said:**
> Try 

```
sudo apt update && sudo apt full-upgrade
```

Any change?

No change. It fails to remove systemd-shim because it's not allowed to rename something. Here's the output:

sudo apt update && sudo apt full-upgrade
[sudo] password for peter: 
Hit:1 [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:3 [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:4 [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu) bionic-security InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
299 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  cgmanager consolekit cpp-5 efibootmgr esound-common evolution-data-server-online-accounts gcc-5-base gcc-5-base:i386 gcc-6-base gcc-6-base:i386
  gnupg-agent gtk3-engines-unico hardening-includes imagemagick-common libaccounts-glib0 libaccounts-qt5-1 libaio1 libass5 libaudcore3 libaudgui3
  libaudiofile1 libaudtag2 libavcodec-ffmpeg56 libavfilter-ffmpeg5 libavformat-ffmpeg56 libavresample-ffmpeg2 libavutil-ffmpeg54 libbind9-140 libbinio1v5
  libboost-filesystem1.58.0 libboost-filesystem1.65.1 libboost-system1.58.0 libcamel-1.2-54 libcapnp-0.5.3 libcapnp-0.6.1 libcgmanager0 libchromaprint0
  libck-connector0 libcomerr2:i386 libdata-alias-perl libdns-export162 libdns162 libebook-1.2-16 libedataserver-1.2-21 libefivar0 libesd0 libfcitx-gclient0
  libfcitx-qt0 libfwup0 libfwupd1 libgnome2-0 libgnome2-bin libgtkglext1 libgweather-3-6 libical1a libidn11:i386 libido3-0.1-0 libisc-export160 libisc160
  libisccc140 libisccfg140 libisl15 libjasper1 libjpeg9 libllvm6.0 libllvm6.0:i386 libllvm9 libllvm9:i386 liblouis9 liblouisutdml6 liblwres141 libmimic0
  libmirclient9 libmircommon7 libmircore1 libmirprotobuf3 libmpfr4 libnma-common libopencv-calib3d2.4v5 libopencv-contrib2.4v5 libopencv-core2.4v5
  libopencv-features2d2.4v5 libopencv-flann2.4v5 libopencv-highgui2.4v5 libopencv-imgproc2.4v5 libopencv-legacy2.4v5 libopencv-ml2.4v5
  libopencv-objdetect2.4v5 libopencv-video2.4v5 libopenjpeg5 libpackagekit-glib2-16 libpcre16-3 libpng12-0:i386 libpoppler58 libpostproc-ffmpeg53 libprocps4
  libprotobuf-lite10 libprotobuf-lite9v5 libpython3.5 libpython3.5-minimal libpython3.5-stdlib libqt5opengl5 libqt5sql5 libqt5sql5-sqlite libqt5xml5
  libsignon-extension1 libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsodium18 libsrtp0 libswresample-ffmpeg1 libswscale-ffmpeg3 libtbb2
  libtxc-dxtn-s2tc0:i386 libudev1:i386 libunistring0 libvpx3 libwebp5 libwebpdemux1 libwebrtc-audio-processing-0 libwildmidi1 libwps-0.4-4 libx264-148
  libx265-79 libxapian22v5 libxfont1 libxtables11 linux-headers-4.4.0-177 linux-headers-4.4.0-177-generic linux-image-4.4.0-177-generic
  linux-modules-4.4.0-177-generic linux-modules-extra-4.4.0-177-generic lubuntu-artwork-16-04 python-ndg-httpsclient python-pyasn1 python3-bs4
  python3-html5lib python3-lxml python3-pycurl python3-webencodings python3.5 python3.5-minimal rename signon-plugin-password signon-ui signon-ui-service
  signon-ui-x11 signond xserver-xorg-video-neomagic xserver-xorg-video-openchrome xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  systemd-shim
The following NEW packages will be installed
  libllvm10 libllvm10:i386 libnetplan0 libzstd1:i386 linux-headers-4.15.0-122 linux-headers-4.15.0-122-generic linux-image-4.15.0-122-generic
  linux-modules-4.15.0-122-generic linux-modules-extra-4.15.0-122-generic
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils aptdaemon aptdaemon-data base-files bind9-host binutils binutils-common binutils-x86-64-linux-gnu
  bsdutils busybox-initramfs busybox-static ca-certificates chromium-codecs-ffmpeg-extra cryptsetup cryptsetup-bin dbus dbus-user-session dbus-x11 dirmngr
  dmsetup dnsutils evolution-data-server evolution-data-server-common evolution-data-server-online-accounts fdisk ffmpeg file firefox firefox-locale-en
  flashplugin-installer fwupd fwupd-signed ghostscript ghostscript-x gir1.2-javascriptcoregtk-4.0 gir1.2-packagekitglib-1.0 gir1.2-snapd-1
  gir1.2-webkit2-4.0 glib-networking glib-networking-common glib-networking-services gnupg gnupg-agent gnupg-l10n gnupg-utils gnupg2 gpg gpg-agent
  gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv grub-common grub-pc grub-pc-bin grub2-common initramfs-tools initramfs-tools-bin initramfs-tools-core
  intel-microcode iproute2 kmod libapt-inst2.0 libapt-pkg5.0 libavcodec57 libavdevice57 libavfilter6 libavformat57 libavresample3 libavutil55 libbind9-160
  libbinutils libblkid1 libblkid1:i386 libbrotli1 libc-bin libc-dev-bin libc6 libc6:i386 libc6-dev libcamel-1.2-61 libcephfs2 libcryptsetup12
  libcurl3-gnutls libdbus-1-3 libdbus-1-3:i386 libdevmapper-event1.02.1 libdevmapper1.02.1 libdjvulibre-text libdjvulibre21 libdns-export1100 libdns1100
  libdrm-amdgpu1 libdrm-amdgpu1:i386 libdrm-common libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2 libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386
  libdrm2 libdrm2:i386 libebackend-1.2-10 libebook-1.2-19 libebook-contacts-1.2-2 libecal-1.2-19 libedata-book-1.2-25 libedata-cal-1.2-28
  libedataserver-1.2-23 libegl-mesa0 libegl1-mesa libexif12 libfdisk1 libfreetype6 libfreetype6:i386 libfwupd2 libgbm1 libgl1-mesa-dri libgl1-mesa-dri:i386
  libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386 libgles2-mesa libglx-mesa0 libglx-mesa0:i386 libgnutls-openssl27 libgnutls30
  libgnutls30:i386 libgs9 libgs9-common libirs160 libisc-export169 libisc169 libisccc160 libisccfg160 libjavascriptcoregtk-4.0-18 libjpeg-turbo-progs
  libjpeg-turbo8 libjpeg-turbo8:i386 libjson-c3 libkmod2 libldap-2.4-2 libldap-common liblvm2app2.2 liblwres160 libmagic-mgc libmagic1 libmount1
  libmount1:i386 libmysofa0 libmysqlclient20 libmysqlclient20:i386 libnss-systemd libnss3 libopenexr22 libpackagekit-glib2-18 libpam-modules
  libpam-modules-bin libpam-runtime libpam-systemd libpam0g libpcap0.8 libpostproc54 libproxy1v5 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpython2.7
  libpython2.7-minimal libpython2.7-stdlib libpython3.6 libpython3.6-minimal libpython3.6-stdlib librados2 librsvg2-2 librsvg2-common libsane-common
  libsane1 libseccomp2 libsmartcols1 libsmbclient libsnapd-glib1 libsnmp-base libsnmp30 libsqlite3-0 libsqlite3-0:i386 libssh-gcrypt-4 libssl1.0.0
  libssl1.0.0:i386 libssl1.1 libssl1.1:i386 libswresample2 libswscale4 libsystemd0 libsystemd0:i386 libudev1 libudev1:i386 libuuid1 libuuid1:i386
  libwayland-egl1-mesa libwbclient0 libwebkit2gtk-4.0-37 libwebkit2gtk-4.0-37-gtk2 libwhoopsie0 libx11-6 libx11-6:i386 libx11-data libx11-xcb1
  libx11-xcb1:i386 libxatracker2 libxau6 libxau6:i386 libxmlb1 linux-base linux-firmware linux-generic linux-headers-generic linux-image-generic
  linux-libc-dev locales mesa-va-drivers mesa-vdpau-drivers module-init-tools mount multiarch-support netplan.io nplan ntp ntpdate openssl packagekit
  packagekit-tools ppp pulseaudio pulseaudio-module-bluetooth pulseaudio-utils python-apport python-apt python-apt-common python-aptdaemon
  python-aptdaemon.gtk3widgets python-httplib2 python-problem-report python-samba python-urllib3 python2.7 python2.7-minimal python3-apport python3-apt
  python3-aptdaemon python3-aptdaemon.gtk3widgets python3-distupgrade python3-httplib2 python3-pil python3-problem-report python3-software-properties
  python3-update-manager python3-urllib3 python3.6 python3.6-minimal rfkill samba samba-common samba-common-bin samba-dsdb-modules samba-libs
  samba-vfs-modules sane-utils snapd sntp software-properties-common software-properties-gtk systemd systemd-sysv tzdata ubuntu-minimal
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-standard udev update-manager update-manager-core util-linux uuid-runtime vim-common
  vim-tiny whoopsie xserver-common xserver-xorg-core xserver-xorg-input-wacom xserver-xorg-legacy xxd
299 to upgrade, 9 to newly install, 1 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 403 MB of archives.
After this operation, 552 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y

***Leaving out 308 lines of Get commends***

Fetched 403 MB in 1min 17s (5,263 kB/s)                                                                                                                      
Extract templates from packages: 100%
Preconfiguring packages ...
setting xserver-xorg-legacy/xwrapper/allowed_users from configuration file
(Reading database ... 228451 files and directories currently installed.)
Removing systemd-shim (9-1bzr4ubuntu1) ...
Removing 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' with
  different file '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd', not allowed
dpkg: error processing package systemd-shim (--remove):
 installed systemd-shim package post-removal script subprocess returned error exit status 2
Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks.

---

### Post by grahammechanical on 2020-10-22
The 296 files not to upgrade could be all those files that are no longer required. Have you counted them? I am joking. If you run

```
sudo apt autoremove
```

Those files will disappear. Then the question becomes: Can you run update/upgrade without any issues apart from the one regarding systemd.shim?

Regards

---

### Post by CelticWarrior on 2020-10-22
I also suggest, just in case, ```
sudo apt clean
```

---

### Post by petertrowles on 2020-10-23
Thanks to all for your suggestions, I learned some things. I did some more searching and found a bug report #1773859 on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859) .
The workaround which fixed my problem is as stated there:

sudo mv /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.bak
sudo apt-get install -f
sudo apt dist-upgrade
sudo apt autoremove


Manually renaming the file which stopped the upgrade, allowed the upgrade to 18.04 to complete. Software Updater is now working again and of course now suggests that I should upgrade to 20.04. I might leave that for another day.

---

