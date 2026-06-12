---
title: "Problems in upgrading Ubuntu 10.04 to 10.10"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by rajulbhavsar on 2010-11-28
I have perfectly working Ubuntu 10.04 on my Dell Vostro 1500 laptop. But, yesterday I upgraded it to Ubuntu 10.10. There were various error messages during upgrade process, but it showed that I can continue without certain package. But, after restarting the laptop, I didn't found the new kernel entry in the GRUB. So, I continued with booting using older kernel version. It showed that ubuntu is booting but after sometime screen went totally blank. I even tried to boot into recovery mode, but faced same problem.

Then I booted with live CD, and chroot to the root folder of ubuntu on my HDD. After running command "dpkg --configure -a" I got error messages which are stored in attached file error-msg.txt.

I cannot format the linux partition for a clean install. Please suggest solution for either recovery of 10.10 or restoration of 10.04.

---

### Post by sikander3786 on 2010-11-28
Welcome to the forums :-)

Here goes your error-msg.txt.

```
root@ubuntu:/# dpkg --configure -a
warning, in file '/var/lib/dpkg/available' near line 4403 package 'ymessenger':
 error in Version string '1.0.4_1': invalid character in version number
dpkg: dependency problems prevent configuration of mono-2.0-gac:
 mono-2.0-gac depends on libc6 (>= 2.12) | libc6.1 (>= 2.12) | libc0.1 (>= 2.12); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.5.
  Package libc6.1 is not installed.
  Package libc0.1 is not installed.
dpkg: error processing mono-2.0-gac (--configure):
 dependency problems - leaving unconfigured
Setting up debconf (1.5.28ubuntu4) ...
debconf: Problem setting up the database defined by stanza 3 of /etc/debconf.conf.
Can't locate Debconf/DbDriver/File.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 15) line 2, <DEBCONF_CONFIG> chunk 3.
BEGIN failed--compilation aborted at (eval 15) line 2, <DEBCONF_CONFIG> chunk 3.
dpkg: error processing debconf (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of memtest86+:
 memtest86+ depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing memtest86+ (--configure):
 dependency problems - leaving unconfigured
Setting up dash (0.5.5.1-7ubuntu1) ...
debconf: Problem setting up the database defined by stanza 3 of /etc/debconf.conf.
Can't locate Debconf/DbDriver/File.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 15) line 2, <DEBCONF_CONFIG> chunk 3.
BEGIN failed--compilation aborted at (eval 15) line 2, <DEBCONF_CONFIG> chunk 3.
dpkg: error processing dash (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mono-csharp-shell:
 mono-csharp-shell depends on libc6 (>= 2.12) | libc6.1 (>= 2.12) | libc0.1 (>= 2.12); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.5.
  Package libc6.1 is not installed.
  Package libc0.1 is not installed.
dpkg: error processing mono-csharp-shell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of man-db:
 man-db depends on debconf (>= 1.2.0) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing man-db (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dbg:
 libc6-dbg depends on libc6 (= 2.12.1-0ubuntu9); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.5.
dpkg: error processing libc6-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam0g:
 libpam0g depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing libpam0g (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.35-23-generic (2.6.35-23.40) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
/etc/kernel/header_postinst.d/dkms: line 7: /dev/null: Permission denied
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mono-gac:
 mono-gac depends on mono-2.0-gac (= 2.6.7-3ubuntu1); however:
  Package mono-2.0-gac is not configured yet.
dpkg: error processing mono-gac (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-posix2.0-cil:
 libmono-posix2.0-cil depends on libc6 (>= 2.12) | libc6.1 (>= 2.12) | libc0.1 (>= 2.12); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.5.
  Package libc6.1 is not installed.
  Package libc0.1 is not installed.
dpkg: error processing libmono-posix2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on man-db (>= 2.5.1-1); however:
  Package man-db is not configured yet.
dpkg: error processing debhelper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-inetd:
 update-inetd depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing update-inetd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssl-cert:
 ssl-cert depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing ssl-cert (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.12.1-0ubuntu9); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.5.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libssl0.9.8:
 libssl0.9.8 depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing libssl0.9.8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl0.9.8 (>= 0.9.8m-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing openssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of byobu:
 byobu depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing byobu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sysv-rc:
 sysv-rc depends on debconf | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing sysv-rc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tzdata-java:
 tzdata-java depends on tzdata (= 2010o-0ubuntu0.10.10); however:
  Version of tzdata on system is 2010l-1.
dpkg: error processing tzdata-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on man-db; however:
  Package man-db is not configured yet.
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-smbpass:
 libpam-smbpass depends on libpam0g (>= 0.99.7.1); however:
  Package libpam0g is not configured yet.
dpkg: error processing libpam-smbpass (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tzdata:
 tzdata depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing tzdata (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libvirtodbc0:
 libvirtodbc0 depends on libssl0.9.8 (>= 0.9.8m-1); however:
  Package libssl0.9.8 is not configured yet.
 libvirtodbc0 depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing libvirtodbc0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-amd64:
 libc6-amd64 depends on libc6 (= 2.12.1-0ubuntu9); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.5.
dpkg: error processing libc6-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc-dev-bin:
 libc-dev-bin depends on libc6 (>> 2.12); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.5.
dpkg: error processing libc-dev-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dhcp3-client:
 dhcp3-client depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing dhcp3-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libslp1:
 libslp1 depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing libslp1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwvstreams4.6-extras:
 libwvstreams4.6-extras depends on libpam0g (>= 0.99.7.1); however:
  Package libpam0g is not configured yet.
 libwvstreams4.6-extras depends on libssl0.9.8 (>= 0.9.8m-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libwvstreams4.6-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on ure (>= 1.6.1); however:
  Version of ure on system is 1.6.0+OOo3.2.0-7ubuntu4.1.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdns66:
 libdns66 depends on libssl0.9.8 (>= 0.9.8m-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libdns66 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on libpam0g (>= 0.99.7.1); however:
  Package libpam0g is not configured yet.
dpkg: error processing winbind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tasksel:
 tasksel depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
 tasksel depends on debconf (>= 1.5.5) | cdebconf (>= 0.106); however:
  Package debconf is not configured yet.
  Package cdebconf is not installed.
dpkg: error processing tasksel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gbrainy:
 gbrainy depends on libc6 (>= 2.12) | libc6.1 (>= 2.12) | libc0.1 (>= 2.12); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.5.
  Package libc6.1 is not installed.
  Package libc0.1 is not installed.
 gbrainy depends on libmono-posix2.0-cil (>= 2.4); however:
  Package libmono-posix2.0-cil is not configured yet.
 gbrainy depends on mono-csharp-shell (>= 1.0); however:
  Package mono-csharp-shell is not configured yet.
dpkg: error processing gbrainy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libncurses5-dev:
 libncurses5-dev depends on libc-dev; however:
  Package libc-dev is not installed.
  Package libc6-dev which provides libc-dev is not configured yet.
dpkg: error processing libncurses5-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtuoso-opensource-6.1-common:
 virtuoso-opensource-6.1-common depends on libssl0.9.8 (>= 0.9.8m-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing virtuoso-opensource-6.1-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstdc++6-4.3-dev:
 libstdc++6-4.3-dev depends on libc6-dev (>= 2.5); however:
  Package libc6-dev is not configured yet.
dpkg: error processing libstdc++6-4.3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sysinfo:
 sysinfo depends on libc6 (>= 2.12) | libc6.1 (>= 2.12) | libc0.1 (>= 2.12); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.5.
  Package libc6.1 is not installed.
  Package libc0.1 is not installed.
dpkg: error processing sysinfo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpt2.6.7:
 libpt2.6.7 depends on libssl0.9.8 (>= 0.9.8m-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libpt2.6.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm-guest-session:
 gdm-guest-session depends on gdm (>= 2.30.0-0ubuntu5); however:
  Package gdm is not configured yet.
dpkg: error processing gdm-guest-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtuoso-opensource-6.1-bin:
 virtuoso-opensource-6.1-bin depends on libssl0.9.8 (>= 0.9.8m-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing virtuoso-opensource-6.1-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sysstat:
 sysstat depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing sysstat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.6-dbg:
 python2.6-dbg depends on libssl0.9.8 (>= 0.9.8m-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing python2.6-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-management2.0-cil:
 libmono-management2.0-cil depends on libmono-posix2.0-cil (>= 2.4); however:
  Package libmono-posix2.0-cil is not configured yet.
dpkg: error processing libmono-management2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tasksel-data:
 tasksel-data depends on tasksel; however:
  Package tasksel is not configured yet.
dpkg: error processing tasksel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ppp:
 ppp depends on libpam0g (>= 0.99.7.1); however:
  Package libpam0g is not configured yet.
dpkg: error processing ppp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of debconf-utils:
 debconf-utils depends on debconf (>= 1.3.20); however:
  Package debconf is not configured yet.
dpkg: error processing debconf-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-common:
 libpango1.0-common depends on debconf | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing libpango1.0-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-bad:
 gstreamer0.10-plugins-bad depends on libssl0.9.8 (>= 0.9.8m-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-bad (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.2; however:
  Package wine1.2 is not installed.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 mono-2.0-gac
 debconf
 memtest86+
 dash
 mono-csharp-shell
 gdm
 man-db
 libc6-dbg
 libpam0g
 linux-headers-2.6.35-23-generic
 mono-gac
 libmono-posix2.0-cil
 debhelper
 update-inetd
 ssl-cert
 libc6-dev
 libssl0.9.8
 openssl
 byobu
 sysv-rc
 tzdata-java
 ubuntu-standard
 libpam-smbpass
 tzdata
 libvirtodbc0
 libc6-amd64
 libc-dev-bin
 dhcp3-client
 libslp1
 libwvstreams4.6-extras
 openoffice.org-base
 libdns66
 winbind
 tasksel
 gbrainy
 libncurses5-dev
 virtuoso-opensource-6.1-common
 libstdc++6-4.3-dev
 sysinfo
 libpt2.6.7
 gdm-guest-session
 virtuoso-opensource-6.1-bin
 sysstat
 python2.6-dbg
 libmono-management2.0-cil
 tasksel-data
 ppp
 debconf-utils
 libpango1.0-common
 gstreamer0.10-plugins-bad
 wine
Processing was halted because there were too many errors.

```

