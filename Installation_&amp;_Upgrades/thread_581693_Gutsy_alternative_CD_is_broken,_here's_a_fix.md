---
title: "Gutsy alternative CD is broken, here's a fix"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by poetbeware on 2007-10-19
The instructions at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) say put the CD in and an application will magically appear to hold my hand through the upgrade. This doesn't happen.

The instructions say if the application doesn't magically appear, I should run 'gksu "sh /cdrom/cdromupgrade"', which doesn't work, for the very good reason that there's nothing in /cdrom.

I have a /media/Ubuntu 7.10 i386/ directory, but the cdromupgrade program can't cope with the spaces in the filename path.

If I understand correctly, no one will be able to upgrade using the alternate CD by following the official instructions.

Here is how I coped. Open a Terminal, type:

```

cd
ln -s /media/Ubuntu\ 7.10\ i386 cdrom
gksu "sh /home/$USER/cdrom/cdromupgrade"

```

That should launch everything correctly. I'll let you know if it actually worked after I finish the upgrade. :)

-Paul

---

### Post by poetbeware on 2007-10-19
Never mind, the Alternate CD is simply broken. If you want to upgrade to Gutsy, you'll have to use the network install. Which basically means you'll have to wait fifteen years for Ubuntu's servers to be able to handle the demand.

For the record, here's what the upgrade program told me:

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/s/shadow/passwd_4.0.18.1-9_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/p/pciutils/pciutils_2.2.4-1ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/p/procps/procps_3.2.7-3ubuntu5_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/taglib/libtag1c2a_1.4-8_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/w/wavpack/libwavpack1_4.41.0-1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/s/shared-mime-info/shared-mime-info_0.22-2ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/p/pwlib/libpt-1.10.0_1.10.10-0ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xterm/xterm_229-1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/u/ubuntu-artwork/ubuntu-artwork_38_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/p/poppler/libpoppler2_0.6-0ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/p/poppler/poppler-utils_0.6-0ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/s/sane-backends/libsane_1.0.19~cvs20070505-3ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/u/update-inetd/update-inetd_4.27-0.5_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/r/recode/librecode0_3.6-14_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/s/software-properties/software-properties-gtk_0.60_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/w/whois/whois_4.7.21_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/p/pilot-link/libpisock9_0.12.2-9ubuntu3_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/r/rss-glx/rss-glx_0.8.1-6ubuntu5_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/s/screen/screen_4.0.3-0.4ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/s/sound-juicer/sound-juicer_2.20.0-1ubuntu3_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/o/openssh/openssh-client_4.6p1-5build1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/s/system-config-printer/system-config-printer_0.7.75+svn1653-0ubuntu2_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/tangerine-icon-theme/tangerine-icon-theme_0.26_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/tsclient/tsclient_0.148-3ubuntu1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/u/usplash/libusplash0_0.5.7_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.9.3-2ubuntu1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xserver-xorg-video-newport/xserver-xorg-video-newport_0.2.1-2ubuntu1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xserver-xorg-video-glint/xserver-xorg-video-glint_1.1.1-6_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.7.195-1ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xorg/xserver-xorg_7.2-5ubuntu13_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xscreensaver/xscreensaver-gl_4.24-5ubuntu3_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/z/zenity/zenity_2.20.0-0ubuntu1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/w/wvstreams/libwvstreams4.3-base_4.3-0ubuntu6_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/w/wvstreams/libwvstreams4.3-extras_4.3-0ubuntu6_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/w/wvdial/wvdial_1.56-1.2ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/o/openoffice.org/openoffice.org-calc_2.3.0-1ubuntu5_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/o/openoffice.org/openoffice.org-writer_2.3.0-1ubuntu5_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/o/openoffice.org/openoffice.org-java-common_2.3.0-1ubuntu5_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/o/openoffice.org/openoffice.org-evolution_2.3.0-1ubuntu5_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/o/openoffice.org/openoffice.org-core_2.3.0-1ubuntu5_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/o/openoffice.org/python-uno_2.3.0-1ubuntu5_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/o/openoffice.org/openoffice.org-style-human_2.3.0-1ubuntu5_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/o/openoffice.org/openoffice.org-common_2.3.0-1ubuntu5_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/tzdata/tzdata_2007f-3ubuntu1_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/u/util-linux/util-linux_2.13-8ubuntu1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/u/util-linux/mount_2.13-8ubuntu1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/u/upstart/upstart_0.3.8-2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/ttf-arphic-uming/ttf-arphic-uming_0.1.20060928-2.1ubuntu1_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/u/ubuntu-docs/ubuntu-docs_7.10.4_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xfonts-terminus/console-terminus_4.20-5.1_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/v/vim/vim-tiny_7.1-056+2ubuntu2_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/w/wpasupplicant/wpasupplicant_0.6.0+0.5.8-0ubuntu1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/p/pppoeconf/pppoeconf_1.16ubuntu1_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/r/reiserfsprogs/reiserfsprogs_3.6.19-6_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/tracker/tracker_0.6.3-0ubuntu3_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/p/pidgin/pidgin-data_2.2.1-1ubuntu4_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/restricted/l/linux-restricted-modules-2.6.22/linux-restricted-modules-2.6.22-14-generic_2.6.22.4-14.9_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/p/pidgin/pidgin_2.2.1-1ubuntu4_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/tomboy/tomboy_0.8.0-1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/totem/totem-gstreamer_2.20.0-0ubuntu3_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/totem/totem_2.20.0-0ubuntu3_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/totem/totem-mozilla_2.20.0-0ubuntu3_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/tracker/tracker-search-tool_0.6.3-0ubuntu3_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/ttf-arabeyes/ttf-arabeyes_1.1-9_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/ttf-indic-fonts/ttf-indic-fonts-core_0.5.0-0ubuntu1_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/ttf-indic-fonts/ttf-malayalam-fonts_0.5.0-0ubuntu1_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/thaifonts-scalable/ttf-thai-tlwg_0.4.7-1_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/t/ttf-unfonts/ttf-unfonts-core_1.0.1-6ubuntu1_all.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xsane/xsane_0.99+0.991-3ubuntu5_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/x/xsane/xsane-common_0.99+0.991-3ubuntu5_all.deb MD5Sum mismatch

