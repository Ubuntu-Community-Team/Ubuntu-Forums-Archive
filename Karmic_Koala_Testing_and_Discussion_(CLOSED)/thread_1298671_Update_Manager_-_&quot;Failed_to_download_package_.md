---
title: "Update Manager - &quot;Failed to download package files&quot;"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by StuM on 2009-10-23
Hey,

I've been running Karmic happily for the last few weeks, and due to running into no problems, I haven't been checking in with the latest developments of the beta.

But yesterday it struck me I hadn't seen the update manager for a while (which I've read today is a known bug), and forced a manual update.  The update was huge and most of the packages were downloaded successfully.  But I got a "Failed to download package files - Check your internet connection" error message.  I decided to leave it for a day in case some servers were down or something.  But today I am getting the same message.  Below is the text that accompanies the error.

I should point out that I'm no computer whizz, very much a front end user.  Reading the sticky on 'partial upgrades' I'm wondering if I may have done this on first install of Karmic.  If I've broke it, I'm thinking it might be best to do another fresh install.

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4~rc1-1ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.4~rc1-1ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.4~rc1-1ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_0.2.2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libs/libselinux/libselinux1_2.0.85-2ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysvinit-utils_2.87dsf-4ubuntu10_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysv-rc_2.87dsf-4ubuntu10_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu10_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/alsa-utils/alsa-utils_1.0.20-2ubuntu5_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.19.91.20091014-0ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-cups_3.9.8-1ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_9.10+20091010_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_9.10+20091010_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-14-generic_2.6.31-14.47_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-emailmerge_3.1.1-4ubuntu1_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_9.10.10_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_1.174_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.3.1+1403-0ubuntu26_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.3.1+1403-0ubuntu26_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.3.1+1403-0ubuntu26_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.3.1+1403-0ubuntu26_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-standard_1.174_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_1.9.3-0ubuntu2_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_1.9.3-0ubuntu2_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_1.9.3-0ubuntu2_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_1.9.3-0ubuntu2_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/byobu/byobu_2.38-0ubuntu2_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.8.4-0ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.8.4-0ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.8.4-0ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.8.4-0ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-wrapper_0.8.4-0ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.8.4-0ubuntu1_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/couchdb/couchdb-bin_0.10.0-0ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/empathy/libempathy30_2.28.0.1-1ubuntu6_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/empathy/libempathy-common_2.28.0.1-1ubuntu6_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/empathy/libempathy-gtk28_2.28.0.1-1ubuntu6_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/empathy/libempathy-gtk-common_2.28.0.1-1ubuntu6_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.28.0.1-1ubuntu6_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-doc_2.28.0.1-1ubuntu6_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument1_2.28.0-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevview1_2.28.0-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.28.0-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5-branding_3.5.3+build1+nobinonly-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5-gnome-support_3.5.3+build1+nobinonly-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5_3.5.3+build1+nobinonly-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox_3.5.3+build1+nobinonly-0ubuntu4_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-gnome-support_3.5.3+build1+nobinonly-0ubuntu4_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcalctool/gcalctool_5.28.0-0ubuntu3_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/usplash/libusplash0_0.5.44_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/usplash/usplash_0.5.44_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.28.0-0ubuntu5_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libx/libxklavier/libxklavier15_4.0-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.28.0-0ubuntu19_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.28.0-0ubuntu5_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.28.0-0ubuntu5_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.28.0-0ubuntu7_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/libgvfscommon0_1.4.0-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_1.4.0-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-backends_1.4.0-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-bin_1.4.0-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs_1.4.0-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.4.13_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.4.13_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-esound-compat_0.9.19-0ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-udev_0.9.19-0ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-gconf_0.9.19-0ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-utils_0.9.19-0ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-x11_0.9.19-0ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-bluetooth_0.9.19-0ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio_0.9.19-0ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse-mainloop-glib0_0.9.19-0ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse-browse0_0.9.19-0ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.19-0ubuntu2_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.23_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-14_2.6.31-14.47_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-14-generic_2.6.31-14.47_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.31-14.47_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers-173/nvidia-173-modaliases_173.14.20-0ubuntu3_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers-180/nvidia-185-modaliases_185.18.36-0ubuntu7_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers-96/nvidia-96-modaliases_96.43.13-0ubuntu4_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ure_1.5.1+OOo3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/uno-libs3_1.5.1+OOo3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_3.1.1-4ubuntu1_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_3.1.1-4ubuntu1_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_3.1.1-4ubuntu1_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.1.1-4ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/python-cupshelpers_1.1.12+git20090826-0ubuntu7_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.0.1-0ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_1.0.1-0ubuntu1_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.0.1-0ubuntu1_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.6-0ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.12.5-0ubuntu3_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_1.0_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-common_1.1.12+git20090826-0ubuntu7_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-gnome_1.1.12+git20090826-0ubuntu7_all.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-udev_1.1.12+git20090826-0ubuntu7_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-gabble/telepathy-gabble_0.8.6-1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.174_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_2.28.0-0ubuntu5_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.97~beta4-1ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.97~beta4-1ubuntu1_i386.deb 404  Not Found [IP: 194.169.254.10 80]
```p.s. I have a similar issue when trying to activate the proprietary Nvidia drivers from the Hardware drivers menu.

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-185_185.18.36-0ubuntu7_i386.deb 404  Not Found [IP: 194.***.***.10 80]
``` (I've asterisked some of the IP address above, not sure if that is mine, and if it is, whether it would be safe to post publically.

---

### Post by Lazy123 on 2009-10-23
Click "Check" and after that try to install updates again. You seem to have outdated package information because file
[http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4~rc1-1ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4~rc1-1ubuntu1_i386.deb) does not exist but there is a newer one [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4~rc2-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4~rc2-0ubuntu1_i386.deb)

Probably the same thing with the other files

---

### Post by linux-hack on 2009-10-23
are you behind a proxy ?

---