You need to copy/paste the text from your terminal straight into your post and wrap that output with code tags # from the post menu. You don't need to attach the file.

Now back to the original issue, please try this command and post the output.

```
sudo apt-get install -f
```

---

### Post by rajulbhavsar on 2010-11-28
the output of the command  "apt-get install -f" (without sudo) is

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-fstab libglitz-glx1 realpath libxcb-render-util0 libopenraw1 libindicator0 libopenrawgnome1 libbeagle1 libibus1 libevview2 libdns64 libboost-thread1.40.0 libdvbpsi5
  libgnome-bluetooth7 liblzma1 libavutil-extra-49 libx264-85 libdirectfb-1.2-0 libprotobuf5 liblouis0 libpoppler5 libgirepository1.0-0 libimobiledevice0 libglitz1
  libevdocument2 libmagickcore2 libmagick++2 libgdata6 firefox-3.0 firefox-3.5 libappindicator0 libmpfr1ldbl libmagickwand2 liboobs-1-4-dbg liboobs-1-4 libmodplug0c2
  libclalsadrv1 libvala0 libebml0 libboost-system1.40.0 libprotoc5 libestools1.2 libmpcdec3 libavahi-core6 libmatroska0 libgupnp-igd-1.0-2 libpoppler-glib4 libgpgme++2
  libntfs-3g75
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6 linux-image-2.6.35-23-generic openssh-server samba tzdata ure wine1.2 xserver-xorg
Suggested packages:
  glibc-doc linux-doc-2.6.35 linux-source-2.6.35 linux-tools rssh molly-guard openssh-blacklist openssh-blacklist-extra openbsd-inetd inet-superserver smbldap-tools ldb-tools
  cli-uno-bridge
