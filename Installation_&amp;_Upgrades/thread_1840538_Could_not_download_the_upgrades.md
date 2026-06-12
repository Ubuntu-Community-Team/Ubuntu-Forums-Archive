---
title: "Could not download the upgrades"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by techbrainless on 2011-09-07
Hi All,

I am trying to upgrade from 10.10 to 11.04 using alternative DVD

but getting the following error
( by the way i have executed the commands apt-get update && upgrade before upgrading from the DVD

```

Could not download the upgrades

The upgrade has aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.


Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/upstart/upstart_0.9.7-1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/util-linux/mount_2.17.2-9.1ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/udev/libudev0_167-0ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/util-linux/util-linux_2.17.2-9.1ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/z/zlib/zlib1g-dev_1.2.3.4.dfsg-3ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/z/zlib/zlib1g_1.2.3.4.dfsg-3ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xkeyboard-config/xkb-data_2.1-1ubuntu3_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xorg/x11-common_7.6+4ubuntu3_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/util-linux/libuuid1_2.17.2-9.1ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/x11-xkb-utils/x11-xkb-utils_7.6+2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xorg-server/xserver-common_1.10.1-1ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-tseng/xserver-xorg-video-tseng_1.2.4-0ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-siliconmotion/xserver-xorg-video-siliconmotion_1.7.4-0ubuntu7_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-r128/xserver-xorg-video-r128_6.8.1-4ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-mach64/xserver-xorg-video-mach64_6.8.2+git20101202.d60087f0-4ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-radeon_6.14.0-0ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.14.0-0ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-i740/xserver-xorg-video-i740_1.3.2-3ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-geode/xserver-xorg-video-geode_2.11.12-1build2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-qxl/xserver-xorg-video-qxl_0.0.12-1ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-apm/xserver-xorg-video-apm_1.2.3-0ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-ark/xserver-xorg-video-ark_0.7.3-1ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-chips/xserver-xorg-video-chips_1.2.3-2ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-cirrus/xserver-xorg-video-cirrus_1.3.2-2ubuntu7_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-fbdev/xserver-xorg-video-fbdev_0.4.2-3ubuntu6_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-i128/xserver-xorg-video-i128_1.3.4-1ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.14.0-4ubuntu7_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-mga/xserver-xorg-video-mga_1.4.13.dfsg-3build1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-neomagic/xserver-xorg-video-neomagic_1.2.5-1ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.2.904+svn916-1build1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-rendition/xserver-xorg-video-rendition_4.2.4-0ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-s3/xserver-xorg-video-s3_0.6.3-3ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-s3virge/xserver-xorg-video-s3virge_1.10.4-3ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-savage/xserver-xorg-video-savage_2.3.2-3ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.10.3-2ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-sisusb/xserver-xorg-video-sisusb_0.9.4-0ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-tdfx/xserver-xorg-video-tdfx_1.4.3-3ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-trident/xserver-xorg-video-trident_1.3.4-0ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-vesa/xserver-xorg-video-vesa_2.3.0-4ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-voodoo/xserver-xorg-video-voodoo_1.2.4-0ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ucf/ucf_3.0025+nmu1ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/tiff/libtiff4_3.9.4-5ubuntu6_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.6.1-0ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/twisted-names/python-twisted-names_10.1.0-1build2_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xorg/xserver-xorg-video-all_7.6+4ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xorg/xserver-xorg_7.6+4ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-vmware/xserver-xorg-video-vmware_11.0.3-1ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-input-mouse/xserver-xorg-input-mouse_1.6.0-1ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/utouch-evemu/libutouch-evemu1_1.0.5-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/utouch-frame/libutouch-frame1_1.1.1-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/utouch-grail/libutouch-grail1_1.0.20-0ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu12_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.6.0-1ubuntu12_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xf86-input-wacom/xserver-xorg-input-wacom_0.10.11-0ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.6.99.901-1ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xserver-xorg-video-nouveau/xserver-xorg-video-nouveau_0.0.16+git20110107+b795ca6e-0ubuntu7_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xorg-server/xserver-xorg-core_1.10.1-1ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/udev/udev_167-0ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/w/wsgi-intercept/python-wsgi-intercept_0.4-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-meta/ubuntu-minimal_1.220_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/w/webkit/libwebkitgtk-1.0-common_1.3.13-0ubuntu2_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/w/webkit/libwebkitgtk-1.0-0_1.3.13-0ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/y/yelp-xsl/yelp-xsl_3.0.0-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/y/yelp/yelp_3.0.0-0ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/update-manager/update-manager_0.150_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/update-manager/update-manager-core_0.150_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/vte/gir1.2-vte-0.0_0.27.90-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/utouch-geis/libutouch-geis1_2.0.10-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/unity/unity-common_3.8.10-0ubuntu2_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/unity-asset-pool/unity-asset-pool_0.8.20-0ubuntu2_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/unity/unity_3.8.10-0ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-meta/ubuntu-desktop_1.220_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/virtkey/python-virtkey_0.60.0-0ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/twisted/python-twisted-bin_10.2.0-1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/twisted/python-twisted-core_10.2.0-1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xapian-core/libxapian22_1.2.4-1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xapian-bindings/python-xapian_1.2.3-3ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ufw/ufw_0.30.1-1ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/vte/python-vte_0.27.90-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_1.2.1-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/twisted-web/python-twisted-web_10.2.0-1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/z/zope.interface/python-zope.interface_3.6.1-0ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/vte/libvte-common_0.27.90-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/vte/libvte9_0.27.90-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xauth/xauth_1.0.5-1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/unattended-upgrades/unattended-upgrades_0.72.1ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xz-utils/liblzma2_5.0.0-2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xz-utils/xz-utils_5.0.0-2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/update-inetd/update-inetd_4.38_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/v4l-utils/libv4l-0_0.8.3-1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/w/wget/wget_1.12-2.1ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/unzip/unzip_6.0-4ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/z/zip/zip_3.0-3build1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/upower/libupower-glib1_0.9.9-4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/udev/libgudev-1.0-0_167-0ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/upower/upower_0.9.9-4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/usbmuxd/libusbmuxd1_1.0.7-1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/usbmuxd/usbmuxd_1.0.7-1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/util-linux/libblkid1_2.17.2-9.1ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/udisks/udisks_1.0.2-4ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xft/libxft2_2.2.0-2ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-system-service/ubuntu-system-service_0.1.21_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/x11-utils/x11-utils_7.6+1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/w/whois/whois_5.0.11ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/z/zenity/zenity_2.32.1-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntuone-storage-protocol/python-ubuntuone-storageprotocol_1.6.0-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntuone-client/libsyncdaemon-1.0-1_1.6.1-0ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntuone-client/ubuntuone-client_1.6.1-0ubuntu3_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.6.1-0ubuntu3_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/util-linux/bsdutils_2.17.2-9.1ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-sounds/ubuntu-sounds_0.13_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/update-notifier/update-notifier_0.111ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/update-notifier/update-notifier-common_0.111ubuntu2_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/w/wireless-tools/libiw30_30~pre9-3ubuntu6_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/w/wireless-tools/wireless-tools_30~pre9-3ubuntu6_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/w/wpasupplicant/wpasupplicant_0.7.3-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xdg-user-dirs/xdg-user-dirs_0.13-2ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xfonts-encodings/xfonts-encodings_1.0.4-1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xfonts-utils/xfonts-utils_7.6~1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xfonts-base/xfonts-base_1.0.3_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/x11-apps/x11-apps_7.6+4ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/x11-session-utils/x11-session-utils_7.6+1ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/x11-xserver-utils/x11-xserver-utils_7.6+2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xinit/xinit_1.3.0-1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xorg-docs/xorg-docs-core_1.5.99.901-1ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xbitmaps/xbitmaps_1.1.1-1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xterm/xterm_268-1ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xinput/xinput_1.5.3-2ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xorg/xorg_7.6+4ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xscreensaver/xscreensaver-data_5.12-0ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xscreensaver/xscreensaver-gl_5.12-0ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xorg/xserver-xorg-input-all_7.6+4ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ureadahead/ureadahead_0.100.0-11_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/vim/vim-tiny_7.3.035+hg~8fdc12103333-1ubuntu7_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/vim/vim-common_7.3.035+hg~8fdc12103333-1ubuntu7_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/w/wireless-crda/wireless-crda_1.13_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-docs/ubuntu-docs_11.04.2_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/usb-modeswitch/usb-modeswitch_1.1.7-1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/usb-modeswitch-data/usb-modeswitch-data_20110227-2_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/usbutils/usbutils_0.87-5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/time/time_1.7-23.1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-meta/ubuntu-standard_1.220_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/util-linux/uuid-runtime_2.17.2-9.1ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/totem-pl-parser/libtotem-plparser17_2.32.4-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-geoip/geoclue-ubuntu-geoip_0.0.2-0ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-mono/ubuntu-mono_0.0.30_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/unixodbc/odbcinst1debian2_2.2.14p2-2ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/unixodbc/odbcinst_2.2.14p2-2ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xdg-utils/xdg-utils_1.1.0~rc1-2ubuntu3_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/tomboy/tomboy_1.6.0-0ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/totem/totem-plugins_2.32.0-0ubuntu10_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/totem/totem-mozilla_2.32.0-0ubuntu10_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/totem/totem-common_2.32.0-0ubuntu10_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/totem/totem_2.32.0-0ubuntu10_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/transmission/transmission-gtk_2.13-0ubuntu8_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/transmission/transmission-common_2.13-0ubuntu8_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/tsclient/tsclient_0.150-4ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/ttf-indic-fonts/ttf-indic-fonts-core_0.5.11ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/ttf-kacst-one/ttf-kacst-one_4.0-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/ttf-lao/ttf-lao_0.0.20060226-7_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/ttf-indic-fonts/ttf-punjabi-fonts_0.5.11ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/t/ttf-takao/ttf-takao-pgothic_003.02.01-4ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-font-family-sources/ttf-ubuntu-font-family_0.71.2-0ubuntu3_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntu-wallpapers/ubuntu-wallpapers_0.31.10_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/z/zeitgeist/zeitgeist-core_0.7.1-1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/z/zeitgeist-datahub/zeitgeist-datahub_0.7.0-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/z/zeitgeist/zeitgeist_0.7.1-1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/z/zeitgeist-extensions/zeitgeist-extension-fts_0.0.7-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/unity-place-applications/unity-place-applications_0.2.46-0ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/unity-place-files/unity-place-files_0.5.46-0ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/unixodbc/unixodbc_2.2.14p2-2ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/usb-creator/usb-creator-gtk_0.2.28_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/usb-creator/usb-creator-common_0.2.28_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/vbetool/vbetool_1.1-2ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/vinagre/vinagre_2.30.3-1ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/v/vino/vino_2.32.1-0ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/w/w3m/w3m_0.5.3-1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xcursor-themes/xcursor-themes_1.0.3-1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/x/xfonts-scalable/xfonts-scalable_1.0.3-1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntuone-control-panel/python-ubuntuone-control-panel_1.0.0-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntuone-control-panel/ubuntuone-control-panel_1.0.0-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/pool/main/u/ubuntuone-control-panel/ubuntuone-control-panel-gtk_1.0.0-0ubuntu1_all.deb Hash Sum mismatch

```

---

### Post by Hakunka-Matata on 2011-09-07
Kernel.org/ got hacked.
[http://www.google.com/#q=kernel.org+compromised&hl=en&prmd=ivnsu&source=univ&tbm=nws&tbo=u&sa=X&ei=4ANoTqTiHubmiAKAjbmZDQ&sqi=2&ved=0CDAQqAI&bav=on.2,or.r_gc.r_pw.&fp=425cd68637565bc9&biw=1920&bih=967](http://www.google.com/#q=kernel.org+compromised&hl=en&prmd=ivnsu&source=univ&tbm=nws&tbo=u&sa=X&ei=4ANoTqTiHubmiAKAjbmZDQ&sqi=2&ved=0CDAQqAI&bav=on.2,or.r_gc.r_pw.&fp=425cd68637565bc9&biw=1920&bih=967)

---

### Post by techbrainless on 2011-09-08
Thanks Hakunka-Matata ,

>  		Kernel.org/ got hacked.
[http://www.google.com/#q=kernel.org+...w=1920&bih=967]("http://www.google.com/#q=kernel.org+compromised&hl=en&prmd=ivnsu&source=univ&tbm=nws&tbo=u&sa=X&ei=4ANoTqTiHubmiAKAjbmZDQ&sqi=2&ved=0CDAQqAI&bav=on.2,or.r_gc.r_pw.&fp=425cd68637565bc9&biw=1920&bih=967")

Sorry I did not get you .......

---

### Post by Hakunka-Matata on 2011-09-08
Kernel.org/ got hacked, and they shut down a bunch of servers, so there are / were a lot of updaters and others getting errors when attempting to download updates and other software.  Maybe they are all back up and running now, Sept.8,2011:16:00 UTC

You can try simply changing which repository mirror you're using.  If you're in the us, don't use Main Mirror, try choosing **"other"** let it search through ~368 distinct mirror sites to pick the closest/fastest one to you, makes a difference at times.

---

