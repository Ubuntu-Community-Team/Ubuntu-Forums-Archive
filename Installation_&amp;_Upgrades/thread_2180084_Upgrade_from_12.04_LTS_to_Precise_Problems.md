---
title: "Upgrade from 12.04 LTS to Precise Problems"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by Claude_Sutton on 2013-10-11
I have fought this problem for about three weeks.

Downloading Precise directly from Ubuntu and burning a disk or putting it on a memory stick results in crashes, loss of the boot process and all sorts of bad things.

Failure messages similar to bad CD, bad drive, etc.

Ran memory tests, linux babblocks, etc., with no problems found.

Machine is an HP Pavillion Laptop with 70GB drive and 7.7 GB memory.

Precise would run from memory using the stick, but would not install.

So the only solution was to reinstall LTS and do an upgrade from there.

What follows is the return from apt-get dist-upgrade.

I can post the entire return if anyone wants to see all of it.

This has become a serious problem, resulting in crashes, loss of boot, etc.

Luckily I have boot repair, but other things crash that can only be fixed with a re-install and that is getting tiresome.

I have tried all of the suggestions regarding rebuilding lists, keyrings, hash, etc., that I can find on this forum and on the web with no improvement.

I would appreciate suggistions.

By the way, I have another laptop, a Lenovo Think Pad that has run like a charm for years...one of the very first Lenovo's...and I put the memory stick in it to see if it would update and it crahsed it big time.

Ran boot repair and when I asked it to reboot, it returned "No operating system".

Lucky for me that everything that I might need that was on it has been sived to an external drive.

If the stick is bad, I have two bad sticks of different makes purchased a long time apart.

If I have a bad CD, the system tests lied and I have a bad CD and two sticks.

Not likely.

I created the sticks with system creator.


```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_6.5ubuntu6.6_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.14.2-6ubuntu2.3_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.15-0ubuntu10.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnutls26/libgnutls26_2.12.14-5ubuntu3.5_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulsedsp_1.1-0ubuntu15.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.8.1-0ubuntu4.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.8.1-0ubuntu4.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libx/libxi/libxi6_1.6.0-0ubuntu2.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-declarative_4.8.1-0ubuntu4.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.8.1-0ubuntu4.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.8.1-0ubuntu4.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.8.1-0ubuntu4.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qdbus_4.8.1-0ubuntu4.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.6.3-2ubuntu2.8_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libxatracker1-lts-quantal_9.0.3-0ubuntu0.4~precise1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcursor/libxcursor1_1.1.12-1ubuntu0.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxrandr-lts-quantal/libxrandr-ltsq2_1.4.0-1~precise2_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxrandr/libxrandr2_1.3.2-2ubuntu0.2_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/isc-dhcp/isc-dhcp-common_4.1.ESV-R4-0ubuntu5.9_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib4_0.9.4.0-0ubuntu4.3_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomekbd/libgnomekbd7_3.4.0.2-1ubuntu0.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_3.4.2-0ubuntu8_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-greeter/unity-greeter_0.2.9-0ubuntu1.2_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/w/whoopsie-daisy/whoopsie_0.1.33_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglu1-mesa_8.0.4-0ubuntu0.6_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.8.16~exp12ubuntu10.15_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres80_9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-80_9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dosfstools/dosfstools_3.0.12-1ubuntu1.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_1.0.1-4ubuntu5.10_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-driver/alsa-base_1.0.25+dfsg-0ubuntu1.1_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt-xapian-index/apt-xapian-index_0.44ubuntu5.1_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz-plugins-main/compiz-plugins-main-default_0.9.7.0~bzr19-0ubuntu10.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.9.7.12-0ubuntu2_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity/libunity-core-5.0-5_5.20.0-0ubuntu2_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-common_5.20.0-0ubuntu2_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/libgnome-control-center1_3.4.2-0ubuntu0.12_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/duplicity/duplicity_0.6.18-0ubuntu3.2_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_3.4.0-0ubuntu1.7_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook-1.2-12_3.2.3-0ubuntu7.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_3.2.3-0ubuntu7.1_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_24.0+build1-0ubuntu0.12.04.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-libs_1.12.1-0ubuntu1.2_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_3.4.2-0ubuntu8_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_2.96-0ubuntu4.3_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/libnm-gtk0_0.9.4.1-0ubuntu2.3_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libgcr-3-common_3.2.2-2ubuntu4.1_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.2.2-2ubuntu4.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-screenshot/gnome-screenshot_3.4.1-0ubuntu1.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_3.4.2-0ubuntu2.3_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-common_0.9.7-0ubuntu7.11_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui-3.0-1_3.2.3-0ubuntu7.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libpam-gnome-keyring_3.2.2-2ubuntu4.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.10.3-0ubuntu1.3_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-emailmerge_3.5.7-0ubuntu4_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-style-human_3.5.7-0ubuntu4_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-style-tango_3.5.7-0ubuntu4_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_3.0.2-0ubuntu2_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-2d/unity-2d-spread_5.14.0-0ubuntu1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-2d/libunity-2d-private0_5.14.0-0ubuntu1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.79.6_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-lts-quantal/linux-headers-3.5.0-41_3.5.0-41.64~precise1_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mtools/mtools_4.0.12-1ubuntu0.12.04.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-utils_1.1-0ubuntu15.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio_1.1-0ubuntu15.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-x11_1.1-0ubuntu15.4_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/remmina/remmina-plugin-rdp_1.0.0-1ubuntu6.3_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/remmina/remmina-plugin-vnc_1.0.0-1ubuntu6.3_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/remmina/remmina_1.0.0-1ubuntu6.3_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rtkit/rtkit_0.10-2ubuntu0.12.04.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.6.3-2ubuntu2.8_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.82.7.5_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-gabble/telepathy-gabble_0.16.0-0ubuntu3.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-idle/telepathy-idle_0.1.11-2ubuntu0.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-common_0.2.38.2_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/usbmuxd/usbmuxd_1.0.7-2ubuntu0.1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/v/vino/vino_3.4.2-0ubuntu1.3_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel-lts-quantal/xserver-xorg-video-intel-lts-quantal_2.20.9-0ubuntu2.2~precise1_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-openchrome-lts-quantal/xserver-xorg-video-openchrome-lts-quantal_0.3.1-0ubuntu1~precise3_amd64.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sessioninstaller/sessioninstaller_0.20+bzr128-0ubuntu1.3_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by Claude_Sutton on 2013-10-11
I ran dist-upgrade again with --fix-missing and it seems to have helped.  I will not say solved because I am not sure.  However, I am still getting "can not be authenticated" and I would like to fix that.

---