Recommended packages:
  winetricks wisotool
The following NEW packages will be installed:
  linux-image-2.6.35-23-generic
The following packages will be upgraded:
  libc6 openssh-server samba tzdata ure wine1.2 xserver-xorg
7 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1511 not fully installed or removed.
Need to get 0B/58.7MB of archives.
After this operation, 112MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tzdata libc6 ure wine1.2 openssh-server linux-image-2.6.35-23-generic samba xserver-xorg
Install these packages without verification [y/N]? y
E: Could not perform immediate configuration on already unpacked 'util-linux'.Please see man 5 apt.conf under APT::Immediate-Configure for details.

```

---

### Post by sikander3786 on 2010-11-28
Edit your sources.list by,

```
gedit /etc/apt/sources.list
```

Change all entries from Lucid to Maverick, close and save and then

```
apt-get dist-upgrade
```

And the only way out is to upgrade to Maverick. No way you can drop back to Lucid now.

If you are unsure about sources.list, please post the output of following command to let us take a look on that.

```
cat /etc/apt/sources.list
```

---

### Post by rajulbhavsar on 2010-11-28
sources.list is already set for maverick

```
deb http://archive.ubuntu.com/ubuntu/ maverick main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ maverick main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ maverick-security universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ maverick-security universe main multiverse restricted #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ maverick-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ maverick-updates universe main multiverse restricted #Added by software-properties
# deb http://download.virtualbox.org/virtualbox/debian maverick non-free # disabled on upgrade to maverick

# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

deb http://archive.ubuntu.com/ubuntu/ maverick-backports universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ maverick-backports universe main multiverse restricted #Added by software-properties
# deb http://apt.wicd.net gutsy extras
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository

```

---

### Post by sikander3786 on 2010-11-28
> **rajulbhavsar said:**
> sources.list is already set for maverick

```
deb http://archive.ubuntu.com/ubuntu/ maverick main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ maverick main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ maverick-security universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ maverick-security universe main multiverse restricted #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ maverick-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ maverick-updates universe main multiverse restricted #Added by software-properties
# deb http://download.virtualbox.org/virtualbox/debian maverick non-free # disabled on upgrade to maverick

# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

deb http://archive.ubuntu.com/ubuntu/ maverick-backports universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ maverick-backports universe main multiverse restricted #Added by software-properties
# deb http://apt.wicd.net gutsy extras
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository

```
Go for the dist-upgrade command then. Hope that would fix the problem.

---

### Post by rajulbhavsar on 2010-11-28
no dist-upgrade is also not working. I think there is a dependency chain which is not satisfying. e.g. libc6 package seems to be broken, but i am not able to reinstall it. i could not figure out what is the main cause for unmet dependency.

output for command 

```
apt-get dist-upgrade
```

is 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 f-spot : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed or
                   libc6.1 (>= 2.12) but it is not installable or
                   libc0.1 (>= 2.12) but it is not installable
 gbrainy : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed or
                    libc6.1 (>= 2.12) but it is not installable or
                    libc0.1 (>= 2.12) but it is not installable
 libc-dev-bin : Depends: libc6 (> 2.12) but 2.11.1-0ubuntu7.5 is installed
 libc6 : Depends: libc-bin (= 2.11.1-0ubuntu7.5) but 2.12.1-0ubuntu9 is installed
         Recommends: libc6-i686
 libc6-amd64 : Depends: libc6 (= 2.12.1-0ubuntu9) but 2.11.1-0ubuntu7.5 is installed
 libc6-dbg : Depends: libc6 (= 2.12.1-0ubuntu9) but 2.11.1-0ubuntu7.5 is installed
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu9) but 2.11.1-0ubuntu7.5 is installed
 libldap-2.4-2 : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed
 libmono-posix2.0-cil : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed or
                                 libc6.1 (>= 2.12) but it is not installable or
                                 libc0.1 (>= 2.12) but it is not installable
 libmono-system1.0-cil : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed or
                                  libc6.1 (>= 2.12) but it is not installable or
                                  libc0.1 (>= 2.12) but it is not installable
 libmono-system2.0-cil : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed or
                                  libc6.1 (>= 2.12) but it is not installable or
                                  libc0.1 (>= 2.12) but it is not installable
 libnih1 : Depends: libc6 (> 2.12) but 2.11.1-0ubuntu7.5 is installed
 linux-image-generic : Depends: linux-image-2.6.35-23-generic but it is not installed
 mono-2.0-gac : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed or
                         libc6.1 (>= 2.12) but it is not installable or
                         libc0.1 (>= 2.12) but it is not installable
 mono-csharp-shell : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed or
                              libc6.1 (>= 2.12) but it is not installable or
                              libc0.1 (>= 2.12) but it is not installable
 mono-gmcs : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed or
                      libc6.1 (>= 2.12) but it is not installable or
                      libc0.1 (>= 2.12) but it is not installable
 openoffice.org-base : Depends: ure (>= 1.6.1) but 1.6.0+OOo3.2.0-7ubuntu4.1 is installed
 openoffice.org-core : Depends: ure (>= 1.6.1) but 1.6.0+OOo3.2.0-7ubuntu4.1 is installed
 openssh-server : Depends: openssh-client (= 1:5.3p1-3ubuntu4) but 1:5.5p1-4ubuntu4 is installed
 samba : Depends: samba-common (= 2:3.4.7~dfsg-1ubuntu3.2) but 2:3.5.4~dfsg-1ubuntu8 is installed
         Depends: libwbclient0 (= 2:3.4.7~dfsg-1ubuntu3.2) but 2:3.5.4~dfsg-1ubuntu8 is installed
 sysinfo : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed or
                    libc6.1 (>= 2.12) but it is not installable or
                    libc0.1 (>= 2.12) but it is not installable
 tomboy : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is installed or
                   libc6.1 (>= 2.12) but it is not installable or
                   libc0.1 (>= 2.12) but it is not installable
 tzdata-java : Depends: tzdata (= 2010o-0ubuntu0.10.10) but 2010l-1 is installed
 ure : Depends: uno-libs3 (= 1.6.0+OOo3.2.0-7ubuntu4.1) but 1.6.1+OOo3.2.1-7ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```