---

### Post by tmcmack on 2007-10-19
Does this mean that the alt CD is broken for a clean install as well (not upgrade)? 

I've tried to do a clean install from the Gutsy alt CD a few times on my old (pentium 2) desktop, using both the "install in text mode" and "install a command-line system" options, but either way the install fails. 

First error it gets to says  that it failed to install libslang2, but it lets me continue. Some time later, I get a debootstrap warning about a failure while configuring base packages. Finally, an error about being unable to install initramfs-tools. At this point, it's failed to install the base packages so it tells me to back up and repeat the step, but each time I get the same errors.

I'm fairly confident that the CD downloaded and burned correctly because I checked the MD5 sums (both for the iso and the individual files on the burned CD) as described in [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM").

Next step is to try the server install, but I thought that the server install would be similar to the command-line system option on the alt CD. Or I'll wait till fluxbuntu gutsy comes out; fluxbuntu dapper worked well on this old machine.

---

### Post by ianmidd on 2007-10-19
I had the same problem.  

Here is how I got it working:
[URL="http://ubuntuforums.org/showthread.php?t=580338&highlight=alternate+cd+spaces+upgrade"]
http://ubuntuforums.org/showthread.php?t=580338&highlight=alternate+cd+spaces+upgrade[/URL]

---

### Post by tmcmack on 2007-10-19
ianmidd, would the space-in-directory-name problem described in the post you linked to affect a completely fresh install from the alt CD?

---

### Post by Lacrimstein on 2007-10-19
> Does this mean that the alt CD is broken for a clean install as well (not upgrade)?

I've tried to do a clean install from the Gutsy alt CD a few times on my old (pentium 2) desktop, using both the "install in text mode" and "install a command-line system" options, but either way the install fails.

First error it gets to says that it failed to install libslang2, but it lets me continue. Some time later, I get a debootstrap warning about a failure while configuring base packages. Finally, an error about being unable to install initramfs-tools. At this point, it's failed to install the base packages so it tells me to back up and repeat the step, but each time I get the same errors.

I'm fairly confident that the CD downloaded and burned correctly because I checked the MD5 sums (both for the iso and the individual files on the burned CD) as described in HowToMD5SUM.

Next step is to try the server install, but I thought that the server install would be similar to the command-line system option on the alt CD. Or I'll wait till fluxbuntu gutsy comes out; fluxbuntu dapper worked well on this old machine.
__________________

No, the clean install works. Just installed it to another partition to check - works better than feisty for me :)

---

### Post by ianmidd on 2007-10-19
> **tmcmack said:**
> ianmidd, would the space-in-directory-name problem described in the post you linked to affect a completely fresh install from the alt CD?

I'm not sure, as I only did the upgrade from CD.

Although, I can't see the spaces causing an issue if you are booting from the CD.

---

