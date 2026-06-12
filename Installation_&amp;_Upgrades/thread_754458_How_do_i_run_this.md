---
title: "How do i run this?"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by OutCell on 2008-04-13
hi,
I don't have an internet connection and i am trying to update my system. I downloaded deb files from nonetdebs. In said that i need to run the files using the same list and they provided this script:
> #!/bin/bash
# This script is to upgrade packages
# Created on [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net)
# Date: Sunday 13th of April 2008 11:52:06 PM
#
# If you used Windows to save this script, please open it with:
#
# "nano script_name"
#
# Press Ctrl-o and then press Alt-d to change from:
#
# "File Name to Write [DOS Format]:"
#
# To:
#
# "File Name to Write:"
#
# Then save the script and run it with "sudo bash script_name".
#
dpkg -i ./coreutils_6.10-3ubuntu2_i386.deb
dpkg -i ./debianutils_2.28.2-0ubuntu1_i386.deb
dpkg -i ./libc6_2.7-10ubuntu3_i386.deb
dpkg -i ./libc6-i686_2.7-10ubuntu3_i386.deb
dpkg -i ./libgomp1_4.2.3-2ubuntu7_i386.deb
dpkg -i ./gcc-4.2-base_4.2.3-2ubuntu7_i386.deb
dpkg -i ./libgcc1_4.2.3-2ubuntu7_i386.deb
dpkg -i ./cpp-4.2_4.2.3-2ubuntu7_i386.deb
dpkg -i ./gcc-4.2_4.2.3-2ubuntu7_i386.deb
dpkg -i ./libffi4_4.2.3-2ubuntu7_i386.deb
dpkg -i ./libstdc++6_4.2.3-2ubuntu7_i386.deb
dpkg -i ./e2fslibs_1.40.8-2ubuntu2_i386.deb
dpkg -i ./e2fsprogs_1.40.8-2ubuntu2_i386.deb
dpkg -i ./findutils_4.2.32-1ubuntu2_i386.deb
dpkg -i ./libpam-runtime_0.99.7.1-5ubuntu6_all.deb
dpkg -i ./libpam0g_0.99.7.1-5ubuntu6_i386.deb
dpkg -i ./libpam-modules_0.99.7.1-5ubuntu6_i386.deb
dpkg -i ./login_4.0.18.2-1ubuntu2_i386.deb
dpkg -i ./mktemp_1.5-5ubuntu2_i386.deb
dpkg -i ./mount_2.13.1-4ubuntu1_i386.deb
dpkg -i ./sysvutils_2.86.ds1-14.1ubuntu43_i386.deb
dpkg -i ./tar_1.19-3_i386.deb
dpkg -i ./lsb-base_3.2-4ubuntu1_all.deb
dpkg -i ./tzdata_2008b-1ubuntu1_all.deb
dpkg -i ./util-linux_2.13.1-4ubuntu1_i386.deb
dpkg -i ./base-files_4.0.1ubuntu4_i386.deb
dpkg -i ./bsdutils_2.13.1-4ubuntu1_i386.deb
dpkg -i ./passwd_4.0.18.2-1ubuntu2_i386.deb
dpkg -i ./initscripts_2.86.ds1-14.1ubuntu43_i386.deb
dpkg -i ./sysv-rc_2.86.ds1-14.1ubuntu43_all.deb
dpkg -i ./upstart-compat-sysv_0.3.9-2_i386.deb
dpkg -i ./upstart-logd_0.3.9-2_i386.deb
dpkg -i ./upstart_0.3.9-2_i386.deb
dpkg -i ./python-support_0.7.5ubuntu1_all.deb
dpkg -i ./gnome-applets-data_2.22.1-0ubuntu1_all.deb
dpkg -i ./locales_2.7.9-4_all.deb
dpkg -i ./language-pack-en_8.04+20080401_all.deb
dpkg -i ./language-pack-en-base_8.04+20080325_all.deb
dpkg -i ./language-pack-gnome-en_8.04+20080401_all.deb
dpkg -i ./language-pack-gnome-en-base_8.04+20080325_all.deb
dpkg -i ./libxft2_2.1.12-2ubuntu5_i386.deb
dpkg -i ./openoffice.org-calc_2.4.0-3ubuntu2_i386.deb
dpkg -i ./openoffice.org-impress_2.4.0-3ubuntu2_i386.deb
dpkg -i ./openoffice.org-draw_2.4.0-3ubuntu2_i386.deb
dpkg -i ./libglib2.0-0_2.16.3-1_i386.deb
dpkg -i ./libavahi-common-data_0.6.22-2ubuntu4_i386.deb
dpkg -i ./libavahi-common3_0.6.22-2ubuntu4_i386.deb
dpkg -i ./libavahi-client3_0.6.22-2ubuntu4_i386.deb
dpkg -i ./libavahi-glib1_0.6.22-2ubuntu4_i386.deb
dpkg -i ./shared-mime-info_0.23-5_i386.deb
dpkg -i ./libgnomevfs2-common_2.22.0-2ubuntu1_all.deb
dpkg -i ./libhal1_0.5.11~rc2-1ubuntu6_i386.deb
dpkg -i ./libhal-storage1_0.5.11~rc2-1ubuntu6_i386.deb
dpkg -i ./libgnomevfs2-0_2.22.0-2ubuntu1_i386.deb
dpkg -i ./libidl0_0.8.10-0.1_i386.deb
dpkg -i ./liborbit2_2.14.12-0.1_i386.deb
dpkg -i ./libpixman-1-0_0.10.0-0ubuntu1_i386.deb
dpkg -i ./libcairo2_1.6.0-0ubuntu1_i386.deb
dpkg -i ./libgtk2.0-common_2.12.9-2ubuntu2_all.deb
dpkg -i ./libpango1.0-common_1.20.1-1_all.deb
dpkg -i ./libpango1.0-0_1.20.1-1_i386.deb
dpkg -i ./gtk2-engines-pixbuf_2.12.9-2ubuntu2_i386.deb
dpkg -i ./libcomerr2_1.40.8-2ubuntu2_i386.deb
dpkg -i ./libcupsys2_1.3.7-1ubuntu2_i386.deb
dpkg -i ./libtiff4_3.8.2-7ubuntu3_i386.deb
dpkg -i ./libgtk2.0-0_2.12.9-2ubuntu2_i386.deb
dpkg -i ./openoffice.org-gnome_2.4.0-3ubuntu2_i386.deb
dpkg -i ./openoffice.org-gtk_2.4.0-3ubuntu2_i386.deb
dpkg -i ./openoffice.org-writer_2.4.0-3ubuntu2_i386.deb
dpkg -i ./openoffice.org-l10n-en-za_2.4.0-3ubuntu1_all.deb
dpkg -i ./openoffice.org-core_2.4.0-3ubuntu2_i386.deb
dpkg -i ./openoffice.org-l10n-en-gb_2.4.0-3ubuntu1_all.deb
dpkg -i ./python-uno_2.4.0-3ubuntu2_i386.deb
dpkg -i ./openoffice.org-help-en-gb_2.4.0-3ubuntu1_all.deb
dpkg -i ./openoffice.org-help-en-us_2.4.0-3ubuntu1_all.deb
dpkg -i ./openoffice.org-l10n-common_2.4.0-3ubuntu1_all.deb
dpkg -i ./language-support-translations-en_8.04+20080407_all.deb
dpkg -i ./openoffice.org-style-human_2.4.0-3ubuntu2_all.deb
dpkg -i ./openoffice.org-common_2.4.0-3ubuntu2_all.deb
dpkg -i ./python-central_0.6.1ubuntu2_all.deb
dpkg -i ./bzip2_1.0.4-2ubuntu4_i386.deb
dpkg -i ./libbz2-1.0_1.0.4-2ubuntu4_i386.deb
dpkg -i ./mime-support_3.39-1ubuntu1_all.deb
dpkg -i ./python2.5_2.5.2-2ubuntu3_i386.deb
dpkg -i ./python2.5-minimal_2.5.2-2ubuntu3_i386.deb
dpkg -i ./libgstreamer0.10-0_0.10.18-4ubuntu1_i386.deb
dpkg -i ./libgstreamer-plugins-base0.10-0_0.10.18-3_i386.deb
dpkg -i ./libsasl2-2_2.1.22.dfsg1-18ubuntu2_i386.deb
dpkg -i ./libsasl2-modules_2.1.22.dfsg1-18ubuntu2_i386.deb
dpkg -i ./libldap-2.4-2_2.4.7-6ubuntu3_i386.deb
dpkg -i ./libnspr4-0d_4.7.1~beta2-0ubuntu1_i386.deb
dpkg -i ./libnss3-1d_3.12.0~beta3-0ubuntu1_i386.deb
dpkg -i ./ttf-opensymbol_2.4.0-3ubuntu2_all.deb
dpkg -i ./openoffice.org-base-core_2.4.0-3ubuntu2_i386.deb
dpkg -i ./gnome-user-guide_2.22.0+svn20080407ubuntu1_all.deb
dpkg -i ./ubuntu-docs_8.04.1_all.deb
dpkg -i ./x11-common_7.3+10ubuntu8_i386.deb
dpkg -i ./xkb-data_1.1~cvs.20080104.1-1ubuntu5_all.deb
dpkg -i ./xserver-xorg-core_1.4.1~git20080131-1ubuntu7_i386.deb
dpkg -i ./xserver-xorg-input-evdev_1.2.0-1ubuntu2_i386.deb
dpkg -i ./xserver-xorg-input-wacom_0.7.9.8-0ubuntu3_i386.deb
dpkg -i ./xserver-xorg-input-all_7.3+10ubuntu8_i386.deb
dpkg -i ./xserver-xorg-video-amd_2.7.7.7-1_i386.deb
dpkg -i ./xserver-xorg-video-intel_2.2.1-1ubuntu12_i386.deb
dpkg -i ./xserver-xorg-video-nv_2.1.8-1ubuntu1_i386.deb
dpkg -i ./xserver-xorg-video-vesa_1.3.0-4ubuntu4_i386.deb
dpkg -i ./xserver-xorg-video-all_7.3+10ubuntu8_i386.deb
dpkg -i ./xserver-xorg_7.3+10ubuntu8_all.deb
dpkg -i ./apt_0.7.9ubuntu16_i386.deb
dpkg -i ./libblkid1_1.40.8-2ubuntu2_i386.deb
dpkg -i ./libss2_1.40.8-2ubuntu2_i386.deb
dpkg -i ./libuuid1_1.40.8-2ubuntu2_i386.deb
dpkg -i ./apt-utils_0.7.9ubuntu16_i386.deb
dpkg -i ./libsigc++-2.0-0c2a_2.0.17-2ubuntu3_i386.deb
dpkg -i ./aptitude_0.4.9-2ubuntu5_i386.deb
dpkg -i ./console-setup_1.21ubuntu6_all.deb
dpkg -i ./dhcp3-client_3.0.6.dfsg-1ubuntu9_i386.deb
dpkg -i ./dhcp3-common_3.0.6.dfsg-1ubuntu9_i386.deb
dpkg -i ./iproute_20071016-2ubuntu1_i386.deb
dpkg -i ./klibc-utils_1.5.7-4ubuntu3_i386.deb
dpkg -i ./libklibc_1.5.7-4ubuntu3_i386.deb
dpkg -i ./libsysfs2_2.1.0-4_i386.deb
dpkg -i ./libvolume-id0_117-8_i386.deb
dpkg -i ./lsb-release_3.2-4ubuntu1_all.deb
dpkg -i ./pciutils_2.2.4-1.1ubuntu3_i386.deb
dpkg -i ./tasksel-data_2.70ubuntu5_all.deb
dpkg -i ./tasksel_2.70ubuntu5_all.deb
dpkg -i ./startup-tasks_0.3.9-2_i386.deb
dpkg -i ./system-services_0.3.9-2_i386.deb
dpkg -i ./util-linux-locales_2.13.1-4ubuntu1_all.deb
dpkg -i ./ubuntu-minimal_1.99_i386.deb
dpkg -i ./apparmor_2.1+1075-0ubuntu9_i386.deb
dpkg -i ./apparmor-utils_2.1+1075-0ubuntu9_i386.deb
dpkg -i ./libisc32_9.4.2-10_i386.deb
dpkg -i ./libdns32_9.4.2-10_i386.deb
dpkg -i ./libisccc30_9.4.2-10_i386.deb
dpkg -i ./libisccfg30_9.4.2-10_i386.deb
dpkg -i ./libbind9-30_9.4.2-10_i386.deb
dpkg -i ./liblwres30_9.4.2-10_i386.deb
dpkg -i ./bind9-host_9.4.2-10_i386.deb
dpkg -i ./command-not-found-data_0.2.17ubuntu1_i386.deb
dpkg -i ./python-apt_0.7.4ubuntu7_i386.deb
dpkg -i ./command-not-found_0.2.17ubuntu1_all.deb
dpkg -i ./cron_3.0pl1-100ubuntu2_i386.deb
dpkg -i ./dnsutils_9.4.2-10_i386.deb
dpkg -i ./libnewt0.52_0.52.2-11.2ubuntu1_i386.deb
dpkg -i ./whiptail_0.52.2-11.2ubuntu1_i386.deb
dpkg -i ./friendly-recovery_0.1_all.deb
dpkg -i ./hdparm_8.6-1ubuntu1_i386.deb
dpkg -i ./libparted1.7-1_1.7.1-5.1ubuntu9_i386.deb
dpkg -i ./lshw_02.12.01-2ubuntu1_i386.deb
dpkg -i ./mtr-tiny_0.72-2ubuntu1_i386.deb
dpkg -i ./nano_2.0.7-1ubuntu1_i386.deb
dpkg -i ./openssh-client_4.7p1-8ubuntu1_i386.deb
dpkg -i ./parted_1.7.1-5.1ubuntu9_i386.deb
dpkg -i ./rsync_2.6.9-6ubuntu2_i386.deb
dpkg -i ./ufw_0.16.2_all.deb
dpkg -i ./ubuntu-standard_1.99_i386.deb
dpkg -i ./libgnome-keyring0_2.22.1-1_i386.deb
dpkg -i ./gnome-keyring_2.22.1-1_i386.deb
dpkg -i ./gksu_2.0.0-5ubuntu2_i386.deb
dpkg -i ./update-manager_0.87.17_all.deb
dpkg -i ./update-manager-core_0.87.17_i386.deb
dpkg -i ./acpi-support_0.108_i386.deb
dpkg -i ./app-install-data_0.5.9_all.deb
dpkg -i ./python-launchpad-bugs_0.2.30_all.deb
dpkg -i ./gdb_6.8-1ubuntu1_i386.deb
dpkg -i ./python-problem-report_0.107_all.deb
dpkg -i ./python-apport_0.107_all.deb
dpkg -i ./python-xdg_0.15-1.1ubuntu3_all.deb
dpkg -i ./apport_0.107_all.deb
dpkg -i ./apport-gtk_0.107_all.deb
dpkg -i ./librsvg2-common_2.22.2-2_i386.deb
dpkg -i ./librsvg2-2_2.22.2-2_i386.deb
dpkg -i ./gnome-icon-theme_2.22.0-1ubuntu2_all.deb
dpkg -i ./python-gobject_2.14.1-2ubuntu2_i386.deb
dpkg -i ./python-gst0.10_0.10.11-1_i386.deb
dpkg -i ./gnome-app-install_0.5.2.7-0ubuntu1_all.deb
dpkg -i ./apturl_0.2.1ubuntu1_all.deb
dpkg -i ./python-pyatspi_1.22.1-0ubuntu1_all.deb
dpkg -i ./libatspi1.0-0_1.22.1-0ubuntu1_i386.deb
dpkg -i ./at-spi_1.22.1-0ubuntu1_i386.deb
dpkg -i ./avahi-autoipd_0.6.22-2ubuntu4_i386.deb
dpkg -i ./libavahi-core5_0.6.22-2ubuntu4_i386.deb
dpkg -i ./avahi-daemon_0.6.22-2ubuntu4_i386.deb
dpkg -i ./libbluetooth2_3.29-0ubuntu1_i386.deb
dpkg -i ./bluez-audio_3.26-0ubuntu5_i386.deb
dpkg -i ./cupsys-common_1.3.7-1ubuntu2_all.deb
dpkg -i ./libcupsimage2_1.3.7-1ubuntu2_i386.deb
dpkg -i ./libgs8_8.61.dfsg.1-1ubuntu3_i386.deb
dpkg -i ./ghostscript_8.61.dfsg.1-1ubuntu3_i386.deb
dpkg -i ./libavahi-compat-libdnssd1_0.6.22-2ubuntu4_i386.deb
dpkg -i ./cupsys_1.3.7-1ubuntu2_i386.deb
dpkg -i ./bluez-cups_3.26-0ubuntu5_i386.deb
dpkg -i ./obex-data-server_0.3.1-0ubuntu1_i386.deb
dpkg -i ./bluez-gnome_0.25-0ubuntu1_i386.deb
dpkg -i ./bluez-utils_3.26-0ubuntu5_i386.deb
dpkg -i ./liboil0.3_0.3.14-3_i386.deb
dpkg -i ./gstreamer0.10-plugins-base_0.10.18-3_i386.deb
dpkg -i ./libgnomeui-common_2.22.1.0-0ubuntu1_all.deb
dpkg -i ./libgnomeui-0_2.22.1.0-0ubuntu1_i386.deb
dpkg -i ./libnautilus-burn4_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libedataserver1.2-9_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libcamel1.2-11_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libtotem-plparser10_2.22.2-0ubuntu1_i386.deb
dpkg -i ./brasero_0.7.1-3ubuntu1_i386.deb
dpkg -i ./gnome-about_2.22.1-0ubuntu5_i386.deb
dpkg -i ./gnome-desktop-data_2.22.1-0ubuntu5_all.deb
dpkg -i ./libebook1.2-9_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libgnome-menu2_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libsoup2.4-1_2.4.1-1_i386.deb
dpkg -i ./bug-buddy_2.22.0+dfsg-2_i386.deb
dpkg -i ./capplets-data_2.22.1-0ubuntu2_all.deb
dpkg -i ./compiz-gnome_0.7.4-0ubuntu4_i386.deb
dpkg -i ./compiz-plugins_0.7.4-0ubuntu4_i386.deb
dpkg -i ./libcompizconfig0_0.7.4-0ubuntu1_i386.deb
dpkg -i ./compiz-core_0.7.4-0ubuntu4_i386.deb
dpkg -i ./libdecoration0_0.7.4-0ubuntu4_i386.deb
dpkg -i ./libgl1-mesa-dri_7.0.3~rc2-1ubuntu3_i386.deb
dpkg -i ./libgl1-mesa-glx_7.0.3~rc2-1ubuntu3_i386.deb
dpkg -i ./libglu1-mesa_7.0.3~rc2-1ubuntu3_i386.deb
dpkg -i ./compizconfig-backend-gconf_0.7.4-0ubuntu1_i386.deb
dpkg -i ./gnome-menus_2.22.1-0ubuntu1_i386.deb
dpkg -i ./python-gmenu_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libgnomekbd2_2.22.0-1_i386.deb
dpkg -i ./libgnomekbd-common_2.22.0-1_all.deb
dpkg -i ./gnome-settings-daemon_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libpanel-applet2-0_2.22.1.2-0ubuntu3_i386.deb
dpkg -i ./gnome-control-center_2.22.1-0ubuntu2_i386.deb
dpkg -i ./libgnome-window-settings1_2.22.1-0ubuntu2_i386.deb
dpkg -i ./libgnomekbdui2_2.22.0-1_i386.deb
dpkg -i ./metacity-common_2.22.0-0ubuntu4_all.deb
dpkg -i ./libmetacity0_2.22.0-0ubuntu4_i386.deb
dpkg -i ./libnautilus-extension1_2.22.2-0ubuntu3_i386.deb
dpkg -i ./libgnome-desktop-2_2.22.1-0ubuntu5_i386.deb
dpkg -i ./libwnck-common_2.22.1-0ubuntu1_all.deb
dpkg -i ./libwnck22_2.22.1-0ubuntu1_i386.deb
dpkg -i ./mesa-utils_7.0.3~rc2-1ubuntu3_i386.deb
dpkg -i ./compiz-fusion-plugins-extra_0.7.4-0ubuntu1_i386.deb
dpkg -i ./compiz-fusion-plugins-main_0.7.4-0ubuntu3_i386.deb
dpkg -i ./compiz_0.7.4-0ubuntu4_all.deb
dpkg -i ./cupsys-bsd_1.3.7-1ubuntu2_i386.deb
dpkg -i ./cupsys-client_1.3.7-1ubuntu2_i386.deb
dpkg -i ./deskbar-applet_2.22.1-0ubuntu1_i386.deb
dpkg -i ./guidance-backends_0.8.0svn20080103-0ubuntu14_i386.deb
dpkg -i ./displayconfig-gtk_0.3.10_all.deb
dpkg -i ./dvd+rw-tools_7.0-9ubuntu1_i386.deb
dpkg -i ./evolution-data-server_2.22.1-0ubuntu1_i386.deb
dpkg -i ./evolution-data-server-common_2.22.1-0ubuntu1_all.deb
dpkg -i ./libecal1.2-7_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libedata-book1.2-2_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libedata-cal1.2-6_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libegroupwise1.2-13_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libgdata1.2-1_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libgdata-google1.2-1_2.22.1-0ubuntu1_i386.deb
dpkg -i ./example-content_31_all.deb
dpkg -i ./firefox-3.0-gnome-support_3.0~b5+nobinonly-0ubuntu1_i386.deb
dpkg -i ./firefox-3.0_3.0~b5+nobinonly-0ubuntu1_i386.deb
dpkg -i ./xulrunner-1.9-gnome-support_1.9~b5+nobinonly-0ubuntu1_i386.deb
dpkg -i ./xulrunner-1.9_1.9~b5+nobinonly-0ubuntu1_i386.deb
dpkg -i ./firefox_3.0~b5+nobinonly-0ubuntu1_all.deb
dpkg -i ./firefox-gnome-support_3.0~b5+nobinonly-0ubuntu1_all.deb
dpkg -i ./foo2zjs_20071205-0ubuntu3_i386.deb
dpkg -i ./foomatic-db-hpijs_20070813-0ubuntu2_all.deb
dpkg -i ./gdebi_0.3.7_all.deb
dpkg -i ./gdebi-core_0.3.7_all.deb
dpkg -i ./hal-info_20080317+git20080318-1ubuntu3_all.deb
dpkg -i ./libpolkit2_0.7-2ubuntu6_i386.deb
dpkg -i ./pm-utils_0.99.2-3ubuntu9_all.deb
dpkg -i ./libpolkit-dbus2_0.7-2ubuntu6_i386.deb
dpkg -i ./libpolkit-grant2_0.7-2ubuntu6_i386.deb
dpkg -i ./policykit_0.7-2ubuntu6_i386.deb
dpkg -i ./hal_0.5.11~rc2-1ubuntu6_i386.deb
dpkg -i ./notification-daemon_0.3.7-1ubuntu11_i386.deb
dpkg -i ./gnome-power-manager_2.22.1-1ubuntu4_i386.deb
dpkg -i ./gdm_2.20.5-0ubuntu2_i386.deb
dpkg -i ./gnome-session_2.22.1.1-0ubuntu2_i386.deb
dpkg -i ./xterm_229-1ubuntu1_i386.deb
dpkg -i ./metacity_2.22.0-0ubuntu4_i386.deb
dpkg -i ./xbase-clients_7.3+10ubuntu8_all.deb
dpkg -i ./gedit-common_2.22.1-0ubuntu1_all.deb
dpkg -i ./ghostscript-x_8.61.dfsg.1-1ubuntu3_i386.deb
dpkg -i ./gnome-cards-data_2.22.1.1-0ubuntu3_all.deb
dpkg -i ./gnome-games-data_2.22.1.1-0ubuntu3_all.deb
dpkg -i ./gnome-media-common_2.22.0-0ubuntu3_all.deb
dpkg -i ./libpolkit-gnome0_0.7-2ubuntu1_i386.deb
dpkg -i ./policykit-gnome_0.7-2ubuntu1_i386.deb
dpkg -i ./gnome-mount_0.8~svn20080225-0ubuntu2_i386.deb
dpkg -i ./libbrlapi0.5_3.9-6ubuntu1_i386.deb
dpkg -i ./python-brlapi_3.9-6ubuntu1_i386.deb
dpkg -i ./gnome-orca_2.22.1-0ubuntu1_all.deb
dpkg -i ./gnome-panel-data_2.22.1.2-0ubuntu3_all.deb
dpkg -i ./gnome-screensaver_2.22.2-0ubuntu1_i386.deb
dpkg -i ./gnome-terminal-data_2.22.1-0ubuntu2_all.deb
dpkg -i ./gnome-volume-manager_2.22.1-1ubuntu5_i386.deb
dpkg -i ./gstreamer0.10-alsa_0.10.18-3_i386.deb
dpkg -i ./gstreamer0.10-gnomevfs_0.10.18-3_i386.deb
dpkg -i ./gstreamer0.10-tools_0.10.18-4ubuntu1_i386.deb
dpkg -i ./gstreamer0.10-plugins-base-apps_0.10.18-3_i386.deb
dpkg -i ./gstreamer0.10-plugins-good_0.10.7-3_i386.deb
dpkg -i ./gstreamer0.10-x_0.10.18-3_i386.deb
dpkg -i ./gtk2-engines_2.14.1-0ubuntu1_i386.deb
dpkg -i ./gtk2-engines-ubuntulooks_0.9.12-11_i386.deb
dpkg -i ./libgail18_1.22.1-0ubuntu1_i386.deb
dpkg -i ./libgail-common_1.22.1-0ubuntu1_i386.deb
dpkg -i ./libgtkhtml3.14-19_3.18.1-0ubuntu1_i386.deb
dpkg -i ./gtkhtml3.14_3.18.1-0ubuntu1_i386.deb
dpkg -i ./system-config-printer-common_0.7.81+svn1976-0ubuntu7_all.deb
dpkg -i ./hal-cups-utils_0.6.13+svn86-0ubuntu4_i386.deb
dpkg -i ./hotkey-setup_0.1-17ubuntu21_i386.deb
dpkg -i ./hplip-data_2.8.2-0ubuntu7_all.deb
dpkg -i ./human-icon-theme_0.28_all.deb
dpkg -i ./human-theme_0.16_all.deb
dpkg -i ./hwtest_0.1-0ubuntu7_all.deb
dpkg -i ./hwtest-gtk_0.1-0ubuntu7_all.deb
dpkg -i ./jockey-gtk_0.3.3-0ubuntu7_all.deb
dpkg -i ./jockey-common_0.3.3-0ubuntu7_all.deb
dpkg -i ./myspell-en-gb_2.4.0~m240-1ubuntu1_all.deb
dpkg -i ./myspell-en-us_2.4.0~m240-1ubuntu1_all.deb
dpkg -i ./myspell-en-za_2.4.0~m240-1ubuntu1_all.deb
dpkg -i ./openoffice.org-hyphenation_0.3_all.deb
dpkg -i ./openoffice.org-thesaurus-en-us_2.4.0~m240-1ubuntu1_all.deb
dpkg -i ./language-support-writing-en_8.04+20080410_all.deb
dpkg -i ./launchpad-integration_0.1.19_all.deb
dpkg -i ./mono-runtime_1.2.6+dfsg-6ubuntu3_i386.deb
dpkg -i ./mono-gac_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./mono-jit_1.2.6+dfsg-6ubuntu3_i386.deb
dpkg -i ./mono-common_1.2.6+dfsg-6ubuntu3_i386.deb
dpkg -i ./libmono-corlib1.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-system1.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libglib2.0-cil_2.12.0-2ubuntu1_i386.deb
dpkg -i ./libart2.0-cil_2.20.0-2ubuntu1_i386.deb
dpkg -i ./libavahi-ui0_0.6.22-2ubuntu4_i386.deb
dpkg -i ./libtrackerclient0_0.6.6-0ubuntu3_i386.deb
dpkg -i ./libtracker-gtk0_0.6.6-0ubuntu3_i386.deb
dpkg -i ./tracker-search-tool_0.6.6-0ubuntu3_i386.deb
dpkg -i ./libexempi3_1.99.9-1_i386.deb
dpkg -i ./tracker_0.6.6-0ubuntu3_i386.deb
dpkg -i ./libdeskbar-tracker_0.6.6-0ubuntu3_all.deb
dpkg -i ./libdirectfb-1.0-0_1.0.1-7ubuntu3_i386.deb
dpkg -i ./libedataserverui1.2-8_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libeel2-data_2.22.1-0ubuntu1_all.deb
dpkg -i ./libeel2-2_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libexchange-storage1.2-3_2.22.1-0ubuntu1_i386.deb
dpkg -i ./libgconf2.0-cil_2.20.0-2ubuntu1_all.deb
dpkg -i ./libmono-cairo1.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libgtk2.0-cil_2.12.0-2ubuntu1_i386.deb
dpkg -i ./libglade2.0-cil_2.12.0-2ubuntu1_i386.deb
dpkg -i ./libgnome-media0_2.22.0-0ubuntu3_i386.deb
dpkg -i ./libgnome-vfs2.0-cil_2.20.0-2ubuntu1_i386.deb
dpkg -i ./libgnomeprint2.2-0_2.18.4-1_i386.deb
dpkg -i ./libgnomeprint2.2-data_2.18.4-1_all.deb
dpkg -i ./libgnome2.0-cil_2.20.0-2ubuntu1_i386.deb
dpkg -i ./libgnomevfs2-bin_2.22.0-2ubuntu1_i386.deb
dpkg -i ./libsmbclient_3.0.28a-1ubuntu4_i386.deb
dpkg -i ./libgnomevfs2-extra_2.22.0-2ubuntu1_i386.deb
dpkg -i ./libgphoto2-port0_2.4.0-8ubuntu6_i386.deb
dpkg -i ./libgphoto2-2_2.4.0-8ubuntu6_i386.deb
dpkg -i ./libgtk2.0-bin_2.12.9-2ubuntu2_all.deb
dpkg -i ./libgtksourceview2.0-common_2.2.1-1_all.deb
dpkg -i ./libgtksourceview2.0-0_2.2.1-1_i386.deb
dpkg -i ./libgvfscommon0_0.2.3-0ubuntu1_i386.deb
dpkg -i ./liblaunchpad-integration0_0.1.16_i386.deb
dpkg -i ./libmono-sharpzip0.84-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-addins0.2-cil_0.3.1-4_all.deb
dpkg -i ./libmono-security1.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-data-tds1.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-system-data1.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-system-web1.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono0_1.2.6+dfsg-6ubuntu3_i386.deb
dpkg -i ./libmono1.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-addins-gui0.2-cil_0.3.1-4_all.deb
dpkg -i ./libmono-corlib2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-system2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-security2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-data-tds2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-sharpzip2.84-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-system-data2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-sqlite2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono-system-web2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmono2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
dpkg -i ./libmtp7_0.2.6.1-2ubuntu1_i386.deb
dpkg -i ./mysql-common_5.0.51a-3ubuntu5_all.deb
dpkg -i ./libmysqlclient15off_5.0.51a-3ubuntu5_i386.deb
dpkg -i ./libnm-glib0_0.6.6-0ubuntu5_i386.deb
dpkg -i ./libnm-util0_0.6.6-0ubuntu5_i386.deb
dpkg -i ./libpam-gnome-keyring_2.22.1-1_i386.deb
dpkg -i ./libpt-1.10.10-plugins-alsa_1.10.10-1ubuntu6_i386.deb
dpkg -i ./libpt-1.10.10-plugins-v4l_1.10.10-1ubuntu6_i386.deb
dpkg -i ./libpt-1.10.10-plugins-v4l2_1.10.10-1ubuntu6_i386.deb
dpkg -i ./libpt-1.10.10_1.10.10-1ubuntu6_i386.deb
dpkg -i ./libpulse0_0.9.10-1ubuntu1_i386.deb
dpkg -i ./libpulse-browse0_0.9.10-1ubuntu1_i386.deb
dpkg -i ./libpulsecore5_0.9.10-1ubuntu1_i386.deb
dpkg -i ./libsane_1.0.19-1ubuntu3_i386.deb
dpkg -i ./libscim8c2a_1.4.7-3ubuntu8_i386.deb
dpkg -i ./libx86-1_0.99-1.2ubuntu4_i386.deb
dpkg -i ./libusplash0_0.5.19_i386.deb
dpkg -i ./linux-restricted-modules-common_2.6.24.12-16.34_all.deb
dpkg -i ./mousetweaks_2.22.1-0ubuntu2_i386.deb
dpkg -i ./nautilus-cd-burner_2.22.1-0ubuntu1_i386.deb
dpkg -i ./nautilus-data_2.22.2-0ubuntu3_all.deb
dpkg -i ./network-manager_0.6.6-0ubuntu5_i386.deb
dpkg -i ./network-manager-gnome_0.6.6-0ubuntu2_i386.deb
dpkg -i ./pulseaudio_0.9.10-1ubuntu1_i386.deb
dpkg -i ./pulseaudio-esound-compat_0.9.10-1ubuntu1_i386.deb
dpkg -i ./pulseaudio-module-gconf_0.9.10-1ubuntu1_i386.deb
dpkg -i ./pulseaudio-module-hal_0.9.10-1ubuntu1_i386.deb
dpkg -i ./pulseaudio-utils_0.9.10-1ubuntu1_i386.deb
dpkg -i ./readahead_0.20050517.0220-0ubuntu13_i386.deb
dpkg -i ./smbclient_3.0.28a-1ubuntu4_i386.deb
dpkg -i ./samba-common_3.0.28a-1ubuntu4_i386.deb
dpkg -i ./scim_1.4.7-3ubuntu8_i386.deb
dpkg -i ./scim-gtk2-immodule_1.4.7-3ubuntu8_i386.deb
dpkg -i ./scim-modules-socket_1.4.7-3ubuntu8_i386.deb
dpkg -i ./seahorse_2.22.1-0ubuntu1_i386.deb
dpkg -i ./ssh-askpass-gnome_4.7p1-8ubuntu1_i386.deb
dpkg -i ./system-config-printer-gnome_0.7.81+svn1976-0ubuntu7_all.deb
dpkg -i ./system-tools-backends_2.6.0-0ubuntu6_i386.deb
dpkg -i ./tomboy_0.10.1-1_i386.deb
dpkg -i ./totem-common_2.22.1-0ubuntu2_all.deb
dpkg -i ./transmission-gtk_1.06-0ubuntu4_i386.deb
dpkg -i ./transmission-common_1.06-0ubuntu4_all.deb
dpkg -i ./tsclient_0.150-1ubuntu1_i386.deb
dpkg -i ./ubufox_0.5~rc1-0ubuntu1_all.deb
dpkg -i ./ubuntu-gdm-themes_0.29_all.deb
dpkg -i ./ubuntu-wallpapers_0.25_all.deb
dpkg -i ./ubuntu-artwork_41_all.deb
dpkg -i ./unzip_5.52-10ubuntu2_i386.deb
dpkg -i ./update-notifier-common_0.70.7_all.deb
dpkg -i ./update-notifier_0.70.7_i386.deb
dpkg -i ./usplash_0.5.19_i386.deb
dpkg -i ./usplash-theme-ubuntu_0.18_i386.deb
dpkg -i ./vinagre_0.5.1-0ubuntu1_i386.deb
dpkg -i ./vino_2.22.1-1_i386.deb
dpkg -i ./xutils_7.3+10ubuntu8_all.deb
dpkg -i ./x-ttcidfont-conf_27_all.deb
dpkg -i ./xorg_7.3+10ubuntu8_i386.deb
dpkg -i ./xscreensaver-data_5.04-4ubuntu1_i386.deb
dpkg -i ./xscreensaver-gl_5.04-4ubuntu1_i386.deb
dpkg -i ./zenity_2.22.1-1_i386.deb
dpkg -i ./brltty-x11_3.9-6ubuntu1_i386.deb
dpkg -i ./brltty_3.9-6ubuntu1_i386.deb
dpkg -i ./gnome-system-tools_2.22.0-0ubuntu7_i386.deb
dpkg -i ./libgweather-common_2.22.1.1-0ubuntu1_all.deb
dpkg -i ./liblircclient0_0.8.3~pre1-0ubuntu7_i386.deb
# Resolve dependencies left unset or broken packages.
apt-get install -f
#EOF

