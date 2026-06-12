---
title: "Can't view movies after partial upgrade"
date: 2014-02-10
forum: Installation &amp; Upgrades
---

### Post by mark1977 on 2014-02-10
HI,
I'm on 12.04, all movies are blank after a partial upgrade.
Here's the output of apt-get upgrade:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cinnamon gir1.2-muffin-3.0 libdrm-dev libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau1a libdrm-nouveau1a:i386
  libdrm-nouveau2 libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386 libgl1-mesa-dri
  libgl1-mesa-dri:i386 libkms1 linux-headers-generic linux-headers-generic-lts-quantal
  linux-signed-image-generic-lts-quantal marco marco-common mate-control-center mate-settings-daemon
  mate-settings-daemon-common mate-settings-daemon-gstreamer nautilus-renamer nemo nemo-data shim-signed
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa
  xserver-xorg-video-vmware
0 to upgrade, 0 to newly install, 0 to remove and 54 not to upgrade.
24 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up procps (1:3.2.8-11ubuntu6.3) ...
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dmsetup:
 dmsetup depends on udev (>> 141-2); however:
  Package udev is not configured yet.
dpkg: error processing dmsetup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing apport-gtk (--confNo apport report written because the error message indicates it's a follow-up error from a previous failure.
                                No apport report written because the error message indicates it's a follow-up error from a previous failure.
                       No apport report written because MaxReports has already been reached
                                                                                           No apport report written because MaxReports has already been reached
                                          No apport report written because MaxReports has already been reached
                                                                                                              No apport report written because MaxReports has already been reached
                                                             No apport report written because MaxReports has already been reached
            No apport report written because MaxReports has already been reached
                                                                                No apport report written because MaxReports has already been reached
                               No apport report written because MaxReports has already been reached
                                                                                                   No apport report written because MaxReports has already been reached
                                                  No apport report written because MaxReports has already been reached
 igure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-kde:
 apport-kde depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing apport-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox:
 checkbox depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing checkbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-qt:
 checkbox-qt depends on checkbox (>= 0.13.10); however:
  Package checkbox is not configured yet.
dpkg: error processing checkbox-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dropbox:
 dropbox depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing dropbox (--configure):
 dependency problems - leaving unconfigured
dpkg:No apport report written because MaxReports has already been reached
                                                                         No apport report written because MaxReports has already been reached
                        No apport report written because MaxReports has already been reached
                                                                                            No apport report written because MaxReports has already been reached
                                           No apport report written because MaxReports has already been reached
                                                                                                               No apport report written because MaxReports has already been reached
                                                              No apport report written because MaxReports has already been reached
             No apport report written because MaxReports has already been reached
                                                                                 No apport report written because MaxReports has already been reached
                                No apport report written because MaxReports has already been reached
                                                                                                    No apport report written because MaxReports has already been reached
                                                    dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on udev (>= 154); however:
  Package udev is not configured yet.
dpkg: error processing gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nemo-fileroller:
 nemo-fileroller depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing nemo-fileroller (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-widget-networkmanagement:
 plasma-widget-networkmanagement depends on network-manager (>= 0.9.0); however:
  Package network-manager is not configured yet.
dpkg: error processing plasma-widget-networkmanagement (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upower:
 upower depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing upower (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on udev (>= 147~-5); however:
  Package udev is not configured yet.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdevmapper1.02.1:
 libdevmapper1.02.1 depends on dmsetup (>= 2:1.02.48-4ubuntu7.4); however:
  Package dmsetup is not configured yet.
dpkg: error processing libdevmapper1.02.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-common:
 grub-common depends on libdevmapper1.02.1 (>= 2:1.02.36); however:
  Package libdevmapper1.02.1 is not configured yet.
dpkg: error processing grub-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 1.99-21ubuntu3.14); however:
  Package grub-common is not configured yet.
dpkg: error processing grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64-bin:
 grub-efi-amd64-bin depends on grub-common (= 1.99-21ubuntu3.14); however:
  Package grub-common is not configured yet.
dpkg: error processing grub-efi-amd64-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64:
 grub-efi-amd64 depends on grub-common; however:
  Package grub-common is not configured yet.
 grub-efi-amd64 depends on grub2-common (= 1.99-21ubuntu3.14); however:
  Package grub2-common is not configured yet.
 grub-efi-amd64 depends on grub-efi-amd64-bin (= 1.99-21ubuntu3.14); however:
  Package grub-efi-amd64-bin is not configured yet.
dpkg: error processing grub-efi-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 (>= 1.99-21ubuntu3.5); however:
  Package grub-efi-amd64 is not configured yet.
dpkg: error processing grub-efi-amd64-signed (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdevmapper-event1.02.1:
 libdevmapper-event1.02.1 depends on libdevmapper1.02.1 (>= 2:1.02.36); however:
  Package libdevmapper1.02.1 is not configured yet.
dpkg: error processing libdevmapper-event1.02.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblvm2app2.2:
 liblvm2app2.2 depends on libdevmapper-event1.02.1 (>= 2:1.02.20); however:
  Package libdevmapper-event1.02.1 is not configured yet.
 liblvm2app2.2 depends on libdevmapper1.02.1 (>= 2:1.02.44); however:
  Package libdevmapper1.02.1 is not configured yet.
dpkg: error processing liblvm2app2.2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 procps
 udev
 dmsetup
 network-manager
 apport-gtk
 apport-kde
 checkbox
 checkbox-qt
 dropbox
 gnome-bluetooth
 nemo-fileroller
 plasma-widget-networkmanagement
 samba
 upower
 initramfs-tools
 libdevmapper1.02.1
 apparmor
 grub-common
 grub2-common
 grub-efi-amd64-bin
 grub-efi-amd64
 grub-efi-amd64-signed
 libdevmapper-event1.02.1
 liblvm2app2.2



Here is the output of /usr/share/insserv/check-initd-order:
> error: LSB header missing in /etc/rc2.d/S99acpi-support

Sorry I don't really know much more than that, if anyone could help, I'd be grateful :)

---

### Post by ibjsb4 on 2014-02-11
First :)  'Code tags' work better than 'Quote tags:

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

Partial upgrades are usually not a good idea.

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

You can try this:

```
sudo apt-get dist-upgrade
```

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