with -f option the output is 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-image-2.6.35-23-generic
The following packages will be upgraded:
  debconf hostname libc6 libpam-modules openssh-server samba tzdata ure wine1.2 x11-common xserver-xorg
11 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1511 not fully installed or removed.
Need to get 0B/59.5MB of archives.
After this operation, 111MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  debconf tzdata libc6 libpam-modules x11-common ure wine1.2 openssh-server linux-image-2.6.35-23-generic samba xserver-xorg hostname
Install these packages without verification [y/N]? y
E: Could not perform immediate configuration on already unpacked 'util-linux'.Please see man 5 apt.conf under APT::Immediate-Configure for details.
```

i tried to install util-linux but was not successful as again it has dependency problem

---

### Post by sikander3786 on 2010-11-28
> Here is where the problem comes in. Apt is looking for the util-linux package, which is part of upstart-job, but someone apparenlty forgot to write the code to tell apt-about this (whoops!)

So, you now need to install upstart-job by itself. By skipping this step you will get the error message when you try to run step 5: "E: Could not perform immediate configuration on 'util-linux'.Please see man 5 apt"

sudo apt-get install upstart-job

Now you can run apt-get dist-upgrade:

sudo apt-get dist-upgrade -y

Found in my notes. Hope it helps this time :-)

---

### Post by rajulbhavsar on 2010-11-28
output of command apt-get install upstart-job

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'upstart' instead of 'upstart-job'
upstart is already the newest version.
upstart set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 f-spot : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed or
                   libc6.1 (>= 2.12) but it is not installable or
                   libc0.1 (>= 2.12) but it is not installable
 gbrainy : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed or
                    libc6.1 (>= 2.12) but it is not installable or
                    libc0.1 (>= 2.12) but it is not installable
 libc-dev-bin : Depends: libc6 (> 2.12) but 2.11.1-0ubuntu7.5 is to be installed
 libc6 : Depends: libc-bin (= 2.11.1-0ubuntu7.5) but 2.12.1-0ubuntu9 is to be installed
         Recommends: libc6-i686
 libc6-amd64 : Depends: libc6 (= 2.12.1-0ubuntu9) but 2.11.1-0ubuntu7.5 is to be installed
 libc6-dbg : Depends: libc6 (= 2.12.1-0ubuntu9) but 2.11.1-0ubuntu7.5 is to be installed
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu9) but 2.11.1-0ubuntu7.5 is to be installed
 libldap-2.4-2 : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed
 libmono-posix2.0-cil : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed or
                                 libc6.1 (>= 2.12) but it is not installable or
                                 libc0.1 (>= 2.12) but it is not installable
 libmono-system1.0-cil : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed or
                                  libc6.1 (>= 2.12) but it is not installable or
                                  libc0.1 (>= 2.12) but it is not installable
 libmono-system2.0-cil : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed or
                                  libc6.1 (>= 2.12) but it is not installable or
                                  libc0.1 (>= 2.12) but it is not installable
 libnih1 : Depends: libc6 (> 2.12) but 2.11.1-0ubuntu7.5 is to be installed
 linux-image-generic : Depends: linux-image-2.6.35-23-generic but it is not going to be installed
 mono-2.0-gac : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed or
                         libc6.1 (>= 2.12) but it is not installable or
                         libc0.1 (>= 2.12) but it is not installable
 mono-csharp-shell : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed or
                              libc6.1 (>= 2.12) but it is not installable or
                              libc0.1 (>= 2.12) but it is not installable
 mono-gmcs : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed or
                      libc6.1 (>= 2.12) but it is not installable or
                      libc0.1 (>= 2.12) but it is not installable
 openoffice.org-base : Depends: ure (>= 1.6.1) but 1.6.0+OOo3.2.0-7ubuntu4.1 is to be installed
 openoffice.org-core : Depends: ure (>= 1.6.1) but 1.6.0+OOo3.2.0-7ubuntu4.1 is to be installed
 openssh-server : Depends: openssh-client (= 1:5.3p1-3ubuntu4) but 1:5.5p1-4ubuntu4 is to be installed
 sysinfo : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed or
                    libc6.1 (>= 2.12) but it is not installable or
                    libc0.1 (>= 2.12) but it is not installable
 tomboy : Depends: libc6 (>= 2.12) but 2.11.1-0ubuntu7.5 is to be installed or
                   libc6.1 (>= 2.12) but it is not installable or
                   libc0.1 (>= 2.12) but it is not installable
 tzdata-java : Depends: tzdata (= 2010o-0ubuntu0.10.10) but 2010l-1 is to be installed
 ure : Depends: uno-libs3 (= 1.6.0+OOo3.2.0-7ubuntu4.1) but 1.6.1+OOo3.2.1-7ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


this also does not resolve the dependency issue. this does not seem to be a circular dependency problem. so which is the main package creating the problem? i tried to install  libc-bin, which is needed for libc6, bu in vain.

also there seems to be problem with debconf as suggested by output of 
```
dpkg --configure -a
```

---

### Post by sikander3786 on 2010-11-28
Check if aptitude is installed and if installed, this might help.

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by rajulbhavsar on 2010-11-28
output of

```
aptitude update && aptitude safe-upgrade
```

```
The program 'aptitude' can be found in the following packages:
 * aptitude
 * aptitude-gtk