I saved this to a txt file and named it run. How do i run this text file on my system and with all deb files? And does it matter what i name it?

---

### Post by Pumalite on 2008-04-13
This might help:

'E. Go to the offline computer, plug the USB memory (or the media you used), and open a terminal. Go to the directory where the USB memory is mounted:
Code:

cd /media/disk

and run the script file you saved. If you have named it like "updates", run:
Code:

sudo bash updates

The script will run the "dpkg -i" commands to install the new packages. Don't panic if you see any dependencies problems while the script is executed. An "apt-get install -f" is executed in the end of the script. It will resolve all the dependencies and finish installing the packages that were left behind.'

---

### Post by OutCell on 2008-04-13
Thanks i will try that

---

### Post by OutCell on 2008-04-13
I get errors :(
> Errors were encountered while processing:
 ./libpt-1.10.10-plugins-alsa_1.10.10-1ubuntu6_i386.deb
 (--install):rocessing ./libpt-1.10.10-plugins-v4l_1.10.10-1ubuntu6_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libpt-1.10.10-plugins-v4l_1.10.10-1ubuntu6_i386.deb
 (--install):rocessing ./libpt-1.10.10-plugins-v4l2_1.10.10-1ubuntu6_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libpt-1.10.10-plugins-v4l2_1.10.10-1ubuntu6_i386.deb
 (--install):rocessing ./libpt-1.10.10_1.10.10-1ubuntu6_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libpt-1.10.10_1.10.10-1ubuntu6_i386.deb
 (--install):rocessing ./libpulse0_0.9.10-1ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libpulse0_0.9.10-1ubuntu1_i386.deb
 (--install):rocessing ./libpulse-browse0_0.9.10-1ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libpulse-browse0_0.9.10-1ubuntu1_i386.deb
 (--install):rocessing ./libpulsecore5_0.9.10-1ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libpulsecore5_0.9.10-1ubuntu1_i386.deb
 (--install):rocessing ./libsane_1.0.19-1ubuntu3_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libsane_1.0.19-1ubuntu3_i386.deb
 (--install):rocessing ./libscim8c2a_1.4.7-3ubuntu8_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libscim8c2a_1.4.7-3ubuntu8_i386.deb
 (--install):rocessing ./libx86-1_0.99-1.2ubuntu4_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libx86-1_0.99-1.2ubuntu4_i386.deb
 (--install):rocessing ./libusplash0_0.5.19_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libusplash0_0.5.19_i386.deb
 (--install):rocessing ./linux-restricted-modules-common_2.6.24.12-16.34_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./linux-restricted-modules-common_2.6.24.12-16.34_all.deb
 (--install):rocessing ./mousetweaks_2.22.1-0ubuntu2_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./mousetweaks_2.22.1-0ubuntu2_i386.deb
 (--install):rocessing ./nautilus-cd-burner_2.22.1-0ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./nautilus-cd-burner_2.22.1-0ubuntu1_i386.deb
 (--install):rocessing ./nautilus-data_2.22.2-0ubuntu3_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./nautilus-data_2.22.2-0ubuntu3_all.deb
 (--install):rocessing ./network-manager_0.6.6-0ubuntu5_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./network-manager_0.6.6-0ubuntu5_i386.deb
 (--install):rocessing ./network-manager-gnome_0.6.6-0ubuntu2_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./network-manager-gnome_0.6.6-0ubuntu2_i386.deb
 (--install):rocessing ./pulseaudio_0.9.10-1ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./pulseaudio_0.9.10-1ubuntu1_i386.deb
 (--install):rocessing ./pulseaudio-esound-compat_0.9.10-1ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./pulseaudio-esound-compat_0.9.10-1ubuntu1_i386.deb
 (--install):rocessing ./pulseaudio-module-gconf_0.9.10-1ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./pulseaudio-module-gconf_0.9.10-1ubuntu1_i386.deb
 (--install):rocessing ./pulseaudio-module-hal_0.9.10-1ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./pulseaudio-module-hal_0.9.10-1ubuntu1_i386.deb
 (--install):rocessing ./pulseaudio-utils_0.9.10-1ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./pulseaudio-utils_0.9.10-1ubuntu1_i386.deb
 (--install):rocessing ./readahead_0.20050517.0220-0ubuntu13_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./readahead_0.20050517.0220-0ubuntu13_i386.deb
 (--install):rocessing ./smbclient_3.0.28a-1ubuntu4_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./smbclient_3.0.28a-1ubuntu4_i386.deb
 (--install):rocessing ./samba-common_3.0.28a-1ubuntu4_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./samba-common_3.0.28a-1ubuntu4_i386.deb
 (--install):rocessing ./scim_1.4.7-3ubuntu8_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./scim_1.4.7-3ubuntu8_i386.deb
 (--install):rocessing ./scim-gtk2-immodule_1.4.7-3ubuntu8_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./scim-gtk2-immodule_1.4.7-3ubuntu8_i386.deb
 (--install):rocessing ./scim-modules-socket_1.4.7-3ubuntu8_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./scim-modules-socket_1.4.7-3ubuntu8_i386.deb
 (--install):rocessing ./seahorse_2.22.1-0ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./seahorse_2.22.1-0ubuntu1_i386.deb
 (--install):rocessing ./ssh-askpass-gnome_4.7p1-8ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./ssh-askpass-gnome_4.7p1-8ubuntu1_i386.deb
dpkg: error processing ./system-config-printer-gnome_0.7.81+svn1976-0ubuntu7_all (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./system-config-printer-gnome_0.7.81+svn1976-0ubuntu7_all.deb
 (--install):rocessing ./system-tools-backends_2.6.0-0ubuntu6_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./system-tools-backends_2.6.0-0ubuntu6_i386.deb
 (--install):rocessing ./tomboy_0.10.1-1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./tomboy_0.10.1-1_i386.deb
 (--install):rocessing ./totem-common_2.22.1-0ubuntu2_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./totem-common_2.22.1-0ubuntu2_all.deb
 (--install):rocessing ./transmission-gtk_1.06-0ubuntu4_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./transmission-gtk_1.06-0ubuntu4_i386.deb
 (--install):rocessing ./transmission-common_1.06-0ubuntu4_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./transmission-common_1.06-0ubuntu4_all.deb
 (--install):rocessing ./tsclient_0.150-1ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./tsclient_0.150-1ubuntu1_i386.deb
 (--install):rocessing ./ubufox_0.5~rc1-0ubuntu1_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./ubufox_0.5~rc1-0ubuntu1_all.deb
 (--install):rocessing ./ubuntu-gdm-themes_0.29_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./ubuntu-gdm-themes_0.29_all.deb
 (--install):rocessing ./ubuntu-wallpapers_0.25_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./ubuntu-wallpapers_0.25_all.deb
 (--install):rocessing ./ubuntu-artwork_41_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./ubuntu-artwork_41_all.deb
 (--install):rocessing ./unzip_5.52-10ubuntu2_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./unzip_5.52-10ubuntu2_i386.deb
 (--install):rocessing ./update-notifier-common_0.70.7_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./update-notifier-common_0.70.7_all.deb
 (--install):rocessing ./update-notifier_0.70.7_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./update-notifier_0.70.7_i386.deb
 (--install):rocessing ./usplash_0.5.19_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./usplash_0.5.19_i386.deb
 (--install):rocessing ./usplash-theme-ubuntu_0.18_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./usplash-theme-ubuntu_0.18_i386.deb
 (--install):rocessing ./vinagre_0.5.1-0ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./vinagre_0.5.1-0ubuntu1_i386.deb
 (--install):rocessing ./vino_2.22.1-1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./vino_2.22.1-1_i386.deb
 (--install):rocessing ./xutils_7.3+10ubuntu8_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./xutils_7.3+10ubuntu8_all.deb
 (--install):rocessing ./x-ttcidfont-conf_27_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./x-ttcidfont-conf_27_all.deb
 (--install):rocessing ./xorg_7.3+10ubuntu8_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./xorg_7.3+10ubuntu8_i386.deb
 (--install):rocessing ./xscreensaver-data_5.04-4ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./xscreensaver-data_5.04-4ubuntu1_i386.deb
 (--install):rocessing ./xscreensaver-gl_5.04-4ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./xscreensaver-gl_5.04-4ubuntu1_i386.deb
 (--install):rocessing ./zenity_2.22.1-1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./zenity_2.22.1-1_i386.deb
 (--install):rocessing ./brltty-x11_3.9-6ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./brltty-x11_3.9-6ubuntu1_i386.deb
 (--install):rocessing ./brltty_3.9-6ubuntu1_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./brltty_3.9-6ubuntu1_i386.deb
 (--install):rocessing ./gnome-system-tools_2.22.0-0ubuntu7_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./gnome-system-tools_2.22.0-0ubuntu7_i386.deb
 (--install):rocessing ./libgweather-common_2.22.1.1-0ubuntu1_all.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./libgweather-common_2.22.1.1-0ubuntu1_all.deb
 (--install):rocessing ./liblircclient0_0.8.3~pre1-0ubuntu7_i386.deb
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./liblircclient0_0.8.3~pre1-0ubuntu7_i386.deb
] is not known. option '


I saved the script on a windows machine, and i didn't understand this part:
> # If you used Windows to save this script, please open it with:
#
# "nano script_name"
#
# Press Ctrl-o and then press Alt-d to change from:
#
# "File Name to Write [DOS Format]:"
#
# To:
#
# "File Name to Write:"

I think the problem is from this, can anyone please help me out and explain this..

---

### Post by Pumalite on 2008-04-13
Use the nano editor and change the name of the file to one appropriate to Linux (not DOS)

---

