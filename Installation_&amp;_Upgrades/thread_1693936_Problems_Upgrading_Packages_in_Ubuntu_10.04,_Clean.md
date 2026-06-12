---
title: "Problems Upgrading Packages in Ubuntu 10.04, Clean Install on USB Pendrive"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by Kvbx4 on 2011-02-23
Hello,

I just performed a clean install of Ubuntu 10.04 on my flash drive, allocating a 6.5 GB persistence file. Of course, the first thing I did after booting from it was to run sudo apt-get update and sudo apt-get upgrade. After a lengthy install process, I was eventually notified that several packages failed to upgrade. I rebooted and tried again, still to no avail. Now, whenever I install a new package or attempt to upgrade with apt-get, I receive the following or a simmilar output:

```

Setting up fuse-utils (2.8.1-1.1ubuntu2.2) ...
creating fuse group...
udev active, skipping device node creation.
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing fuse-utils (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gvfs-fuse:
 gvfs-fuse depends on fuse-utils; however:
  Package fuse-utils is not configured yet.
dpkg: error processing gvfs-fuse (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up udev (151-12.3) ...
udev start/running, process 4075
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dmsetup:
 dmsetup depends on udev (>> 141-2); however:
  Package udev is not configured yet.
dpkg: error processing dmsetup (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on udev (>= 149-2); however:
  Package udev is not configured yet.
dpkg: error processing plymouth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
 plymouth-theme-ubuntu-text depends on plymouth; however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-theme-ubuntu-text (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gdm:
 gdm depends on udev (>= 149-2); however:
  Package udev is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hal:
 hal depends on udev (>= 143); however:
  Package udev is not configured yet.
dpkg: error processing hal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of media-player-info:
 media-player-info depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing media-player-info (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-label:
 plymouth-label depends on plymouth (= 0.8.2-2ubuntu2.2); however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-label (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-logo:
 plymouth-theme-ubuntu-logo depends on plymouth; however:
  Package plymouth is not configured yet.
 plymouth-theme-ubuntu-logo depends on plymouth-label; however:
  Package plymouth-label is not configured yet.
dpkg: error processing plymouth-theme-ubuntu-logo (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-x11:
 plymouth-x11 depends on plymouth (= 0.8.2-2ubuntu2.2); however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-x11 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on media-player-info; however:
  Package media-player-info is not configured yet.
dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of rhythmbox-plugin-cdrecorder:
 rhythmbox-plugin-cdrecorder depends on rhythmbox (= 0.12.8-0ubuntu7); however:
  Package rhythmbox is not configured yet.
dpkg: error processing rhythmbox-plugin-cdrecorder (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of rhythmbox-plugins:
 rhythmbox-plugins depends on rhythmbox (= 0.12.8-0ubuntu7); however:
  Package rhythmbox is not configured yet.
dpkg: error processing rhythmbox-plugins (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of udisks:
 udisks depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing udisks (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of usb-creator-common:
 usb-creator-common depends on udisks (>= 1.0~); however:
  Package udisks is not configured yet.
 usb-creator-common depends on udisks (<< 1.1); however:
  Package udisks is not configured yet.
dpkg: error processing usb-creator-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of usb-creator-gtk:
 usb-creator-gtk depends on usb-creator-common (= 0.2.22.1); however:
  Package usb-creator-common is not configured yet.
dpkg: error processing usb-creator-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on udev (>= 149); however:
  Package udev is not configured yet.
dpkg: error processing xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-geode:
 xserver-xorg-video-geode depends on xserver-xorg-core (>= 2:1.6.99.900); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-geode (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of casper:
 casper depends on dmsetup; however:
  Package dmsetup is not configured yet.
dpkg: error processing casper (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on udev (>= 147~-5); however:
  Package udev is not configured yet.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-2.6.32-28-generic:
 linux-image-2.6.32-28-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-2.6.32-28-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-28-generic; however:
  Package linux-image-2.6.32-28-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.28.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 fuse-utils
 gvfs-fuse
 udev
 dmsetup
 plymouth
 plymouth-theme-ubuntu-text
 gdm
 hal
 media-player-info
 plymouth-label
 plymouth-theme-ubuntu-logo
 plymouth-x11
 rhythmbox
 rhythmbox-plugin-cdrecorder
 rhythmbox-plugins
 udisks
 usb-creator-common
 usb-creator-gtk
 xserver-xorg-core
 xserver-xorg-video-geode
 casper
 initramfs-tools
 linux-image-2.6.32-28-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```In Synaptic, the error message is:

```

E: fuse-utils: subprocess installed post-installation script returned error exit status 1
E: gvfs-fuse: dependency problems - leaving unconfigured
E: udev: subprocess installed post-installation script returned error exit status 1
E: dmsetup: dependency problems - leaving unconfigured
E: plymouth: dependency problems - leaving unconfigured
E: plymouth-theme-ubuntu-text: dependency problems - leaving unconfigured
E: gdm: dependency problems - leaving unconfigured
E: hal: dependency problems - leaving unconfigured
E: media-player-info: dependency problems - leaving unconfigured
E: plymouth-label: dependency problems - leaving unconfigured
E: plymouth-theme-ubuntu-logo: dependency problems - leaving unconfigured
E: plymouth-x11: dependency problems - leaving unconfigured
E: rhythmbox: dependency problems - leaving unconfigured
E: rhythmbox-plugin-cdrecorder: dependency problems - leaving unconfigured
E: rhythmbox-plugins: dependency problems - leaving unconfigured
E: udisks: dependency problems - leaving unconfigured
E: usb-creator-common: dependency problems - leaving unconfigured
E: usb-creator-gtk: dependency problems - leaving unconfigured
E: xserver-xorg-core: dependency problems - leaving unconfigured
E: xserver-xorg-video-geode: dependency problems - leaving unconfigured
E: casper: dependency problems - leaving unconfigured
E: initramfs-tools: dependency problems - leaving unconfigured
E: linux-image-2.6.32-28-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

```How can I determine what is causing this error and how to correct it? Any help would be very greatly appreciated.

---

### Post by oldfred on 2011-02-23
The USB installer version is good for testing Ubuntu and installing it. You can add persistence to allow you to save some files. But it cannot update eveything as it still is the ISO installer. I think even updated apps have to be reupdated on every reboot, even if downloaded. Kernel then cannot be updated.

If your flash drive is that large and you want a current install, why not a full install. I have a full install on my 16GB flash with 8GB for / and about 8GB for data.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Kvbx4 on 2011-02-28
> **oldfred said:**
> The USB installer version is good for testing Ubuntu and installing it. You can add persistence to allow you to save some files. But it cannot update eveything as it still is the ISO installer. I think even updated apps have to be reupdated on every reboot, even if downloaded. Kernel then cannot be updated.

If your flash drive is that large and you want a current install, why not a full install. I have a full install on my 16GB flash with 8GB for / and about 8GB for data.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Okay,

My apps and settings do persist from boot to boot, but Your explanation would still explain this problem and the other one I've been having, an error when I try to run update-grub. I was going to post a separate thread about that, but now I guess I don't need to. I think I will go with your suggestion and perform a full install.

Thanks for your useful advice.

---