Try: apt-get install <selected package>

```

But when I try to install aptitude, the following message is displayed (dependency errors are not shown)

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.

```

So, I didn't understand what is the real situation ?

When I executed 
```
locate aptitude
```

it showed one of the location as

```
/usr/bin/aptitude
```

but on listing /usr/bin/ directory content, aptitude is not shown!!!!

---

### Post by rajulbhavsar on 2010-11-28
even executing command 

```
apt-get -f install -o APT::Immediate-Configure=0
```

have not helped

its output is as follows : 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-fstab libglitz-glx1 realpath libxcb-render-util0 libopenraw1 libindicator0 libopenrawgnome1 libbeagle1 libibus1 libevview2 libdns64 libboost-thread1.40.0 libdvbpsi5
  libgnome-bluetooth7 liblzma1 libavutil-extra-49 libx264-85 libdirectfb-1.2-0 libprotobuf5 liblouis0 libpoppler5 libgirepository1.0-0 libimobiledevice0 libglitz1
  libevdocument2 libmagickcore2 libmagick++2 libgdata6 firefox-3.0 firefox-3.5 libappindicator0 libmpfr1ldbl libmagickwand2 liboobs-1-4-dbg liboobs-1-4 libmodplug0c2
  libclalsadrv1 libvala0 libebml0 libboost-system1.40.0 libprotoc5 libestools1.2 libmpcdec3 libavahi-core6 libmatroska0 libgupnp-igd-1.0-2 libpoppler-glib4 libgpgme++2
  libntfs-3g75
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6 linux-image-2.6.35-23-generic openssh-server samba tzdata ure wine1.2 xserver-xorg
Suggested packages:
  glibc-doc linux-doc-2.6.35 linux-source-2.6.35 linux-tools rssh molly-guard openssh-blacklist openssh-blacklist-extra openbsd-inetd inet-superserver smbldap-tools ldb-tools
  cli-uno-bridge
Recommended packages:
  winetricks wisotool
The following NEW packages will be installed:
  linux-image-2.6.35-23-generic
The following packages will be upgraded:
  libc6 openssh-server samba tzdata ure wine1.2 xserver-xorg
7 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1511 not fully installed or removed.
Need to get 0B/58.7MB of archives.
After this operation, 112MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tzdata libc6 ure wine1.2 openssh-server linux-image-2.6.35-23-generic samba xserver-xorg
Install these packages without verification [y/N]? y
Reading changelogs... Done
debconf: Problem setting up the database defined by stanza 3 of /etc/debconf.conf.
Can't locate Debconf/DbDriver/File.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 15) line 2, <DEBCONF_CONFIG> chunk 3.
BEGIN failed--compilation aborted at (eval 15) line 2, <DEBCONF_CONFIG> chunk 3.
Can not write log, openpty() failed (/dev/pts not mounted?)
warning, in file '/var/lib/dpkg/available' near line 4403 package 'ymessenger':
 error in Version string '1.0.4_1': invalid character in version number
(Reading database ... 329727 files and directories currently installed.)
Preparing to replace tzdata 2010l-1 (using .../tzdata_2010o-0ubuntu0.10.10_all.deb) ...
Unpacking replacement tzdata ...
Preparing to replace libc6 2.11.1-0ubuntu7.5 (using .../libc6_2.12.1-0ubuntu9_i386.deb) ...
debconf: Problem setting up the database defined by stanza 3 of /etc/debconf.conf.
Can't locate Debconf/DbDriver/File.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 15) line 2, <DEBCONF_CONFIG> chunk 3.
BEGIN failed--compilation aborted at (eval 15) line 2, <DEBCONF_CONFIG> chunk 3.
dpkg: error processing /var/cache/apt/archives/libc6_2.12.1-0ubuntu9_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.12.1-0ubuntu9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

is there any expert who can help me in this problem? I am clueless now. I have searched many threads, but I am not able to get any solutions to my corrupt upgrade of Maverick.

---

### Post by Vitalius on 2011-01-22
I could break the similar dependency circle by following advice from [superuser]("http://superuser.com/questions/199582/apt-error-could-not-perform-immediate-configuration-on") and manually installing packages by runnning
```
sudo dpkg -i <list of packages with unmet dependencies>
```

---

