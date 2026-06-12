---
title: "Upgrade Blocked"
date: 2024-10-08
forum: Installation &amp; Upgrades
---

### Post by CowDoctor on 2024-10-08
Dear Friends,
   I am trying to upgrade my computers to 24.04.  It was easy and successful on my desktop, but I get the following error message on the laptop:
 An error occurred, please run package manager from the right click menu or apt-get from a terminal to see what is wrong.
 The error message was: Error: Marking the upgrade (E:Internal Error, pkgProblemResolver::ResolveByKeep is looping on package gnome-settings-daemon:amd64.)’. This usually means that your installed packages have unmet dependencies.
  I am unable to do anything with this, evidently not sophisticated enough with commands to know how to proceed.  Can someone help?  Please.
Yours hopefully,
Joe

---

### Post by Bashing-om on 2024-10-08
CowDoctor -

Start this ball rolling -
Post back - between code tags - the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
To maintain the formatting.

[INDENT]see here what tale gets told
[/INDENT]

---

### Post by CowDoctor on 2024-10-08
Thank you.  Will try,

---

### Post by CowDoctor on 2024-10-08
sudo apt update
```

Hit:1 http://us.archive.ubuntu.com/ubuntu noble InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Hit:3 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease
Get:4 http://ppa.launchpad.net/system76-dev/stable/ubuntu noble InRelease [18.1 kB]
Hit:5 http://security.ubuntu.com/ubuntu noble-security InRelease
Get:6 https://esm.ubuntu.com/apps/ubuntu noble-apps-security InRelease [7,532 B]
Get:7 https://esm.ubuntu.com/apps/ubuntu noble-apps-updates InRelease [7,468 B]
Get:8 https://esm.ubuntu.com/infra/ubuntu noble-infra-security InRelease [7,462 B]
Get:9 https://esm.ubuntu.com/infra/ubuntu noble-infra-updates InRelease [7,461 B]
Fetched 174 kB in 7s (24.2 kB/s)                                               
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1989 packages can be upgraded. Run 'apt list --upgradable' to see them.


```

---

### Post by CowDoctor on 2024-10-08
When I run the update it is doing a whole lot of stuff.  Too much to copy, will be a while until it's done.  I hope this means the problem is solved.

---

### Post by CowDoctor on 2024-10-08
I mean upgrade.

---

### Post by Bashing-om on 2024-10-08
CowDoctor --

> 
 I hope this means the problem is solved.
I mean upgrade.


Your update output looks promising :D
Maybe - hope hope ===

what shows:
```

lsb_release -a
sudo apt -f install
sudo dpkg -C

```
If dpkg is all happy there will be no output - just a return to prompt.

-could be all there is to it-

---

### Post by CowDoctor on 2024-10-08
This is the final segment of the upgrade from the terminal
```

Installing grub to /boot/efi.
Installing for x86_64-efi platform.
Installation finished. No error reported.
Setting up python3-pymacaroons (0.13.0-6) ...
Setting up libexttextcat-2.0-0:amd64 (3.4.7-1build1) ...
Setting up libwoff1:amd64 (1.0.2-2build1) ...
Setting up dictionaries-common (1.29.7) ...
Setting up libmodule-implementation-perl (0.09-2) ...
Setting up python3-speechd (0.12.0~rc2-2build3) ...
Setting up libcharls2:amd64 (2.4.2-2build2) ...
Setting up fontconfig-config (2.15.0-1.1ubuntu2) ...
Installing new version of config file /etc/fonts/conf.d/README ...
Installing new version of config file /etc/fonts/fonts.conf ...
Setting up libboost-iostreams1.74.0:amd64 (1.74.0+ds1-23.1ubuntu3) ...
Setting up libpackage-stash-perl (0.40-1) ...
Setting up libimport-into-perl (1.002005-2) ...
Setting up libxtst6:amd64 (2:1.2.3-1.1build1) ...
Setting up libmoo-perl (2.005005-1) ...
Setting up libwebpdemux2:amd64 (1.3.2-0.4build3) ...
Setting up cron (3.0pl1-184ubuntu2) ...
Installing new version of config file /etc/init.d/cron ...
Setting up libcgi-pm-perl (4.63-1) ...
Setting up libkf5akonadicore-bin (4:23.08.5-0ubuntu3) ...
Setting up libkf5dbusaddons5:amd64 (5.115.0-0ubuntu5) ...
Setting up aspell-en (2020.12.07-0-1) ...
Setting up libxxf86dga1:amd64 (2:1.1.5-1build1) ...
Setting up libnet-http-perl (6.23-1) ...
Setting up xserver-xorg-video-ati (1:22.0.0-1build1) ...
Setting up liblist-someutils-perl (0.59-1) ...
Setting up fwupd-signed (1:1.1-4pop0~1643174914~24.04~f30da97~dev) ...
Setting up dpkg-repack (1.52) ...
Setting up debconf-i18n (1.5.86ubuntu1) ...
Setting up libnftnl11:amd64 (1.2.6-2build1) ...
Setting up mythes-en-us (1:24.2.1-1) ...
Setting up xinput (1.6.4-1build1) ...
Setting up libreoffice-style-tango (4:24.2.6-0ubuntu0.24.04.1) ...
Setting up libidn2-0:i386 (2.3.7-2build1) ...
Setting up libnet-dns-perl (1.44-1ubuntu1) ...
Setting up libmbim-proxy (1.31.2-0ubuntu3) ...
Setting up vim-tiny (2:9.1.0016-1ubuntu7.3) ...
Installing new version of config file /etc/vim/vimrc.tiny ...
update-alternatives: updating alternative /usr/bin/vim.tiny because link group e
x has changed slave links
update-alternatives: updating alternative /usr/bin/vim.tiny because link group v
i has changed slave links
update-alternatives: updating alternative /usr/bin/vim.tiny because link group v
iew has changed slave links
Setting up python3-click (8.1.6-2) ...
Setting up fonts-gujr (2:1.5) ...
Setting up hyphen-en-us (2.8.8-7build3) ...
Setting up shim-signed (1.58+15.8-0ubuntu1) ...
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
Installation finished. No error reported.
Setting up printer-driver-gutenprint (5.3.4.20220624T01008808d602-1build4) ...
Setting up openprinting-ppds (20230202-1) ...
Setting up python3-tz (2024.1-2) ...
Setting up libmono-corlib4.5-dll (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up dpkg-dev (1.22.6ubuntu6.1) ...
Setting up apt-clone (0.4.3+nmu2ubuntu2) ...
Setting up xcvt (0.1.2-1build1) ...
Setting up libthai0:amd64 (0.1.29-2build1) ...
Setting up libvorbisfile3:amd64 (1.3.7-1build3) ...
Setting up cracklib-runtime (2.9.6-5.1build2) ...
Removing obsolete conffile /etc/cron.daily/cracklib-runtime ...
Setting up libdata-validate-uri-perl (0.07-3) ...
Setting up python3-oauthlib (3.2.2-1) ...
Setting up python3-louis (3.29.0-1build1) ...
Setting up apt-config-icons-hidpi (1.0.2-1build6) ...
Setting up python3-secretstorage (3.3.3-3) ...
Setting up libnet-smtp-ssl-perl (1.04-2) ...
Setting up system-config-printer (1.5.18-1ubuntu9) ...
Installing new version of config file /etc/xdg/autostart/print-applet.desktop ..
.
Setting up libmailtools-perl (2.21-2) ...
Setting up dmraid (1.0.0.rc16-12ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Setting up fonts-liberation2 (1:2.1.5-3) ...
Setting up python3-pexpect (4.9-2) ...
Setting up python3-wadllib (1.3.6-5) ...
Setting up python3-debian (0.1.49ubuntu2) ...
Setting up python3-requests (2.31.0+dfsg-1ubuntu1) ...
Setting up python3-commandnotfound (23.04.0) ...
Setting up fonts-deva (2:1.4) ...
Setting up xserver-xorg-video-all (1:7.7+23ubuntu3) ...
Setting up ucf (3.0043+nmu1) ...
Setting up usbmuxd (1.1.1-5~exp3ubuntu2) ...
usbmuxd.service is a disabled or a static unit not running, not starting it.
Setting up libfile-desktopentry-perl (0.22-3) ...
Setting up libhdf4-0-alt:amd64 (4.2.16-4build1) ...
Setting up libconst-fast-perl (0.014-2) ...
Setting up libgvpr2:amd64 (2.42.2-9ubuntu0.1) ...
Setting up libnetfilter-conntrack3:amd64 (1.0.9-6build1) ...
Setting up libsord-0-0:amd64 (0.16.16-2build1) ...
Setting up libtiff6:amd64 (4.5.1+git230720-4ubuntu2.2) ...
Setting up xml-core (0.19) ...
Setting up libsratom-0-0:amd64 (0.6.16-1build1) ...
Setting up libmono-corlib4.5-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up language-selector-common (0.225) ...
Removing obsolete conffile /etc/fonts/conf.avail/30-cjk-aliases.conf ...
Removing obsolete conffile /etc/fonts/conf.avail/56-language-selector-ar.conf ..
.
Removing obsolete conffile /etc/fonts/conf.avail/64-language-selector-prefer.con
f ...
Removing obsolete conffile /etc/fonts/conf.avail/69-language-selector-ja.conf ..
.
Removing obsolete conffile /etc/fonts/conf.avail/69-language-selector-zh-cn.conf
 ...
Removing obsolete conffile /etc/fonts/conf.avail/69-language-selector-zh-hk.conf
 ...
Removing obsolete conffile /etc/fonts/conf.avail/69-language-selector-zh-mo.conf
 ...
Removing obsolete conffile /etc/fonts/conf.avail/69-language-selector-zh-sg.conf
 ...
Removing obsolete conffile /etc/fonts/conf.avail/69-language-selector-zh-tw.conf
 ...
Removing obsolete conffile /etc/fonts/conf.avail/99-language-selector-zh.conf ..
.
Setting up liblcms2-utils (2.14-2build1) ...
Setting up linux-image-6.8.0-76060800daily20240311-generic (6.8.0-76060800daily2
0240311.202403110203~1715181801~24.04~aba43ee~dev) ...
Setting up python3-paramiko (2.12.0-2ubuntu4) ...
Setting up libmoox-aliases-perl (0.001006-2) ...
Setting up libkf5completion5:amd64 (5.115.0-0ubuntu5) ...
Setting up libkf5sane5:amd64 (23.08.5-0ubuntu3) ...
Setting up python3-rfc3339 (1.1-4) ...
Setting up libdata-dpath-perl (0.59-1) ...
Setting up python3-macaroonbakery (1.3.4-1) ...
Setting up python3-lazr.restfulclient (0.14.6-1) ...
Setting up libb-hooks-endofscope-perl (0.28-1) ...
Setting up liblilv-0-0:amd64 (0.24.22-1build1) ...
Setting up libmono-accessibility4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up libfile-mimeinfo-perl (0.34-1) ...
Setting up libpaper1:amd64 (1.1.29build1) ...
Setting up libmono-security4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up libdebuginfod-common (0.190-1.1build4) ...
Setting up ca-certificates-mono (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up libemail-valid-perl (1.204-1) ...
Setting up libcgi-fast-perl (1:2.17-1) ...
Setting up libmono-i18n4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up python3-launchpadlib (1.11.0-6) ...
Created symlink /etc/systemd/user/timers.target.wants/launchpadlib-cache-clean.t
imer &#8594; /usr/lib/systemd/user/launchpadlib-cache-clean.timer.
Setting up libmono-system-numerics4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up ufw (0.36.2-6) ...
Installing new version of config file /etc/init.d/ufw ...
Setting up libmono-system-core4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up libpaper-utils (1.1.29build1) ...
Setting up python3-apport (2.28.1-0ubuntu3.1) ...
Setting up python3-requests-unixsocket (0.3.0-3ubuntu3) ...
Setting up libmono-webbrowser4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up unattended-upgrades (2.9.1+nmu4ubuntu1) ...
Setting up command-not-found (23.04.0) ...
Setting up libmono-i18n-west4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up libnamespace-clean-perl (0.27-2) ...
Setting up xserver-xorg (1:7.7+23ubuntu3) ...
Setting up xorg (1:7.7+23ubuntu3) ...
Setting up adwaita-icon-theme (46.0-1) ...
Setting up kbd (2.6.4-2ubuntu2) ...
Setting up console-setup-linux (1.226ubuntu1) ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-1.inc 
...
Installing new version of config file /etc/console-setup/compose.ISO-8859-13.inc
 ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-14.inc
 ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-15.inc
 ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-2.inc 
...
Installing new version of config file /etc/console-setup/compose.ISO-8859-3.inc 
...
Installing new version of config file /etc/console-setup/compose.ISO-8859-4.inc 
...
Installing new version of config file /etc/console-setup/compose.ISO-8859-7.inc 
...
Installing new version of config file /etc/console-setup/compose.ISO-8859-9.inc 
...
Installing new version of config file /etc/console-setup/compose.KOI8-R.inc ...
Installing new version of config file /etc/console-setup/compose.KOI8-U.inc ...
Installing new version of config file /etc/console-setup/compose.VISCII.inc ...
Installing new version of config file /etc/init.d/console-setup.sh ...
Installing new version of config file /etc/init.d/keyboard-setup.sh ...
Setting up libmono-system-configuration4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up console-setup (1.226ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Setting up libwww-perl (6.76-1) ...
Setting up aptdaemon (1.1.1+bzr982-0ubuntu44) ...
Setting up python3-aptdaemon (1.1.1+bzr982-0ubuntu44) ...
Setting up ubuntu-mono (24.04-0ubuntu1) ...
Setting up apport-core-dump-handler (2.28.1-0ubuntu3.1) ...
Installing new version of config file /etc/init.d/apport ...
Created symlink /etc/systemd/system/multi-user.target.wants/apport.service &#8594; /li
b/systemd/system/apport.service.
Setting up apport (2.28.1-0ubuntu3.1) ...
Installing new version of config file /etc/apport/crashdb.conf ...
Removing obsolete conffile /etc/apport/blacklist.d/README.blacklist ...
Removing obsolete conffile /etc/apport/blacklist.d/apport ...
apport-autoreport.service is a disabled or a static unit not running, not starti
ng it.
Setting up language-pack-en (1:24.04+20240817) ...
Setting up apport-gtk (2.28.1-0ubuntu3.1) ...
Setting up libmono-system-transactions4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up python3-aptdaemon.gtk3widgets (1.1.1+bzr982-0ubuntu44) ...
Setting up libmono-system-xml4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up light-themes (24.04-0ubuntu1) ...
Setting up liblwp-protocol-https-perl (6.13-1) ...
Setting up language-pack-gnome-en (1:24.04+20240817) ...
Setting up language-selector-gnome (0.225) ...
Setting up language-pack-en-base (1:24.04+20240817) ...
Generating locales (this might take a while)...
Generation complete.
Setting up libmono-system-enterpriseservices4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) 
...
Setting up libmono-system-runtime-serialization-formatters-soap4.0-cil (6.8.0.10
5+dfsg-3.6ubuntu2) ...
Setting up libmono-system-security4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up language-pack-gnome-en-base (1:24.04+20240817) ...
Setting up libmono-system-data4.0-cil (6.8.0.105+dfsg-3.6ubuntu2) ...
Setting up ubuntu-artwork (1:24.04-0ubuntu1) ...
Processing triggers for fontconfig (2.13.1-4.2ubuntu5) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.9.3-76060903-generic
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for cups (2.4.1op1-1ubuntu4.11) ...
Updating PPD files for foomatic-db-compressed-ppds ...
Updating PPD files for openprinting-ppds ...
Updating PPD files for gutenprint ...
Processing triggers for libglib2.0-0:amd64 (2.72.4-0ubuntu2.3) ...
Processing triggers for libc-bin (2.35-0ubuntu3.8) ...
Processing triggers for rsyslog (8.2112.0-2ubuntu2.2) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for ureadahead (0.100.0-21) ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.5+git20211018-1ubuntu3) 
...
update-initramfs: deferring update (trigger activated)
Processing triggers for libreoffice-common (1:7.3.7-0ubuntu0.22.04.7) ...
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for shared-mime-info (2.1-2) ...
Processing triggers for udev (249.11-0ubuntu3.11pop0~1704473387~22.04~3ce38bf~de
v) ...
Processing triggers for install-info (6.8-4build1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for sgml-base (1.31) ...
Setting up docbook-xml (4.5-12) ...
Processing triggers for ca-certificates (20240203) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
Updating Mono key store
Mono Certificate Store Sync - version 6.8.0.105
Populate Mono certificate store from a concatenated list of certificates.
Copyright 2002, 2003 Motus Technologies. Copyright 2004-2008 Novell. BSD license
d.

Importing into legacy system store:
I already trust 150, your new list has 146
4 previously trusted certificates were removed.
Certificate removed: C=TR, L=Ankara, O=E-Tugra EBG A.S., OU=E-Tugra Trust Center
, CN=E-Tugra Global Root CA RSA v3
Certificate removed: C=ES, CN=Autoridad de Certificacion Firmaprofesional CIF A6
2634068
Certificate removed: C=HK, O=Hongkong Post, CN=Hongkong Post Root CA 1
Certificate removed: C=TR, L=Ankara, O=E-Tu&#287;ra EBG Bili&#351;im Teknolojileri ve Hizm
etleri A.&#350;., OU=E-Tugra Sertifikasyon Merkezi, CN=E-Tugra Certification Authorit
y
Import process completed.

Importing into BTLS system store:
I already trust 149, your new list has 146
Certificate added: C=ES, CN=Autoridad de Certificacion Firmaprofesional CIF A626
34068
1 new root certificates were added to your trust store.
4 previously trusted certificates were removed.
Certificate removed: C=ES, CN=Autoridad de Certificacion Firmaprofesional CIF A6
2634068
Certificate removed: C=HK, O=Hongkong Post, CN=Hongkong Post Root CA 1
Certificate removed: C=TR, L=Ankara, O=E-Tugra EBG A.S., OU=E-Tugra Trust Center
, CN=E-Tugra Global Root CA RSA v3
Certificate removed: C=TR, L=Ankara, O=E-Tu&#287;ra EBG Bili&#351;im Teknolojileri ve Hizm
etleri A.&#350;., OU=E-Tugra Sertifikasyon Merkezi, CN=E-Tugra Certification Authorit
y
Import process completed.
Done
done.
Processing triggers for linux-image-6.9.3-76060903-generic (6.9.3-76060903.20240
5300957~1721174657~22.04~abb7c06~dev) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-6.9.3-76060903-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.9.3-76060903-generic
Found initrd image: /boot/initrd.img-6.9.3-76060903-generic
Found linux image: /boot/vmlinuz-6.8.0-76060800daily20240311-generic
Found initrd image: /boot/initrd.img-6.8.0-76060800daily20240311-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
Processing triggers for dictionaries-common (1.29.7) ...
aspell-autobuildhash: processing: en [en-common].
aspell-autobuildhash: processing: en [en-variant_0].
aspell-autobuildhash: processing: en [en-variant_1].
aspell-autobuildhash: processing: en [en-variant_2].
aspell-autobuildhash: processing: en [en-w_accents-only].
aspell-autobuildhash: processing: en [en-wo_accents-only].
aspell-autobuildhash: processing: en [en_AU-variant_0].
aspell-autobuildhash: processing: en [en_AU-variant_1].
aspell-autobuildhash: processing: en [en_AU-w_accents-only].
aspell-autobuildhash: processing: en [en_AU-wo_accents-only].
aspell-autobuildhash: processing: en [en_CA-variant_0].
aspell-autobuildhash: processing: en [en_CA-variant_1].
aspell-autobuildhash: processing: en [en_CA-w_accents-only].
aspell-autobuildhash: processing: en [en_CA-wo_accents-only].
aspell-autobuildhash: processing: en [en_GB-ise-w_accents-only].
aspell-autobuildhash: processing: en [en_GB-ise-wo_accents-only].
aspell-autobuildhash: processing: en [en_GB-ize-w_accents-only].
aspell-autobuildhash: processing: en [en_GB-ize-wo_accents-only].
aspell-autobuildhash: processing: en [en_GB-variant_0].
aspell-autobuildhash: processing: en [en_GB-variant_1].
aspell-autobuildhash: processing: en [en_US-w_accents-only].
aspell-autobuildhash: processing: en [en_US-wo_accents-only].
Processing triggers for linux-image-6.8.0-76060800daily20240311-generic (6.8.0-7
6060800daily20240311.202403110203~1715181801~24.04~aba43ee~dev) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-6.8.0-76060800daily20240311-generi
c
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.9.3-76060903-generic
Found initrd image: /boot/initrd.img-6.9.3-76060903-generic
Found linux image: /boot/vmlinuz-6.8.0-76060800daily20240311-generic
Found initrd image: /boot/initrd.img-6.8.0-76060800daily20240311-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.9.3-76060903-generic
Processing triggers for sgml-base (1.31) ...
Processing triggers for ca-certificates-java (20240118) ...
done.
joe@Bucky:~$ 



```

---

### Post by Bashing-om on 2024-10-08
CowDoctor --

That all seems well fine good and dandy
However
the proof in the pudding is revealed by the outputs on my last post.

[INDENT]Maybe all good - could be not so
[/INDENT]

---

### Post by CowDoctor on 2024-10-09
Bashing-om
Ooops.  Before I saw your post I went ahead and restarted the computer.  Aaargh!  It won't start.  Here are the error messages.
```

Gave up waiting for suspend/resume device
Gave up waiting for root file system device.  Common problems:
   -Boot args (cat/proc/cmdline)
      -Check root delay= (did the system wait long enough)
   -Missing modules (cat/ proc/modules; 1s /dev)
ALERT! UUID=6496c978-c968-4bdf-8a40-fb3f0b0233b does not exist. Dropping to a shell!

BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3.1) built in shell (ash)
Enter ´help' for a list of built in commands.
 (initramfs)

```
Not sure that needed to be in a code box but there is is.  Entering help yields a long string of commands I know nothing about. Sorry.  I tried running Ubunto in recovery mode and got the same results, after a lot of code I couldn't capture.  I believe it is waiting plenty long enough, as there is substatial lag time before these messages appear.
Any hope?

---

### Post by Bashing-om on 2024-10-09
CowDoctor

As the kernel tells us:
> 
ALERT! UUID=6496c978-c968-4bdf-8a40-fb3f0b0233b does not exist.


And we can surmise that a incorrect UUID is in the mounting file /etc/fstab . 
The easiest way I can think of to check is to boot a liveUSB to "try Ubunu" mode, activate a terminal interface, run terminal command:
```

sudo blkid

```
and then >
open the file manger and mount the root partition of the install and compare these UUID's in the /etc/fstab file.

Remember to UNmount that root partition prior to closing out the file manager !

[INDENT]seems a likely place to look
[/INDENT]

---

### Post by CowDoctor on 2024-10-10
More information and news.  I can get it to load using the second recovery mode option.  It shows a whole lot of code doing this, which I don't know how to capture as it flies by and then disappears right away.  Once up and running, however, if I reboot or power it off and turn it one again, I get the message as above, no start up.  I then have to do a forced shut down by holding the power button down.  Once I do that, I can get  the menu that leads to the recovery mode that works.  I  haven't yet done a lot of exploration to see if everything is working OK, but at least some do.  It tells me I am running 24.04. not the previous version.  I presume that is good.  I have run all the seemingly relevant commands available on the recovery mode without effect.
Functional, perhaps, but certainly not ideal.  Any ideas?
Yours in hope,
Joe

---

### Post by CowDoctor on 2024-10-10
Oh, I missed your last message.  I kept looking every few hours but it didn't show up until I sent the last message.  What?   Anyway, does the news above change anything.  The only USB I have is for a previous version.  Will that work or should I make a new one .... and how do I get it to boot from the USB?  I tried that but couldn't find a way to it.  Sorry to be so dense, and thanks for all your help.j
Yours apologetically,
Joe

---

### Post by Bashing-om on 2024-10-10
CowDoctor - 

Yeah- for what we are doing a previous version will serve.
As to how to boot the USB - can not guide much there as each and every manufacturer implements their Bios wares differently.

In genera, though, one must set in the Bios firmware to boot the USB as the 1st choice.

As to the why you are able to boot recovery in an older kernel - that awaits discovery !

[INDENT]it is in the process, somewhere
[/INDENT]

---

### Post by CowDoctor on 2024-10-11
Bashing-om,
Thank you.  Can I run that blkid from a terminal once I get the laptop running from the recovery option?  And, sorry, I need a little help with how to mount the root partition of the install.  Where do I find that.  I'll look around and see if I can figure it out.  The laptop is from System 76 if that is of any use.  You have been very kind to me.  Thank you.  There are a lot of mysteries here, and I now wish I had recorded some of the earlier error messages when I was trying to install the new update.
Yours gratefully,
Joe

---

### Post by CowDoctor on 2024-10-11
Would there be any point in just downloading it again?

---

### Post by Bashing-om on 2024-10-11
CowDoctor --

Yeah can run lsblkid from any booted source - the result will be the same.
As you can boot a recovery console one can read the fstab file directly.
```

cat /etc/fstab

```

as to learning a new operating system - can be daunting but the rewards are vastly worth the effort. Believe me we understand what new feels like - never ever feel reluctance to ask anything ! ; the only dumb question is the one you do not ask -- All here are here to help. We get ya over the rough spots :)

Presently; all we want is for the upgrade to boot :P

[INDENT]we can do that
[/INDENT]

---

### Post by CowDoctor on 2024-10-11
Thank you.  Will get to work on it.

---

### Post by CowDoctor on 2024-10-12
Here is a screenshot of the results of blkid 
[IMG]pictures/screenshots/Screenshot from 2024-10-12 16-07-06R.png[/IMG]
Hope that worked.  The UUID is the same as the one  it says can't be found when I try to boot normally.  I did omit a character when I first sent you that message.
I can't seem to figure out how to mount the root partition.
Yours helplessly,
Joe

---

### Post by CowDoctor on 2024-10-12
I can't seem to send the screenshot.  Do I need to manually enter all that information?

---

### Post by CowDoctor on 2024-10-12
[IMG]https://ubuntuforums.org/image/jpeg;base64,/9j/4AAQSkZJRgABAQIAHAAcAAD/4QoyRXhpZgAASUkqAAgAAAAHABIBAwABAAAAAQAAABoBBQABAAAAYgAAABsBBQABAAAAagAAACgBAwABAAAAAwAAADEBAgANAAAAcgAAADIBAgAUAAAAgAAAAGmHBAABAAAAlAAAAKYAAAA3AgAAFAAAADcCAAAUAAAAR0lNUCAyLjEwLjMwAAAyMDI0OjEwOjEyIDE2OjU3OjQyAAEAAaADAAEAAAABAAAAAAAAAAkA/gAEAAEAAAABAAAAAAEEAAEAAAAAAQAAAQEEAAEAAAAZAAAAAgEDAAMAAAAYAQAAAwEDAAEAAAAGAAAABgEDAAEAAAAGAAAAFQEDAAEAAAADAAAAAQIEAAEAAAAeAQAAAgIEAAEAAAAMCQAAAAAAAAgACAAIAP/Y/ AAEEpGSUYAAQEAAAEAAQAA/9sAQwAIBgYHBgUIBwcHCQkICgwUDQwLCwwZEhMPFB0aHx4dGhwcICQuJyAiLCMcHCg3KSwwMTQ0NB8nOT04MjwuMzQy/9sAQwEJCQkMCwwYDQ0YMiEcITIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIy/8AAEQgAGQEAAwEiAAIRAQMRAf/EAB8AAAEFAQEBAQEBAAAAAAAAAAABAgMEBQYHCAkKC//EALUQAAIBAwMCBAMFBQQEAAABfQECAwAEEQUSITFBBhNRYQcicRQygZGhCCNCscEVUtHwJDNicoIJChYXGBkaJSYnKCkqNDU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6g4SFhoeIiYqSk5SVlpeYmZqio6Slpqeoqaqys7S1tre4ubrCw8TFxsfIycrS09TV1tfY2drh4uPk5ebn6Onq8fLz9PX29/j5 v/EAB8BAAMBAQEBAQEBAQEAAAAAAAABAgMEBQYHCAkKC//EALURAAIBAgQEAwQHBQQEAAECdwABAgMRBAUhMQYSQVEHYXETIjKBCBRCkaGxwQkjM1LwFWJy0QoWJDThJfEXGBkaJicoKSo1Njc4OTpDREVGR0hJSlNUVVZXWFlaY2RlZmdoaWpzdHV2d3h5eoKDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uLj5OXm5 jp6vLz9PX29/j5 v/aAAwDAQACEQMRAD8A88tdMkuiDJDI8zSHf 92Eckc568hqJtGxJJHHbNvWEykeeMKMkDnvypq1bzxz2s9xMtuvm3BYiSyaZQSSSNw6Hpx6Yx3qWUW39kzDZZ/6rjGnSt2bGH6dOjenWmkrFqmnrqVU0IIbf7RasFZirMLleSzDb347j/9RqP7Ppgt1vvschtZgEjX7QNwfJBz h/CrWlJC1rlYbWQ7yGB0qSUgeYcHI7Y3fljnHD7COOf7QRFFwWTYNJkkQMOTjByDhsHPTH0qjWyMnXdPFjHC8VuYRnDEzB9xPTgHjoetYm9vU1197YxtZS/dhlcAKI9KkjJJH3Ax45xnn9KdclBaH/RraI7igb yXU53BRtJ46H65FCsNWS2OO3t6mje3qa7KbyLcB2S0ktXCB530iQYBH388dT785pJ7eNLyJ3S38pRIzN/ZLqqkAcEY5GQcenfrT0HePY47e3qaN7eprtpUtVlN0TarCkZViNFkCYJAyfT/69JdW6W7STuIZUCH5Do8gWMKpOFJ9evJx3NF12C8exxW9vU0b29TXYW4LxNcSwJAsi5aI6QxjU5wOQfQdf9oirFsy3Kqv2eyAPKh9JkOVI VgR/CeSPxouuwXXY4fe3qaN7eprqoYBqWllGi yxxnIeHTHfzAMZywPTcD/AN881fEFpeW0jBLXbLwpi0eUZBXPDDIU9 /Y0XQ7x7HDb29TRvb1Ndlbqk neZHa23lsGCyppkjk453A9MZ4zjsaiZnW0l yw29242LHJHppEjMy/K2T34J/xouuwrrsclvb1NG9vU12VhZwRKkMbpOFV1cvozuV78kHOcMD7cUj2yxOoEcVxtkAkdtHceX9c9h0x14HvRdBePY47e3qaN7eprrYLe3RHEd3bXBnV5A8ulOxAwB8px7fhUzzWQSRJU09I1KN5n9lSAkfxHrwOn1zRoF49jjN7epo3t6mu1hsQc dGFMcjbSdHlO9cYA9hnPFQz2UF1bmBl yzy4KiLSnXcgJHHc7iVP5fiXQXj2OQ3t6mje3qa7a0VLqAPJBbRspYSRDRXbDe5U//qx0o8m2uC3kyRK0QAYw6M M9ww59QfTgUadguuxxO9vU0b29TXVTTTxyyR2Ok2t9sd98n9nMoUgcjBPBwM47fnWZHqF0XlnXR7N1kK/8umVXHHHYZwf1p6D07GRvb1NG9vU1vW9zqTMzx6DayiR/MX/AELI boF9uOKaLnUdgt/7Btyw5/48juIJyM 3NGg7LsYe9vU0b29TWzPfXtkkEd3otpFt5HnWmwyY456ZqN9eMi7W0vTAO2LfGPyNAWXYyt7epo3t6mrF9fPfSh2hghVeiQptUfhVWiw VdjrtLjkbTiIzOSHHMV ID37HgjOeeuc1aeGee0YEXhUxNuC6iFBOT96M9D6gcVykv/AB4N/wBdT/IUl/0tf vdf5moitDOEbpHRxPLYXsluzP5chVowNRdVXJG4Er6lweRxzViRZEuTGTKsUu4p9n1AAlhnOTxuOFHLcn1PAGBa/8AH/N/17f0FJqH rk/65j/ANGNTC2p0bWsrrNHcRXBThWNxq2cDjPA68Zrkr6e8W7KzXMhkjkLACVm2NnsSf1z6c0aX/x p/vL/wChrUE/3Yf9z/2Y00tS4qzJv7X1PGP7Ru8YAx57dB071C93cyRCJ7iZowMBGckAemPwFQ0VRdkW/wC1dRxj7fdYxjHnN0/OkGp36xCJb65EYXaEEzYxjGMZ6Y4qrRQKyLUup388RilvrmSM8FHmYg/gTSrqmoIqqt/dKqAKoEzAKB0A54xVSigdkXDquochbyeNTwUjcov5DAqP7feCOSMXdxskJLr5rYYnqSM85qvRQFkWIb 8t02Q3c8S iSFR39D7n86dHqd/ESY765Qlix2ysMk9T161VooCyLEN9eW6MkF3PErZLKkhUHPXODUv9r6mF2jUrzGc489uv51SooCyLQ1K/HS9uAS28kSEEtgDOfXAFJPqF5cx XcXU0y5BxI5bpnHX6n86rUUBZFw6tqTMrNqF2SvKkzNx tNk1K/mVVlvblwpyoaVjg 3PvVWigLIu/2vqeMf2jeY9PPb/GkGrakpYrqF2C2MkTtzjpnmqdFArItrqmoLu2390NzbmxMwy3qeetC6rqKZ2ahdrkYOJmGec vqT dVKKB2RdXWNTRQq6leKB0AnYY/WmSanqEufMvrp8/wB6Zj/X2FVaKAsh8s0s8hkmkeRz1Z2JP5mmUUUAFFFFAH//2f/hDTdodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8 IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IlhNUCBDb3JlIDQuNC4wLUV4aXYyIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wTU09Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9tbS8iIHhtbG5zOnN0RXZ0PSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvc1R5cGUvUmVzb3VyY2VFdmVudCMiIHhtbG5zOmRjPSJodHRwOi8vcHVybC5vcmcvZGMvZWxlbWVudHMvMS4xLyIgeG1sbnM6R0lNUD0iaHR0cDovL3d3dy5naW1wLm9yZy94bXAvIiB4bWxuczp4bXA9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC8iIHhtcE1NOkRvY3VtZW50SUQ9ImdpbXA6ZG9jaWQ6Z2ltcDpiZDgxZjY1MC1mYmQ3LTQxMWMtODMzOS1kNzc0MDEyYjFhNTkiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6NTRiODg2YTQtZTg4Zi00NDE4LThhM2YtNGY0MjQ1NDc4YTQxIiB4bXBNTTpPcmlnaW5hbERvY3VtZW50SUQ9InhtcC5kaWQ6NjYzZDgwY2EtOTIzNy00Zjc0LWE5OTEtNzMxZGRjMThiZmI5IiBkYzpGb3JtYXQ9ImltYWdlL2pwZWciIEdJTVA6QVBJPSIyLjAiIEdJTVA6UGxhdGZvcm09IkxpbnV4IiBHSU1QOlRpbWVTdGFtcD0iMTcyODc3NzQ2NDg0NTY0MSIgR0lNUDpWZXJzaW9uPSIyLjEwLjMwIiB4bXA6Q3JlYXRvclRvb2w9IkdJTVAgMi4xMCI IDx4bXBNTTpIaXN0b3J5PiA8cmRmOlNlcT4gPHJkZjpsaSBzdEV2dDphY3Rpb249InNhdmVkIiBzdEV2dDpjaGFuZ2VkPSIvIiBzdEV2dDppbnN0YW5jZUlEPSJ4bXAuaWlkOmJiMzIxNmUzLTg0NWUtNGQ2Ni1hYjk1LWUxYWJjOTI3ZmM2OCIgc3RFdnQ6c29mdHdhcmVBZ2VudD0iR2ltcCAyLjEwIChMaW51eCkiIHN0RXZ0OndoZW49IjIwMjQtMTAtMTJUMTY6NDI6NDItMDc6MDAiLz4gPHJkZjpsaSBzdEV2dDphY3Rpb249InNhdmVkIiBzdEV2dDpjaGFuZ2VkPSIvIiBzdEV2dDppbnN0YW5jZUlEPSJ4bXAuaWlkOjk2NGY2YzE3LWEwZWItNGQxMC1hYmI0LTAwMDhhNmQyZmE5MyIgc3RFdnQ6c29mdHdhcmVBZ2VudD0iR2ltcCAyLjEwIChMaW51eCkiIHN0RXZ0OndoZW49IjIwMjQtMTAtMTJUMTY6NTc6NDQtMDc6MDAiLz4gPC9yZGY6U2VxPiA8L3htcE1NOkhpc3Rvcnk IDwvcmRmOkRlc2NyaXB0aW9uPiA8L3JkZjpSREY IDwveDp4bXBtZXRhPiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIDw/eHBhY2tldCBlbmQ9InciPz7/4gKwSUNDX1BST0ZJTEUAAQEAAAKgbGNtcwRAAABtbnRyUkdCIFhZWiAH6AAKAAwAFwApAAVhY3NwQVBQTAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA9tYAAQAAAADTLWxjbXMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA1kZXNjAAABIAAAAEBjcHJ0AAABYAAAADZ3dHB0AAABmAAAABRjaGFkAAABrAAAACxyWFlaAAAB2AAAABRiWFlaAAAB7AAAABRnWFlaAAACAAAAABRyVFJDAAACFAAAACBnVFJDAAACFAAAACBiVFJDAAACFAAAACBjaHJtAAACNAAAACRkbW5kAAACWAAAACRkbWRkAAACfAAAACRtbHVjAAAAAAAAAAEAAAAMZW5VUwAAACQAAAAcAEcASQBNAFAAIABiAHUAaQBsAHQALQBpAG4AIABzAFIARwBCbWx1YwAAAAAAAAABAAAADGVuVVMAAAAaAAAAHABQAHUAYgBsAGkAYwAgAEQAbwBtAGEAaQBuAABYWVogAAAAAAAA9tYAAQAAAADTLXNmMzIAAAAAAAEMQgAABd7///MlAAAHkwAA/ZD///uh///9ogAAA9wAAMBuWFlaIAAAAAAAAG gAAA49QAAA5BYWVogAAAAAAAAJJ8AAA EAAC2xFhZWiAAAAAAAABilwAAt4cAABjZcGFyYQAAAAAAAwAAAAJmZgAA8qcAAA1ZAAAT0AAACltjaHJtAAAAAAADAAAAAKPXAABUfAAATM0AAJmaAAAmZwAAD1xtbHVjAAAAAAAAAAEAAAAMZW5VUwAAAAgAAAAcAEcASQBNAFBtbHVjAAAAAAAAAAEAAAAMZW5VUwAAAAgAAAAcAHMAUgBHAEL/2wBDAAMCAgMCAgMDAwMEAwMEBQgFBQQEBQoHBwYIDAoMDAsKCwsNDhIQDQ4RDgsLEBYQERMUFRUVDA8XGBYUGBIUFRT/2wBDAQMEBAUEBQkFBQkUDQsNFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBT/wgARCABPAyADAREAAhEBAxEB/8QAGwABAAIDAQEAAAAAAAAAAAAAAAQFAgMGAQf/xAAZAQEBAQEBAQAAAAAAAAAAAAAAAgEDBAX/2gAMAwEAAhADEAAAAfiPmqu9nX1uOThtZMxbkYmR4bWet8Zqb4AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAATeHmuOnk2ucieNVf0Jmeak9X37qch507B5 aj053FpM57Pzx69NyAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABb L5vT z2Zzkqc4/r27qOFVlytyn28kysVe1HrOxjnwW iprQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAO18nys/T7dE9YtzY898ueS3tP3n1vKai9iFnOx9Z7laqLq md2xXz027lpKvvMxO0V31s8aZ0k1Oqaibs9Eko126IirGc93PWUtXPhy111U8/KQpuFS4mTK1XRZOezw 97jedrDBlVVb9yRO83t9e46sqvOkyKKrrm7s3andSLmxsqTU30xFzYu1JzK3d83N7JmbjuasqBq8yaHbsE5TsCtvs51qqvb6TOUDd0q3MZvlT5Fczdxt0C/8XyrX1 6BnTDcspe1PMut 556zzKtVozXmy9iEvm6vtufKFrmb63uRHzZuxqza9e7cuZ5xNrwzzYdJifI2uu7dz0zUQ2m7cjt3kDducjEyzaVdw5xijrpbZMnJ5u tzkbsSExsrRrdivrZOPCWnINq1TNyXk6WtnOL5 66dyi5U7Mksq92DWzIbWUtVrVhuScyMrJm4jNmphq1E/MjUl5kRU3Jw1pbVbQAsvnfM6j3 vKelfWWEvbnk873rnppZRHK11v0bY2bUQFVSpLLec5m76bOejNrK25mcM2JuzajCKx1MZsTU7fMb127N/MSczna6dVMTd5/OHq6VysZytrblGnNrsvX0nCdsTSzVm1l71Ec6WqucmHNad3RW3U89e7IxobW1t1MwlQKX0xT701VGc15mxaywlYokHOXdpEwtrkq67Gazw9DcmDw8PGjPMx0AAAALHwfK7r2 vXHWvrLeCp4S 13vLs M1F1Tqnsu5jLZ590rN24na7VJfTuc8 U7UNhVc3IgT0868 l5VFzOau 9zzsrkr6dNEbNn5nvq755ocdrO PObdjmTszmHS6vnE59OQ6X3U8pjOeXidBXLn57V1OynlsK9vQZPNZdZtXWzFzJ teZxFd zzjcQh1u2pgN53OnVOWGp0bgzn66dQ4Rcvmt69tnDnbulzp02cpUuYuusmIu7aznL1Wvd2Ttfu8lfQAAAAWPh T23s9mXPrS9FxGSb50brym9e6jjabPHOlnsTZ2VsYtplctvWHWgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAXvg Ta 33x5667hNSaj2dqdvys6Sedfl1e7ZTmFZk3dmViqK7AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAn L5PQez3wZ6 1O6dzqccVDpYbEjG1NO6WWZjU6srYyNm0V2AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAB//xAAmEAACAgMBAAIDAAIDAQAAAAADBAIFAAETBhIUERUWEGAgIjAh/9oACAEBAAEFAmTbaP1lDX2Jbzct50yUvjvpn538emRluctz/G9RnLJwIPPjPU9z/GdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM3 Pj9haGAcSjti0W3Ah09xkyodgpRSVi6Dfnq4ykEV7OmAzZuIsIxsFN0BrOvmNO0r4ull8y/6q0tJQwa4VjYA86CYrinUFq61qL vJq/sIefXlqHmU/xYVaqIr9BevXXXTbSta9WvhTjEXUPLoyM0rAK3 q k1 LxenLY7N5ZwYtU8xb3QsGZ1540miA5ihWyKFjyPAdjRjSn nkuBOgE4zundWF/NEgT9VxispBy0h535rQ8 uTDURENfoJHWJ5P4Y35oistefh9Zrz4xpfqjRBPyG9ba8/MCNX5qboB bJ LCqgCf8ANTmqDyDMtWdMRE36NST5qPQdQ82HGvK8lzeWgu2KqCRN3zukxMwDpm185Gv1Dz0JBPTwFUp18Wk4Uqsmp d ev1mvkTyOxxJ5DcdngCAFK1U6MvMxGqfy89ur1OrCUvOMCyPm5SxyK8Jj8xommvNxQSs6gaUdeM3EhaKA4CqCbS/T/ZHGl1AmvLt7jKgOMhERqDpaiNri/kJmEHz65s35/8AC0KBckiUkkYxQT2k7RxWJPzkR2APKsfGw82RACVRtrQvGufbnU7kil5ll1E3mDqrWNPtYwfKdQsUoFBWNXNJhby8G5Aplj6r/Ns2IdUgvy55yas1aGDMZ0ogwY0KJf8ANk7uxeXJZlcm1ZQz5uGXGe4OUTlwc5inmCv/AGnKLFvtFw9soearZwBFcqwOxbil9e7 zIFo6sLqFnULsuwN3BCRmw3uA7QK0zWe8TdtrEg9Wmwd3hoK/dhWwjcx0Re2eXUXtgCYZuA4xU2EijNaRCcloCGxOW l07gbJzWqwtyfIAthax39 42SbTqyk52zldOjeDjTFuCQd3JRfC01v75o6KzaiIH9pZZoLUs21bfFQ9oVhZYrptVNlIJkrM8GB3B5K1tksSZbD5tFsoG3TtxJrVjDbDVk0IRrXELK2cOBi1LJzT0cQYflXwUtoWhC2iAudi9q3rnyWG/sKQFq5YCCNozhNXex/G90X9JZMJhTemCUbQAnrKyUL 2a/M7JkiwHzrC3cObYM8c4AWTSsP27fxadM5uN27DW3zykw0Vo27lzchWBwGjduwgaxYYzd69KULlscC2jJw/8Ja OgXv1G5 qJOJbjZY/0vyyXqI7Ow1o4EPQfQCW4CUUvWEgZdvi8n6Uqy7vpNPhF7AgyB9FoYXX5vldu4tYT0u331LOaRC q67f9LqwDWXZK5n kloVh6ub6yN5MC4fT6BEnp 0QeompGXp5m1v2ctkFfjiNkvc4G K39KxHN iOOErGc7L r5wj64W4EJ0Ip6EigTesmdUdno2A9dsIp n7SjczRFSWw6vUrucnl/R7AK2u5vxvn9vkrHZoMresMpA93JjN qhvcL4WhPekYeXrbnSCivo Mten/6S9T8oH9XMuq29kgSPrDiG96kr6il RYO/ZfMznoiNKAviARXuJCna hJZnXtOJQXkENT9gScP7QmzL3fEkfU70Rq5ifec5fD/AIa1uW/jv8b18d/4/OQjsn/mXf52m6kg6V2mJAjKohasKoM9O1YWzyF9NUiZFD grjqWdmtYHrQFpmt3Cs6mfolTDlfJ72e6WYiC1gGxcvY6BY25NFqiDE5UWVZXrN3S5lmGqzdpVW3B925 aFxbTJY0ba4NbuFJObtVdpOWA4z36JbVsC/r4gK9XkvJ3KHIPoK4RWHSMDrblQFWi8oiuO7Ug2oseqbk8vJdq7gddqyAEqtqCMCPjBWMMkaNr0X5OP0gtnYdU4gfWOsO4RcsmbOP065zQ7gN8kdd30g5uBeTG7K8rYQfcA6q1ZACUha1cSNgoReblKZdcyDLpnCsCRuVRoNX6JFB3gWZwuFNNQtFf1zdhCMwXutshYpoJM gVnCV4lrVyxVlZBeIQW3bVxst21G2l7 sgQdusXJTrt2hLKu1m3qD7FI8mk5G3ponlZVX0x3tUJ2LNb8x2Qx1rPoZzk/enkX/AMpx/wDlZSrsMG8yvzKmCvEbzoysa8kLrOnjwlrQWGVa6B91VbKwmmBEalKGzVY8vCEf5IWjgpkZmMiuxXtlGdj/AFOe9fEVKa0MXzLohSQIIJKA32Ieffhi/nu47CrJXlSTCwsLynQjlBtVeCEJxPSOz2LzTp2AedNPP52UFS10FJ/6mSX/AGg89pqd09GcZtWoWbWwVYh6VyOouWD MtMT3XVr7io1rNzRp2q9dyaMPXo3Ny16Sw1MVk8cPysH1S/cuf8AVP/EADIRAAICAQIEAwYGAwEBAAAAAAABAhESEyEDMUHwIlFhcYGRocHRBBAyYLHhIzBSIPH/2gAIAQMBAT8BnLUm5eYuE3yZoyRpN7WaEhcJyVpmhI0ZGhI0ZI0JGi/M0ZGi dmhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JEeaNH8RLN8G0r6uny 5xvw34xqeUrXfQ4P4D8QpZrbb6P3nD4X4u1Kfwy7v2C4H4vg8JcNN3fur6VzMZU0n9SEZKW5vmvIlHiSs3ybEnk  glK0/RfIlGbjivUk7d/tZwfD4mLMsV8R8Rp0cOTaUX3sQ3ih8VpWOdX6Go nexGTZw25W2NuO5CTlzJumjVl5F7tftZcx8TFOvUzWWJnfwFLdRXp/JqbbflnWXoKdyx76/YhJySfn9jO7UTLa  VikpS786NS2ku9rHLoiUsY2Rnk331a hqNK36/Izu1Ez8xTtpC4lj4j39BT3pmW9IXGsU92mPiU6Rmm6Xe9EZWrZqc7HxURkpKzN1kxy5jm1uR4l9 0XEbVjk1ZlZe1sjxLo1Lr1E7dGXioylSNSt2ZVv0FxNxcWxXvY5O36Ge9GpSTl1Msf1EuJSbHPxKJG63HxKsybdIU96Zq8u/L7mT f1M98VzMujM XqaqqzPqWyUsXQ LXft xKbj8vmRlffq19DKX8/J0Z3aiXK6M3jdGfkPiroKe5KePsNVbClzsfESbRnbIytbmp38fsZMTtI1Bzkr25HEmoScRzrcU7HxKMndC9f/C5oeCj4ug1HdM2 IlFNUVDmbWxqG7YlC7XdCUK2LijwcxYWmj/ABnhTHVbngtUYw2HUdzwWVHYahHmPG2mUrvqeHL1P8fIyhG2PC9xKN7ClHoeAqLdUWo7DfD5FRdlx5FR5lQ2oqMrPAmZJ7CUNqHgeH4GKT35iUGkPCJceRULsaghyrmZRW5cULDkuhJx6jx5ix2M4s8IlGI4wZJQXiY1BbMWPQeOVsbhj7DGF0NwSaFJbI2e5/jXuJYq1LujwI8BnFOhuLtM8MmRUXujBGKuxxT3ZghJIcUzFCVcjCJSZW1GKMU1Q4J7spcjBGETFXf/AJjzHw7jv3Zhu2Y817hQqWV92aW1WdWxwu  lChRpLqSWSolw7bZGGLs0Rw8WQlSpEYY0KGKocbNPv3UR4eLslBS2HDJ3ZHh0Y K77RpX1Hw fqPh3uKCi1uaI4Xf5Y72aa2NNPZjj4cTT3uzR379PyfDuxcOnffX7mNUaPfftNPn6/Ycc5ZslDJmHhx752OHNkYVucNUqJRUqsfCT3772NMXCrr3t9hwbd31v5UR4ai7Q4W7NPzY Hbux8O ouHTT8v7 5KFj4ak7Fw6Hw7eRpd9 wUKbfmS4eV pOOTIxxVDjaa8yUc235mku/f9zSHCx8KxR5en5X/r5f64c0SjKcdut/0PK2yn8EJSyV n8ijKtxc2OMvFXUjCSnfs pw4uMY7d0Wp7LvcUXlb5Cg7XsX9mEvIxlvXmThcX50Y PIjHw00Pp7iUJNtkYtSTYlPGKRKIo7tsUdlZxIuXLyY03e3dmLt13shR/6NN4pEoSbtd8xqWFCjLJM05VXfQpW2iUG8q72RPxTckjB7bdPsNqfIxdt10QoVJUKLrxjg6kqMbm2V0MNl7/AORw795TvfkU725GElFJGO78iauNIcJXt3YoPaxxbjj3zHGTt f2RTztCi68ZTd99SUZb16CU73KaxVlJciUG7aFF3v3zMa5Lz/kcHv31HGVtrvkKP8A0Yctip36GD X0Q4y2a75kVJLcwl37xxl075CTUUvb/JhLv3GL6Esq278zGXNc/8A6VPYnFslGb X0HGTXfqOMn37P7KkOLtujTWxGCrf/XHmic2ouvUfE8T8jeWz8hT/AEr2GqzKst X5JyePqZSpX3sW5WuQ5tOiE3J0 9xcVkpSW3fOhN3gLl 1FzQ IoR27ozWWJf/JlyXs ZqR5jnToUsht3Rq gp22OVewi1dLr9TVSHOnRqfAtuq/ai/UNRx8XQcFvZtFu 6FBKmaUR4qyqHKKe54Y9 ZFQbaRa/SKCi00aURpZZdRYrwI2h4f2p//xAAxEQACAQMDAgUCBgEFAAAAAAAAARECEiExQfBR0RAiYXGRYMEgMoGhseHxAzBAQlL/2gAIAQIBAT8BooVFKoWxaWstLGWljLGWMsZaWstLWWljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljFqRVmB017lNFQlXuRUkUwnnJXlpoq0wZ5 pTS1A5uTXMsacJLafsZUlCilL6WpK8Op pPPj y5rnqaE6iqkliyJ5HqLJqSJzr9Lbn/AGFXjJPQdSVLaG4nw3gvxPOZJ3G8wXPR g3iXzTuTrzeCec9xTGSuq2fb7SS27eaSKu7Ql4TL9 bFxvAqtOdSSec9i6WNjqhPnNSYmScwXc exPUc5KXcXaF3PjuTqbwKrnyUy9SefPYeGyWmkxuC7X0LuonOmheXc exMv0HMwi7nwXE77FLVTSLvLIp3JyKqYE2x16xzkEzPOncbhwXRqOrpzI3DgTnQmfylThSXc57l2jHVFTp5t3LsxzSRVToKcSUuXBdgnYVUk4lFyyTmB1RBf0J1kdUMVUwJ9RuJJJE5LiclzhMU7/AIJydUUxqiEo B22uRxkUDgdKZgUTaYeTytQYMeDttkcZbIMPJghGDDKtpHHP1MIlM8rJQ9SVhc3EoNUK3YwmkRSYyYmCFKRcjBhCVJhow5MUnoYKoSk0RKFBC RVJia1QoaJRjQhSY1LVAo2FA11MZRKYsOEUtJYNRx9zGDy857HlMI0cmFAockELwhEb EEeCUCUELwgiC1EEL8O/gqRKIHRiCNRKB0y5FKIF5VCIiC3oQJC9SNPef5HSoZrqRHPfuWjEksLmhaVJNR7/vBz e4qFSKnREYjmxbz57kQJR4NTPv9i1SUq3BbiCOfPcStUEZksW3NOxpPNoIzPOYFTBbKgemOv2YqVTjmkDUuWUoSyzZohbc5IsaEc e4qI/b9i3calDWpAlHPct1507eFqFTDkgt35v3IzIsNPoJWpIVPglgt35t2LefPc2gVMEYj1/wCRubtlKcQZxPuNVOloqTaZuaOR0uI5sbP37jeGtyGogSj5f84Euv8AnUSeJ6CW7FT5UnzQtl1TzA80tDlkY56CTiCMOdYEtCmnqaNM/wBOl0KGKl451LZ/MRrzqKlrnsUyiMRzYact83FTGuo1NU83IdqQ1iN57kqLRbT6kYyi2dR5qkSxSJW6EZq5t/kShPnQh7FsLyjWop3ErVCI5zmRIXlmBLOealKiOdC2fzGcjT2GnnnT zKTYlGTN083LXz9C3zT6/YWFHNh6kf ipamZKU1HOoqefArskZb5sJPHOpSsjTzzqRuUzuKd aHmMwJNfv9xSqk bf2NOI5uZEs0iWB0ptz/trU3fOdCmpwJzHMEtUmvPfsJzHsUuVJmH pLtb5uTsZUIdUKebdxvUT15sjNMSUppZ lEaOBV4nwuxLJku6Cc EiqklyXKJJLk9C7SC6dPpSk9P1KUtURECipeEJaCiMDcEqJ50MSYpwOlNQQRBhQzFP0p//8QAQhAAAgECBAQEAwUECAYDAQAAAQIDERIABCExEyJBUSMyYXEUgaEFQlKRsSQzcsEQIENgYtHw8TA0Y4KiwlOSo H/2gAIAQEABj8ClmfzOxY46gHHXFSp9/6KFSD2P9F1ptrSv9AVVLMdABjbCUjc3mi0Hm9sNfG62taajY9sKnDa9qUWmprtjb 6xxCJuG7BPuKCBriK2MRt6j eCh5ubUU31Hyw6xgKaDmMda4MhC2W6hhqTjLiilwXuCpb7a9cSZdpKPfVIkrX/u6EYzqZi3iMvhnh3NXXbtiORFVGv4l5grZqptp8jrhBCgE1VP7uhGhuq3Wpphcu9GnW61eHqCWBrd7V0x9oIWLtmZTNG5j/AHZIPT6YhzMpUScOP wqIytK6etN mHYbE1/us8L dNDTCZdhYFykTLwwF1KqeY0Pc64jkaViHAtCuvO1rEqPmAPnjNZiJrLDoAVsUggWU79cNaqpWONqIKDVFO2EgaWVF5qqXW/cUYaban8sZM3SkSkq1DqTQ UU20319sXS50RgNYVvBob6Vr2oRiVvFLgJSLiLVCbt9NfKPzxlEhFatJ4hIPEHLQ6dMZDL8O2R0eR2DLc7AtRRppWmPDd5nMjKDeKLS3fTXf6YzokjvYZd2VuikCvbFvxTjQkLcCXFRzigOm npiCRLjeXFxIoaHoNx8/7rZz L WMisuZali3GVtI0LWqBgS0FjVK71OhI gxOHkCTRyJElDpefX01xO2czFbQ3O5a52CE0FR6Yg MlYfEAtxAtxFN7q0pSuEfiI19eVTqKd8ZNkNz5mQxhfan eMy3xBNlTHyAX8l21a mJ0ScyNDFxG0X8Sjox/F1xBmsy1uVl6pq22IQk7cGUFgbdacWz/wDuG4eYHAlFfDkNrgKW/wDU4dZszDGFR2u5iKruNvXCy5h6Zc26pvzAkfphMtG5EUktiuRrSu MlLx/ Yu0t8tAT/LC/tUgBjibWLq5oOuI5c4wWBmtrGanHHy7NLxJCsSClbbranX WJx8TV40vpZT7t2uu2lMGsqhEHiTP5AdqClTjKTcdnWZlTw0B5mBoBr6emJ8zBmGmVGIXkpdzBe/riWWamWEZttmqGLUrSmAy5i Kh1AWrGoAt5utcZeZC8sspUcIJrUiuFmmLwqZljpb/ioT6YLyzRcHhs6Oh/eUQtp WIYcqz5ubhCSThqTSoB7euMpJHLc89NCui1WvSp6dsPxW4TCYRDlqDzUJrikd80VgkLhfKD3pUYy2TXNkySRhmcDSpAI3p39cZV2m8KUJfSlyMy160H1w0bZrxzmvhkFCNqanT174LRzhn3VW0uFpJ2rroeuIoXzLUe4F1jBCldyebbXGWzBnYLJJwmFF5TT L9aY4nGuCM3FGzWh7bgMFcuzPFpRm3xMy5jiCNSfKNw4ToT3wX JI4SK8w4ewKFxTXXbC59ZmaN2tRSmta9ddNsZiXiHix7QoASR332xHGczMIzlxO0nCHIKV/FjKrl5uJNPGJLWtFBT3r9MfC1ZvtHi8MRjy0xMfiPKtVqlLuS49cXLmL4qbgLVjWgpzdffENjPx9eKrDy9sRzy5l4WabgnwwVHrWuJ3kzNskGji0Wq1taVr8vfEmWysomaMc5cqP0J uIocqWfM0YzBhotPbFZXjjQTcBjWtG/21x9oETcSPK3C9EPMw6YT4Z2dbea8dcZP9oasyh2FlSFsuJGuvbHxGYmdbXKMAg/GV0130riYxTNKIp BzJSpp74tkzBTlXWwDmJII1PSmIPHPFkgMxWi6chanmr9MJnZCBlLqMQebemJZsrKrQrsJNGYhbmp9cZqKWdDLDCZLI67jptjLtfERNTaptqtddPTCRySwxyvKYVQk6kGnbEi5lymZsV40X17/AExPdKYhEAa0B3NO4xl5DI9JELkIntaBU61BwU KfifENBpHy6a137YysvH/AH8bvS3a1LsALmpAGENKxDzSbdcQzZxrMvJ1j1O2mJMyZ5lVZeGo4QN317YktzI4SNw6yijF6VKgCu1cPC2Y8Gr2zItwFp1u2pTELzsIo5VuWnmOlQBWg uHe/jMHKhYwNrranWu M0jXxZmFbuEy7/Wv0wIpvDS2pdVJp0pjLzwcSaSVzGYglSD8icCdQQ7SBEjt36Ek9MTyzHVPKibty3E60OFXLcTNIUv4ipUEdSKE6Yhk IIDLc3KNOUHTX160xOZcxIHin4OkYo3tr2xKqB5oowrGULoAw020xFw8yaSoGUWrXViPxdP54yA KeN81JZRotulRr30wkyFRGz2c1dNd/bGbVpZVaJQyHhrR6 XUN1OH8ZBFGOaZ/KWrSgpXtjKsMxpLG7mibW9NTjMM87fs0/Ck5OlaV3r9MEQsWj01b pNmSthkNadsQTZaiSZkBUSMVAVaAadtPpiFzxPBYmOWzt/iw3LTgScZiRqzNSnv/vieLxFPDN6tHQItp9OXSuEj/tHTlWZEF4NPxb7DESyV4SlrOWg9cQRZZQVPixaJUcwWoJ21phvF8BYr6u6XWEkaV17jTFZ1TiMpQkRxvdqKg0Guw3xAzSqUlJtRpQoFPfQYfLxVAglVSFKmjkigr70xMrXG6OrWKrKEoRpTQddsL/8AJzHVkpU0DA9O2mIYGo0dC8cdVvNteg5u EsuSdW0puGxnlZ GIU8atLVFOlNtD0xSMFW4Nf3SpyL12 uEgDPLU0VK1xmcuL0igPPTobhoD700xPGwmuCBZapzBfX0weDJxSq2kNbbqetdCa09cQSosgSOS2JVT72uwprthoPEGVBtPJse1f5Ynkh5srdbILbqab nvj4hDULFpw7WFtegGmhxlomBkjcrwxVanTSvXau BwLwl4oocbhu38WJg95UoLrFDIFIppTQadseNHzWeYutAFoNTXTpjKgSoqEeGGeMVFCNa9NxrjMTSZgoRNbIt2t4NdsS5pmR GBcWkRKDppXDSIlsw8O5yn3aLpX5Yy3FItArHGbGO3Vd/zx8UZjpPdvz8TTX9MSRycVTJoVMdDt00007YNVlduFqrwXcm9aEfXGUk4kfCapRAq9NNRT9cFixky0jV3W48350rTEt0NvCNG8Re1e unbDSzNE3h3NThOtpYa0GmppjKujUjozxklFFF0NfzprgLMiOjuYeAzqt5u2oCD5u2JBloVy0bCjCME/U1IwALJi0AqI4UcWdK6emMuiqwG0cojs2H4gMDMBJjU6S0O/vjMRn4g8oEoKeUUpr20wbJeEyrbzgKooRoB6E4sjFz0LczAe pxwOEeHx HbUfvKf5fLE/EsKhhM9ZU1J2O u/THFcWtxOCWjtQl60oab64WaEKrMrGplTYaNWp/XByrloxfaVpRQbq/rjMkuzcvjNEOWhHWmLGitbh8U3MAAvqemInW  aMRoE85T236YPF4zxt4Rqmla1p74zgtNV8afixrynvrscCCCV5Xkeuq3UJ6 mIAiglVIR3iQcoFDzEainfEomWRED2sAKIG7aaYzOXyq CKySsN6UpvhSFPxU9RUUcfhNaYWdmtjktH3SDy0FR/CeuIs08fxKXllFdyWpsDXfGbfMWPOviSgONPkdcNEweJZQCVYUuHTCcOTiR5kiMBZUOw2pXl0wJoTceNfyMtbzpWmMxceQjmoUpS37v8A2/hwQAqOVC8vDGxoB79O IXN7I6lo42JqQOwxBYOTinhoWUG/Sum/bGcLaxaSSnlYc33h fTFJp45DIm1istK9qd8RHiCsWiEoKjBgaYtETUg9da7  HjiexX3oBX88CfjES/iUAV9  Ehd/DTZQAP8AfFsU7otQaA9sTLxbVl8wVQOlPlhOK9bBRQAAB WIwJzSPQaDtTXvp3wGaS4hzLza8x3P0xxZWufF3FobbBaoFB6dsQSq/PCKRkqDb/quLFmsW67lUCmtf16Ye Qm 2tNNtsEme6otIKgg/LESLIoWIEKOGux3rpr88PE8tVdrm0FWPqf6ymKB5cvZHGgrY3KQf1/XGXVoBbHo6aUdaEU2rsT1xxAG4xzPxEhHSnkAPzOJVTJ0uBpa tbCpJoNd/TGVkGVMfw9SqxyWjWn HbTbEUdhWwsfOaa9h0xCBAGli0Vy33bw9Ke4xNGMsyq0AgTxfLRrqnTXX2wz5aFYrmZiGYtq2/bthMyyB7X4ltd8cJ4Y5ucSXHetwY/ph4pIGtNKES81QKc2muIyYbgi0rfzk1B1NPQdMLEYGYC6vi7AqRRdOXf1xLM0IETvU0UV9r6Vxm7IjGMxZvJdS35YjnfLM9iuOHGwGrChPlwjIkRsuAuQde53OHLZRdWrbfyUvD6j5b4aJ4CqUFtstDUCmumuOMEVqJaFUBVPa7TXEJlyt 1XZtDRStQCNDriWHhCO9idLToTXXl/yxmAMuHLG65OVV5SuqgYiQZZikagCs3NowYa0202xlBJl9IJFk5XpWnbTTDLDHoZeJSR7qC66g0xmD8JW6Ph3XVIFpGpp6k9MXcDl6jia71pWm3piBJcrxhE19Gk20Oi6aDrTXbEknNzmvO1x/PGZipXjALWu1GB/lgleWTgJAHrWlDWuMm6pKHhSwXyExn1p3 ePjG/eXh U0xMseTReJWhJ1BtpXb0B WNcqUsA4axvQVuB7baYZzQXGumMpEFBjga8rXz61FcGE5eNb1KuUNK6UFO3TDo WeRGy6QERvQ8pGux7YEIy1qKgRGjktdeWm9MReA4KT8cJHNRG5gdRTE Xy8Jiil8yzNc30p mJ2ZGkZrSgVrdQ1dcZTNWD9nt5QdDQ4TLplw WAoInatfEv7fLBjMJh1TrryqR2HfEBCsIlSgZlt4jfeb54MkS3vYyj5jfCpJAspXUs55i911f5YnJQXzJGpNeq01p8tsf8oOHxOPTi/2l11dtvTCK WZ/DkRzxaXXGp 7piXLsEWJzWgrpr74zEIhDtKGF9e607f5YXg5RyqxJGy8StbT/Dt3GMuHyqvwhSt23Lby6afXEpORSkst7VOh57tdP8AXbE6/DJZLHZzeby21qKfpgs0KuOQ0jpH5TUbDGW8AqipaaUF1BQEG3f88NAY1SrV0pSl11DpX64zERhgdZ615LaGlOmAxy1QCG0l1qGuGtNvTGXh4SDhWmr84NFtGhx8MFqLw5JPS66g001xnphAztPWvPyCvcU1wJLEXQi1lRhrvTlx9nloro8obrA1LmrWu3t WFWLLPHIkvEasnn9G5e2JhwfOKCr16U10179MXnL/wD6da17bemIi0VUSBoCqvbuTr6b4ZzBezTCWjScq615R0PrjNGTLOHnhWMHibAU1PLrsO39F9ps2upp/VoBU mK002rih0P9TlBanb/AIZxl4pmT9mjS12F63XXPt16fLGXXhAXVEslDctQatt3od mHaNUEOYzIHD/AOknfrrp WMw8TRiRkIrwj1Qii6d tBjLNl5Y4lEUiSOYzrVaLsu /8AnjLqpjMgLXWqQfSp64yCzzqghmZpYyrVKm3agp0OMxSVg YU8RWVg1bLdKcvbfGY/bIxG8FkZbim03IdRTTY7Yjzs1vBCvayvuShptriWPiSJnHb4gNqaPXTm32/XGfEuYaQSs9oa pWygp0374amctkMhdJuGfDjuXw/ofTGVSbiSZVHlPw tFFeTqMRCMmL7PGYWWym2o9 2M8qTcaSdloUkl0Wjfi9xptjKyZfOmVky6xsebQj IYrK4jQxyLcQTSqEDb3xDl5JrmWYTmRYzbcGHz8tenXGbSPMqksqxgmsoBorA0NKncebGYzEpGbil1VUR6r7 X eIOJLZloeJw615blPbXc4jy0c9XMzO8qvLQaim /wA9cZxoM0ZYZzqddRT198TJmJOEGaNwxUnytWmmIMwmZ4JM8DtytVAikNsOvpgRz5j4ldQ0Vrani3X60 788SLkAYMvIoDJTff1PfBmM6vliv3DLeKEGmopr2GmMqCaMg2F3hmwjtpr HHxDRM0XxAY/hK9eWmM4OOWeZebRqE2Ecum1ejYy3DuSBI7WUrRxRqgCla164SMnwYybE/DXGTgllAMbqxWjEjxbvbb54kjOaVxc7OqI1JgUoF1HQ/rjNO Z4sUgAgUIf2fXtSmn8sJm5GjEWo4rPWtR/h5hh4U 0pI4zneJU33Wfi2xn0 NRmkZbNZvIFIptqffTCP9mI2WNtH031H I9sfZN ZCNl5BVaOUVOpIp5vbE0cOdWSRprhHRuUA1BXSlcGWVrpD1whmlbMRjLLpLU KoqP/LGSVnNscXNNIW0fhFdKajU9MOQL8/fcMwLiN67s36jGZkzo4mcH7o08/LbQ 2hwGzpQ5aOJEReHpst3Q uMj8O8aSwqUNsdH3brTscQZrMNoJhI7fPXGYGYvSSdbNr9FHKWbqbv0w8uXzEsamKZN2uqa269tqdsZXOvmqtFlwtioxfiW06inrviFI5vCWdZAtr1XxrjptsemuJ1bORGTjLIP3rVFpFKsK/nhX zFbLctr6b/8AkcZSoheVYw1FQ78L73fnpiAZvhpw8w0hjEZowI9MTtw1ilkiPh2Hlbmtpp/D2xmS0MQyMKhkYKFOhrT1rqPniON2qkdbF7VxkcpNcYw1ZuoHPdt3O1cTiOWTi5gMzXLQXWAaj5fInEfxObfkGXe6QM2qeYYysy5rhHjRSPytyBY7SNB19MJFmZ/iujRWsebilr9afd9a64lTI1gy0oFyU3 pwpfPtbBAFTi3kSv1u0JpX9MZcGw5lV87xkgG37wprr74ltYFvib49GtA4l1zCny06YzoeV51lHdiWYrTqPKOlcL8LBSIIR4TU9q1X/XfGUUzUeNKbNynh07aa/hxIk0pOX JMixJcLqt94bU uLv3lI40DQ8i6DXQjEZV2iVYwlrIRQByaaV6fI4 z4Zyvw0ER04el9W30Pp0OCQHXL/ABFQw24f8NMZyOOThZaVVNsF6lmt22ApXvTEhGWjtsomrUOux5N6dfrhZGV4zYwvZqgHpSgqO3zwk6RqsvxF7OQajm3pTanSuHi8Pe8hYmFXsGqdtcTS1S6RrmeONgGW48vvT5Yi/cCMRaBomJWSm79xWu2JofiwshmDx8EOLNdSNNPlrj7TZczL4tIolLGlm1T60H1xHwcy7qkAivYklurb v6f8M4ykMilnREllRPM9zfoFpXEBTMni5ioRbeW6hIFfeg eM0 mYtmWGMvsSNXP8vnj7QbmgVZG4YA5VWhIY/4emLb8w2n3UFTzKLx/h5vpjIUhl8TMNC0qa8Ty0K9O CCtwVvK/X3pj7Q/Z H8JzKqM3ONqan8RGMxBDBxXhiYlEEj/eQDSoJOp20xFmGYTEnmyxtFP8AyJ mPiVLQX5iylOSNS1N u CyGZaJxGSReZBYx1 a4gjMkpMkbG1V 8Kdaba7/XH2czBqeEs0Y2a5Sf/AFxN9pRRuqiX91SihffrhniiECHZAa0/uocZZpJuecB5Gk0sUtav5443DHDNSDXUgAn9AcSrm5THHlnVbF15m3p8h9MZtYaOkEjICxoXp2HemJIwY0VxR/FFKgjlPrUjEbcYq5ZlaPh81QKkL LtiZWZTwns312rtjMySTPGYVutWO6uoHcd8WHMVqt68OO6qVAVt9tfpjLMJldphXUqif8A2LYs4wOcMlixLQg7fe2xIJGRvhlt1fsLrR8scFY1vJYb9VpX9cRGV0hEqO63HsK64keSVVzPG4CQgjVtPX1xmIszOI5o9lUVu0/2/P8AuoRiGfLqsYzFsUSaMOWgG/yxEGl58u3KbRUf544KJe3F4rtXzMxCj/XrjMQyuqS3FZKIvm2J9/XD1KOzDQmNdDUGu2p03xlEtjmNxSK6NKk/P364mjma5jJe9QK3e My VjvhpbLqvv19sSxKt9qcJxVfKhBp mMpmW8KDyQzJaH66VHN3w32g1ZVD0Mkhu107/LD8RllVkKWlBQcpXTTTfCtxVqP kvoa7b6DXBy8bCwK7EBFGlpuP5VxNmjSSGKTiOTb5vbEmZaknCUBiKLaNenyP91P/EACkQAQEAAgMBAAICAQMFAQAAAAERACExQVFhcYGRobEQYMEgMNHh8PH/2gAIAQEAAT8h/vgyW5C1vDq4KAWvRkLJso7yfMRzLkI5Hjn8Wjq XI8cZAMCq GVBQmkcfvdytcT1nolvPu8dOsVQ6GfwDu0mVIoTkcjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyjfMAhmF5GycVP4ycwtYJp/tlETKNGw9 HJUbBeBuun7ia5SWERJ7eJhwVBqKm39fmI6LVKVK EPVGdYcQ4WGIEiCpeHxyj CEH9ygA4uuccP2Qz/kGR5MAmKggI9SB6uU8ICNAVy726tOMmcaqEevjqoD9MPnDF/P 1pe02KZyacEtke5FD jOz5eQWnP/AJZTL7zLgJLmoXxrjnEgRAtlING1ymA2ggERycD73jXfyMCmz0aPL4wSb064eIadE5eJiTSFIXYxaUhMuSVSzhfpufvBE52TRT1E3Pi7x6DZ4hUAq3KIYVpRo5Ait69JvL HQZwOWBRH5d51YaZwH Q/h/taU/8AmmAqpGXsb7eQ42cZoQg3QOqiq6Hyy4 IGm3sekFfcrl1MC3ZMBthOHjAKdikxd0AFd4A947N3Tq9Zolv/Cib /45SIg1BOx9tB4vGE5BTY6OwdtB1xk2pI0Kk1 sFaQ3BB/ccBTWpDtEQuh2c5qh6 E3lUjr8XBF1l39Pp  bdYHVgR MPQZX Um8UhdkdRHydv9Y7Byk2M1 sARJEpAayVZpfZlYokIaWmqKQQfoYd7foLRM0azgfmDa55ugoNjDca2L1gUcnbRpNc3WGyGYcKMWycw2ZVQ6qABUJGVOOLrOL4Z5EEVpOwvVwYpm9RDnwv9PmSFNUtwtf2sxmShlwUlCct/rjO6MV7i14B2HpTOB8stR8oXXu MZALnCE5g2PcziKZEMJxzop8usHIF8jBEcNO/G87GftxRctVI/LiJzSOokaI RmbuugEPKmrz8z7CJqBtAH/mwxE p4eONnfecAErOBf7uI693EhReuadhj7/ALQyxZHXOPFtIwZwXBP50dyv8bBIq6GJuDnNWckUp0n9wmdBiKtXT/kD7ib1iDUpu/nKifi FrQbhBfhvBaKYFPIsJVNH5dZccpiCHh/eFRhsC7rbJ8zhUr7Cv8Ap0HbLAxABua/rw/MsfHCfBIV/QuWzwS9viBf D7rITjB03XcJA2/jnBhcVQS2h8kxZAEJ0CSo9BtMQVuWsisrthAneXHQhuhXS8zaOxXQgtrrVpDAnaO4OqPGVGP0w0AboYbTCMYyCTR6OM5eNIm6lnjxwSUEqVCzppcXLtAlrtpEr25DdE6a2eWf2x2tsSdhsA5cYiHCo7QBsOpMmE40VJdm8R5z/OF/wAWNvnd4yumLxhQzidv9YVCgG226fmYGmOgCrpnYa6Nod5qqpaFOUECqFxQ1jKMt70Lzzq4iPaGprVCn9HvWIxKoIGQ0UIAP5xY3pKMdIivwp3M79iyQ8CG7 psXEMABAl1R7pB1ZMXlZFpXwBE/T /CDwgaBgAl0vzWW2zKEYjUesz9pj8AUfJ Z4wuJJ5HVT13bNoXvNF4sIGlPaWxmsKqzzWjZEgWKkauVlhKSGoOnFZw8YFrqYI05kfwcEgzSa4KDZ1dC/ML2WPCxs27XQ6aGOpe170ID VDIT4iDm47DR3G5XJktARsL/d/wCgd2hW4M2lVApdgeT6cT4CQ0eciob1YZtsObVlI8ta1xjTBMab0acAk5 5rjUB7vAGu3azJV2C7CmuvZidsNG3DZcLkwB2qxFClzXsbnZlbYMQGwgh9B 8oxtoaHSO2YYF4DSCt8iDLLixmYyQFFGJscuAtLe721Dsqb3xrFaVa4D9ZCUnma5JyIR1 7jJhaHVSKJTppbg8/l9EBjjrl5iOYFsXghnCTeaRZe6UO5esqlpDCaFKR/PeUI0S0Bw3HZUmAUDA1iobN67cWI2t0pbimy7cmGyIIQVcEeGuHONllJ1c9kMH05wTam Fd3wPW40WiQsoJdmhZLlDpVkwKKKksd4XQnYPTOhGkd8Z8dN/EVdIcejNB4pwCga5nGEoQceRDGthowYXAGlFt5GROesIJxoLQO5apTrKKFwdg0HP/pj3ef0mD08RpzYJaEGiiTaD6nOPS8097HmO9bYiZD5lA69vxZiiBMLQS8OhDy1gWVm2W1bZdlecclpkm5kIGjow1jOB76OnUI3w9mLOA6 o76BjE1gNPYYLoNdPb5m1z1HRNSKB1Zg4rpWtT9rrNAgayjDYvRdUx3SaCDaBBA6KO8VGoEWBUoBr1xie/DPyX X8sd3GFw6fQ02HESAffSCfyN/OEYhJjxGE6TB1srhnyIfR/jFvcHDV0So885q1hTxoUZtqO8l2eQRBIdCHc3M4Fo2wIXO37xiTJKr8H2dbzjDwlw5o662cYTkNwppECTaYA0ff86f4cMppUSqFenRt31iqTLaC9sAcN4xE26MQY7ezQ2bwrxISNoxS60hcjkkETLpBAeDrHoyMkNW rgolp4dMOD8J3lYGPBW2BpXVSYRI6u5v49f0ZvVDzxDJoKsHxgd1nkJ3D5o5wcGiROqG1xTIYXGxdviJsrG/ebWBtNV5RYvFwCpOkhIblYcedYs6chV2cpynu84lJel4Qin6ckCyWP1BtvlyqjeSWSsNp27yQjLqCqYwA4O7yQDkaZL3i5LCKW6AHODLBHmPg XLWPYLoOBS82OcdUwFgABAA0B5nE3aV7nQ5Vqc4ULWkirwk5TmgoiVnXDRy6fMSnEiAapIcBXRiFtE1W7RFu7LcP0xPgOg/ljQuO6i8Fd7j/0l nBBDs4bNB5tTGuLLwalxUXLnjPGctiDwDsOzEGBdpVgaaVA4fnNB0004dfFydu8EyV9m8Yup c42x3qGwUc9l4eMMo6hUf/MyYNWTkWFU4aQzT86cCGzIgfV3UL3YMloOvpFLXnxDNATqJRnTbJOhzd5P4lc2vpOc7Bh0sMwwDZ0T97mMRuUshPFuFh43yKJc N3N5CPqcpqwnJ266ysdaK2uI7bPDTxjV5UVBUEG IYCUBKY1A/l5 4NmjuOcpOT2U4yVvZWgsqnZyP4YlR4i54hJFZrZj8Mt CPK/oXebqkoJRdbZVrz8mMDjkaTSEqFf6MEm9Ml1W33qdPMH9KBu1P4GVdLvG0vwYoALmuyKMjvN9z7BX9GQkn/AN8BwB5pKk0Kcs/vBTocxBEEE qwdpLTmD0tnH3DRTAWqugKukBw7zaMkWSegg6bfveNbiMEC Yk36YvzLBjPmHkeXBu5MB23J3muJI JLe46neDwjBoq7tunjrHt2 QMN9dc3vBla2QUmkHj3AyukaLd5r9/MVgI43afq4UMW6XIvL/APXzKntW3Gwgb24M vSJxHfL68ZWKnSyppGy2Y8ULg3JP EzxnAwqiID0cZENlrX0PTXx3k0oGPJB9Pzm2nGUNg6ah1kGO2BBJaqFunbFHuiFuipyVOweTLpQAg6ShR1dxTKIrYONPKug5kwGe24h6AOOo5xwCSq3cOy9037rCxALR7sANO0fMY2NV GBajOnGxwXoahRsCCB1O3GTuGXUkdrKOO 8qINIdOKGltu8MnYkQAjNKB7/Wd0a8jU8jrZkX8mqXVon7qe4apAV 7VOvHGENplvLQQ6SEQrZnslf5V3bdOT5rHibODblb IacHPeUUtpkbDGv ODLEbIdB0RrfmQ A NM7l6uGX7iZZpjkPl/0of6cYbU3AKudup4NXzGQYMR1H/SnuR6YskxWbD/ALYwcZIFt02Fl9kM6YXVNFXFDViDbpDKz1awk8NLV 2Esnac02Y2VUH b2QfwFDTbSXXbEcLFppsa Jx3ib9g3ux4ciYooi6LCKXC2hbzhWaPi0RHscWawQogdgdVNU3pPmI59CTyG1uXf8APNrwImSaemuNpvBFuzDTreOD4u8TJkq0aJLRrTrGTkm9CrKv5OAJCyoG7hfRduNYbpk9Ipo7DjzBakJhWwF5HBlTPeZIihxYFpxlTAn9k98ZoJeguuC/1cPo lMYTvxOKmHBWxVV9uPIRMDUzTygGo6EYaQmR5GhanHWTtk5DcqXacudzFqapa/I g5NozFfeKKAd9a7wrbJoECSaRgg5MHeSBEouOwFpeeTETKto09tlWvPcmfw8yQq2ocAcmPydsCVKHJtB7eshHRPilQwaBScFmTX2fHGIk/SOZPpvXIaY esDEpF9MNP1jf8gjYFlIjplHDiyNR7aRbv3XFxaERypKwuwvMq5fAjLOQc9vxmgm8CKoo2YN89TLgEwzchuO1UYSbxIslfOgD gwZgrDLXfxF7FwwCjqbgY8zVY9ZX/V3qXIda5f8AOcoGLe3wJq/jNOov JqMJIgfkwkyt5TY6kQ7tuNYZC32WsLEY1T29QorQ6Za O3G3wdoZ11CuBs0avLxg8tBL4pqSuyTjGxmnI4Cavwb5x8KqrOYnPj8y98ZKJ61jr3N3FyKaq3Qmk76hhhMAYEbI93bY/OzE/RCEghjp9dM4p7BDun8ZQoF6EkE7gbOFMjK0IG7LSq0R5GGLD4Qa07bzwznLdrSa8p2V9fZgXgBBRQrsU4LlMN0reKL77 4axeKiJRsDrsJlZvFFeRGDjz4/GCq/Z/YOJ2LUhMoULAzWXcm6CTjH1BJVreMeDmW40hNsdB1K 1XlyjVPJKLOwRJhSLDeKJNk84zvvV8aNzpp mMi673ahziOxyZaVe6N6Kq/nrrIOIMiyjcaaD0YdsIoJVQ4ajR/beUJLsR5dItFeWVcpKa2AxU/wCDNjXQIkGrWS2aHW831tWeqJbRdVIveWp1jyak8gTyayik7peoQCbPwYqLFcuS3iN73wdTQoGer/xH/bhgHCIbCh8Qo9cEooE7ROZoLv8Apks/jSCDk0fhlCPbrsleUhy1FETQOSc9v23ltDr9I7CbWfxzlFPG8geKX HDFJ2LGJSiImnVybQs68SkK10yR/jNkdMLH0fcURxTQQ269Bv cEbTRpPXigfvN2KBOw Q/KaxQHCApSG q/nWCKFtvwT0bwNPMmNKoNAd/nf7/wBqFLuYWTQMOQl2xo/GHajaEA6 qDBOAAOKjYKOv4GapYUdSlNwsMJ2sQfR3HV mDei57MC7a01tMNfi DsHvJ/DrB  lgod6tjrjFUvsyPTgrXweTzESpvgHnYc5ExBqvoy n M1Qoy4VV5SmYccJHdB/hwNLrHv8AwGuesCSF0vsemmGwM11Uy9dP9qGwVjog3Wy Hk94PnZ3YaizTqNM1HCii1G/Wftk7BCkAkQ0hRG33HmdOWXnRJ23jOxRfyEUb7/TcMNTUM0 pt0MzntoloTuvR1kk5ZSfwA/tk0CDR79E sdKSNSexs841hWrrROwOkuVD qi2g5U1b1m9x7zsDNt/WIyGjQIC tBqTG5QIBCIATrg/2p//aAAwDAQACAAMAAAAQUjYeeNBLbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbGIUOw Kf8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wAJ86xzKwf/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/APPp4S/JenkLVTGx 4qqFE7DICh82oe9ZvD3EiulbRdh5TfPAhv/AGz12YS5sN4LTg66fxI/hLUEO2bYVDQvoAF8pIM2bCVo9npZ8f8A/LEhBtxan7EbPZsc36QbQ4YUw9f1kYiaCcGF8yKqe9OX4b//AP8A/wDiaIm9xvpnk vfeVD98Yo6OyiXq6Z7vN/EWcpjoGY/sEw7/wD/AP8A/wCQbANtCiP/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AFsaXzxf9r//AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD3cXt/KlOf/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/xAApEQEAAQMCBgMBAQADAQAAAAABEQAhMUFhUXGBkaHwscHR4fEQIGAw/9oACAEDAQE/EEcyl7tKICmb450klSKEQE863T3pRgyOo1unvSr0SVunvSkkqRUdlPelIiotvV6JP9xSJYjnSdlPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70oTzqVoZKETGZZYLowhFS5NEA2bmNEbZ3odCpAyiSAYJCmoWxMUN1SVQiJSJYsAeCpySARUIRELXIOrGtQxZtC7D3zSPPixnlw5TvSTDm949 lCBwkROsBPLNt8USRhXXiqcoLUNNFnwMcypNIgYncfcxrWmCzOZbLxgyPmgUav8A5afYomLnSlk8Xdq495FRBos7Xg7nsVwETjODM85OM01LqVZqe8Npjnw607Nro6THHPallBc48Lvl TNIk4v1hi3POtObDli/9phlljYIGc9NL9qkoRi3MnxTwdX6asHFrpMFu74xRLgH61/8sreZRPHEdMr1tTKGjHmPmkCUtcjmNCN/qhRco2Bhp1iKghO0fERQypw88qcw9E05WaTzUetZtTqI6t1FsXP2KlOFxjw 0VFAuId18hmggGV29I90pJ1fxhpJJenBGEO/6HWkgNE9UNXMo/Yq1cI YFjua06BmPKluUS8yjgRd04Fs44ne01gQy7C/knOkmURnsL8/eKA5GHa8x8Pagsi/gCJ QoMQH6n1UzpE S3Zn1oBLUHacm9ntTYGcezURgx prHCaAwXtPeIOyPrRgOZ8Me ajiWXx7qwUpCLk8cTG9YhaB741x0 pl4tb5H1bzUKGsfGPPDE4pw8I447T4jehyAvpwwP3UjWU0SZ/B 6EgGzzntSrw57H77NKBG3H6q8QSqdlPpeVRCVpQ6KctKWJ6OtIgjhPVQ KtiOPKCP0KuA8vP8oZhMB6M/j4oTa/xWPBNBGYSdh1jjTFOpg8/RQkEwT0ifeTQGofFmO8UlxaUWYYO79E1Mny7DfnNs0zA0HvQmUZFdr9HVERGaMyWs10Rw2pC8D8mhDBfxeY KVeFuLgkmuv7tQqGlv87zy60kGDBHkH4RqVILX8KfXanAGZ8R 1MgjKdAu8u40s2x80eIZpSsYQ9HpotSGE9BfM1hFz9q9AWJ989q3hE7EzHeKXaGoPGWG3RnlSOvOmt sR1ONAwbED4Hlab3oELlr0n3XamCGqHxfyezAyLIjzz/ykpoeZCPPsNAAMP6keH6moBsfuJi tTmAz/V i23oZYLQOuuPvE4o0av8AlLAk48dItzvrGKBb6X I71lSjHNkDylLFYhXODP0c6tCL7aYzjid7UkhNY8TNYAySeP3SalHF/0M86iiElm7aXnOvFpzqm99c/2pm3w6Qb9fNJOSkc5tzhZ2zUYDuL8m1AEM6 8q5pQ5yA45RUTkeeV2szUWKxi7w3vhoYwR0/KZKspOuMT9ce1HUE24yPlHjrU5zvroZ4lnOIaFzhVNcyzm2RmKmWihMSVud8vV5zO9Flm8F1uv28dahLtTCbl/M9igFHT d6hizvi034Y2xUPMnmOvXSiWKXR0B9xzw1cnP9TM3vJzqQjfXPF 5xV45EjnZ6uN6gnL8fp461HBfPPnUKXffMuHnOKhOBHS34VO/ukQnHPFntcpUniznMs35zilJeI6QY7TQacuu7Hle9F8uV/7yoZZf/f7tUqcJz0DpiMVqmY0dZjvDbNLBujJiz8R0qFZ475u/r3pb0YbpjFjaLkf7TBuymDGYlZvC60jdb4zdeHOXvTcSWqACJ0oAtP9vfn5tRQlmpbO6HbT580Os6b4LeKcckNZYAOOyelLtpY1yE/HjnQiom3cg goOWpjjqftABHNKy B6Tj7SkrON8WPoO1IA5SC7cCpUP7rEa4OxTKmvFzM/Mtt6EsJ8xQAyP1L9tQE4w42LHHFSIFznxf7c5UyGOPQDWzaCKi4OHTxpRKG/v8AKgZSOR1k62njrQfKgHPJzRdLy1eHhz4vSZnN5mjHaeOyz1hvs1wUzHW6/DRWJhz286XvTE4o8cE/3O9CgY57b8qsxFqAs39/KTgmrIRj36pVTWlpT2z9FTopj37aMxSYiPfV7tJEdY8YoBDig4gxfrxpcZZvSaEr73sXzQRZb9zQMQY9 jsVNNss68vi3K1AQF/ pk0EShhnyf5tTaGFZHhefcVHgCA5HvioJajxI8sazzo/keS d6DmH3nSQTZV6o BSMZxLjizx/amCdz6A34VKcfxr4oTWJE7x4tirLfG624Z30qEWePmMcotnrUsDF5iLa/tCTXAL7bTWtTAnkfqoOQQjjhG 3bSj1uZz7/t6GET48nC2KsR8brbhnfSjBf3lPCpXJL5Vve dqBzM2DfAcduFJBsc7lznW9M0uU6cYmOGKRL9WnFXjm9E1Ofnj47U6aIg6za sxraKBa9wjHLHBsXp0hgXEWyvHXV/4ZHhnzH5RmYJ8s IDpUNSbrvdW eNA9ihRcseFfvfFSMrIj1/jPGllmiva/FpOsVebLbwrzq0im4nC53V4nGkKM6zjW/670xJuETF8DM7S0UtfbGXnx40xukJ3T8pKuJXuvCaDJC5ekfr43oLTNvtfuKDjtfgOgBUwVhnwn3SN3 Wg8O1QtLYE7p dc1cJkI20QfTzWADLDjYzw80A4AdgPqoGeI8futJIbl/KNr5ktUhqMxprm  2CpBqAOwHZjSMtCE6vPpyodeiccxx1takEryvebN93hQOdo8BmdqIZXPxPusYnRMcYxw/qgksp4az7sUc6xBO5E0BSxnnfN6yj54Rx/lXX5ugfFOy6E2w2viSfurQTaPtfbxQSL8e7GL2x5askdVxxE 6CwYx1iM8cRytSChtLys66Y6f8QWBv/1UM1If9VMv/mvBXMI4XbS2CyUHm3mOJP5yvQyg3gHWXL4O9T3EVnhJnjaIzDUVGYRybTrzi7QSTE27acKkQaIbcI8cqAIseAp3sIbxegRuM44jje/WmG2ottATm3Spe4raYgi3P57DYIgZtkn7cnWli0LQE4YL 37tRaaynaDnrPzSGLpHipIBY2OO2OlHGJCvdUxsh0qQoJhXZFosYSItiyeZ11oYMTw4r0twxWFCAOOBwn6oUsZRcaI6245pw6Ri1r2CNuWKK2uB3i/mlp4DvEfFGG7MY1SPSSmRMKqO0Aa6jy0zSQNyUR6yEacCW2pFnOeNIQgVYtxhbDEjfhTgW8B11vvRkGI4aL9RMWcUpM3l8knnJbrpFQARNNIZnhqB5HONM0GIJSG1oVddT 1nFgpJyz8ofvNGxe5/0YnlUN1UNIkmelznHKkYLBGmZe3G1OgpfeVQLlMYmVXsTrTKSB8zGb6YOrrQA4KxAi8uSn4jlilu8UtbF2tsflDqWGOnutRkW7pPzN VGWOt9dOmZzypKd5Nr9aXkXzUZKxJ5T0udCCjAGHbEae3b1YvVmeEkw8tKl4uHhlD5HOKiQWiDBq6HPSnQUtCrrc909IqRxeLg38fdR3B5u5vwiLUwhSkOuhL0cc2KEMIn37pjWW6ID2vFLCMQdD4wkjnpU98HTUJ4Pqk4zOMcTPmkWnfpzcH6zUgNyVhvSxFr2DGgE7PGl3u488eOHCKu9B1gehFppbAGO14Y4ySYoiK868I58f8pZxadvDDkzfsUNY5icTYCDnA51vNFTJq3SfN6bZwnv8A4bl lJy6l7XSLm2uKCjlB3tl3jFJxoIljjDrCTmiMS68No1xnviovUnG0IdlHpQkTMfC7XZ51HOJGd8t4S9LDzi OLuYaMUvmc3vpeI4acLVEErYYu2j416UAnIHd/LrHGoGEOeW1uFjp/8AO3oUkarHlYjdulMWIDHImP7yoWwRdHFx2hqVDCdS2Y5N2rWDC87DBveOdLwnR5pJImKvBwHTgL3mNooFFnkcXCM1YhzdeVKoTB9a8KE8YOcoU5EPWlAoe 78qnNc KluWmd49zQQD/5TzqQQxMHJfkDbpTIF4Y8x82omyMk/ETz qjOoi5aPNqZR5B6FmeWKVEYQza85dMeTjRQTUHv90Igzv/KdfqIk53jnPCowmFLS4U4bUjlLCahjuvKgnmzTlbeSasgbMfP5VyoWAzzFPirwLP8A5QQTepYUxZekvfLTkDOecz83pVFk8f6qCNAjkXO2nCrhwhO8flA2rxc6/tAUnCOlFRX/AGhYjN46l8s8quYXubzvV2tiGEezP73qzEbdOHirsyfN/wC0F2A6Ex90Wh/5T//EACkRAQABAgMJAQEBAQEBAAAAAAERACExQaFRYXGBkbHB0fDh8WAgEDD/2gAIAQIBAT8QwlQBytU201FUm0n/AIDbj/yADSRq9H31qmxfH7yVlUNJH/LAAAAAAAAAAAAAAAAAAAAAAAAAAAAFwqZU 22riU/FCR z50KHu4VPBM5fa1heEbYvf7 VATHgvrfE54VNGafWP3WrJN/W/sdKizkeAjqN6KyIDojxkbbMazEdQdEw9N9Am8zpc60jOIH WxDVkZI3RL9lxrC6cIu6vRQwi9 txbgA8OVRJDJe7U3gtwu47oNSkAxiToY9dnPGhgS8 3jjDHXOnYSXcb7B0WOVIofrv5SZxkGq9sfrpEjt53QTjE86SETFzuUsFctMcehsx4U0IQwMdf8ALpJcuKsvaHrRIdiezpPfZRh3k6TL1iONCBgLHCHzxoIjK 7PzQzlRcbh3TxXucLeJORgtSh2EO/LKoUcaisXhdWNKMi4S9JToiowjKNfJ9F6vsF/wfCpp4onSakjGE9B5RQiC8gc6DA5iaNoEF3Y mmAgsel1Zw3N6xOm/H17ihW19bS mFIijGNbO2tpqFocZ0x6TSybbI5z7YTQIDD8HzpQAI4 lHSphFww6aQOtMmAFSnsfnuoIJz3W9hRjLIY6g aQsMNfuFSkOTlgPmiXFK8sfv2FCDvnkOeEXUuFsJ7 t NKxGYvSPfG2FypUHMOTI8dcaMJatDzNmvxzppHJTmIdJaSBjfv6OrsuwH4w 5Uo5XOQfIFClBh e O6lY8biLPYpH2yz1h0ibkqJte0c/wBMJoSJsQ7bX1qwzJ0jupThQszpdzlTlRjUse3llt40NncRzCdWhBnbpI9EjmbawHu6SX1pJYZ24USRs/I5K/lIhtjs9kh40xCYzpB5qCF0PWy6yNcKLwwI1eSkJmakDOz0EvqVYXIx2PSpF5Tox3tQ8ie51kTjS4YjPRt1eZXM0aL41rEm41iekNYwpcBgi9A7zbd0q2mBOi bqUKF5j46UKDNflb3Sti74L8pQ51ArNtGwQXrTccwnjjhxSCkC5j2D0mXnUkA v6zi1MhduHVDTPhtq0jEJ44 n6KYnIkz090Shn2hZ34am2oNsU vZu2xRFFkfsPPKiYcD2HnjumpIM5OlnlMHOgeaPuV6VCLnpfETcmpTBsn12elRgXMnoL4aSAYyEcfy/9qOfLa4 mrkbI1Y0/lSAMfS NzrUhzdJtp/w2KsqZ3ea/biKUSxJoweipEMrNV7X4FRJcGPT0YVYDz1cObQsjZpf9pJRcDRk91YExt1DuRu21Lk237374VBEXDwOOeJUw70HKe193WoVk9h3I0ogIYfq9xbbKAXMg6MRpG KGblASYTHPM04WN1A9R0jtpuoGRTAb0d8uvCd9YZynW3opAVz73batt9BamY9IvyTrTILy zxahAzzHKJ6ycahmdpPZfZZLeaBoMumBywjfhRA3w6McLTjUAm/vHe2lYzs/euDhQBDjF cPXDfQKGd/nWgtDGlOJ1lnnk9Kavs5YRBywipOF4Y5rPVKkIyJ8T2OhSEltvxv0xasecDUH1voEGPucec476LCPwh3S FXybzrCmk9d9QiOMX4MdZtvw3Ui55yl99qsJZGi9dt JbtpSTLkaHxRBZUMnKfXotuKTlnfoP6HMoCQwP4aoVIjx0x7aOxoNExFM8W71iahQ5Oc n6KCgwQeS21w/KsUww5T  acwwXs yoBdlqibzOn5QITFua 3rVgHJ1X3WAyDtOfN61ZXMHS0W6RVkj77SiYcB5TyG7bRaG9eavfWi02y9YXWHdRBxP6 29bCp7vld1MWOTPOE7LVy N9QusUJkb45kuhnkUGTbzyxz5rYbqRTPnY BwyGlRdgPJQ8lDAMYk4Xvo9KEgZMHHH7lVmDB7bOtQldv3zjUUQYfeaSYqKbY1CaIOP1k7LUbGygCpUEz99Y6UFgbqDBS0yY/dN2FYzv/lAIj7H20FSY486xLffL1ags/be96CiMv8AkZPGolVxmeRY01owCZIjQJ0/axRwnmuPbVoFyiZ5DHqszb7W/WrAmYA35/f2g3gB5K aSDN5HoBV5C2/V80dwEaY8qAAWCNJ90RCX0B4plO/pn7qECZgjflj01oA3XldmKuHaiCpw/BrpUAWz vmkhGYj4oxp FfOFbU39geKCiGPb77GpWwdraINaCJffqvnfRNsf0drbJpGVNo9AX2 lREZEaB4qATIjiX99elJknH8aRq2wqDO9 O3FsyotQ3CJzyvOeGtQIr7v7rFHEPREc1mgEH8saWoBDfrSVLf48T13FKiTGR6HX0UYnIimSleIN2N9acxb502N 6kJFxR6f0pKs36W0FWvPWcNmMcCoCmQ 31cTFB0OeNEORI5Q8JpATD0HgoC8zfwHiiEwnLdj3V0ypZ2yNEfEUtf5ZvqedCc7U6PvxSpGcIjlqxUEQbAOqT9oIybyvNle7Vi xPVuLQRJss9BOdtaIzfLnlny1atydr1ydd BWETjQk99E89akUfsHwcs6gJb3jf27aZET9I KBKH6Bfb KI3PmPWtCG/XF50ErhGkfc6Am P6 aiVdpHf21ZCyAncnjHHVog3XmelmgrCk/za24tKi/ajRHxerAnbrOGwvhRBByPQiNZ4/wDk3j/rOKx/9mlAl/8AmFvGsQbQ5E92Xg0MYIOweTpnRJG8udgzwvpRlznsRyxoBM/38ollu91NgTbUl1tQ4GcY43X5jOeyoYM4PLVmY8qnLiMN/E907gcsZnROlKpSbmh5II2hakERMRPxvMfFCMwBO WfFXy6n77ptlTOGzqwbt6RGWY6QHWeu2aO0k8lSBDDzI9zpThRmsW2cmTQENrqtTnuYOkHYq6mwcNr7m1DDDNdZPHShzGEdGiN63gI6zQMGQcEu6yecKFtL208lCCRN54 l88LRQELLETt7rw7r76A7MeUrHS22p4Gbx Q3xDi0hF5DnGHhCaYw1jFMAXbAHimDJB2D3MMc8Cp9gI52v8AXtYvSL3ieXPmG6bYUbAkiNnDLxlRi1h6RoOG3ZNEg3JVw3YbrRk1KZeP6OjUk2jsARnlfKlgTD9Ol5322UQiheYSkPIfNt6jO6D9cqAjAfbNuNMA3tUZ7nOjuMV0vhp9agkccHWi3Ih0gqZhtnZcjDkM8VQrJiHe/wDcyiwjHDZkOk/WpwQwIOQDfeTnjhSFJtnD5hnepTLh/Z0alMN/DKPNBZusnrWgIMJI6aJ7IL0yDGWDqGiLwvQpzMaEGlQITAtx2NmJO2kYDA9rrM8iM6UImAeJZ38tTkmTr KEhDI5QJ63UN2obaeSpRl5tyhJ44vF3UykW/prE 6USYK HNknvUACWHS6XfZh640JSfWf5spUT667DbDLOoMsQTdmOcphbLApBLm6QHilkrz6HC0mPcqF1jAdp8xURzfniaFhcDbg3T0YzpIP23DTZhxpEyb2y3k/zk2aIjJBwkgPUM8ONFLgPM9LWXtHKzMLW2sSjdgXwu4hSXRjl1NYnbehZJIb8ITz7pYSQrLuzg5gcCslC6Eh1lef/wAxrpU2BB3V ZUgESwPGwvnnpg2avJY6yPKiYzJ0i3Fm1ChvFwvlOb5j1uGEyjMb/lQCzoWw3kaoPIF3rsoTfQ19C7UmzZj/LVi17dbOHGKReLQQc5dKUEZfvrdM9WVFyHqN0v1oVN0/vrGgApf8o7lYg3dWXtDzoEK1h7dpqRSM1Ok e9BjvNMXhVixNzm3w6NQYbhJ7e9Gu60YfymcqlDOIg7BZz5TzNtTwjKd A akAFv7 dajX20C8C1RhTL2ncaJG4PWPdMkZp5Rj97qQkz/T96f5SDDUXVi9yh2ThUE2ekeqDIZWO oaULTBnXHkxhhUQQWvPfDZjQ3JbQt4owOD3QC9IJ4MOkNKcFx/n5UoYZ/fTSjanWPRUL/bfb1oItgAcpPIUipvjmi6xU4 f4ev8p//EACQQAQEBAQEBAQEAAgIDAQEAAAERIQAxQVFhcYEQYCAwsZGh/9oACAEBAAE/EHDGSeVIP5XhDO3aDZT90S/zmbtBKrxgSiVP4v739fY4qgH R/44RiUOksU FQWfg/n/ABwGo0zMANVcA6k/IER icUOA0BRQN1CFahxDqmcltzH0bjmcQyQgIFQoCR6JLepvyAiP4/9W7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u5WG1/8AOgVN9PlTRL6m8hMYPwjT6UFXP50MeLxjWJCUIuyhbIQL5AATso/efzl S4itOzL C/OHwt1nQqiWEJIW8UF7ikrsky1gNPZMvpiSOFIcxxjiQEkWSESeEdopM6Qg7GTZCbKM8QHO zwTRUDo0yjkUluNxgctrdHHph5rARvUqj0qWmPpiKT/AO/9WCwJPQno/k6INgW6cIqD8F0EqpmG NATFGexcJAkCgBtsiQhUQFy2PaQlGQAq9D/AAQXGTZkBBbDiqFysBrXRMwhQ1gCLYQjUbWVMIL9xvzAsBAOAUeVlAJzSAFmWpire3HRlwZkhCgTRVLi6HDWFdMkEzls1ZUVGFSCJXq5PqbhziraNfRKEIdyS4S Dj0p4H/qwTZBnYghfbR0YIwBHxXi9XzBzHsyKRigu47eAxs1yyA2el zm2Ee5jgpzSbj2kPygE8vEMxcjCzzV/QP5yicCdya2vyT9Xjdbc9dgCpB4pBrs6o1EET2P4LoaW68fTE5/txeDLhLHZR1Mcj7zmIRDJxBEsCSN7y9D6YiioKIjwS m7NSA Iryn ivykTQk2hTN66zd3/AF/2z4S35x17BbVAbTQ38XbruJDxHiz/AL6ZqoOk6GPAE1RdDDuMZGlBC7A8z2yUMwFHDkqDeTd/BNQURPC5eHqi7HIC0IQwhHEl FlAb0qj6GnMzcBBuAdRqRHgn05LAeSoMTUsBQKBPZnhmKCKow9FhDEpAt4knJZs45JKIgKgdKxFvDZ4mYKYgIFouAobAeyNgiABEqB44Nq3kkKyOo1BFvQttSndt0ZBECgZgKgGOJM1AKhg1XgcSIcRREBJow9cfX8yL8iChVDmJRJJVGDCrJiXObKgZtSCQSaaUCDycYUQBWQq6KaYJvLVE0xdpnjB/A7Ri88btPmfEDnkBR8GeH wjI1YLxniUL4OBsK1FIuFCDYCTY0E0tQN5OPLcA/CEFFVBo7S4BcrUPTCobFx4UkZkZ20/wCAvNK90AlIIEMk6gQspqYAhDtqgE8ErYMfgBwWmr5OGDepMmTHb8t b0ZioFjSF8NZjIXrELMSgBB44Fn1xDyvS56VlxBgG8ahtQQhcSqc/wBeIzUrWYG2PQFBDeER1TLABQHf68/qfIkhwIeic94LOEInWQgMAfRpbcwCG OkD1vydMiCeJOGnFksvnF1oWx2ECpldUsnUKp2jvHUbOtwY8wAWktoYryGx7IARpylw8itOHtVHBcVG1gJubzNlZQAkEloLcO3lyD1bpklDjuDAwCnMNUFYMFzjhNjUKIy2ugd5RNIHYs4Bn0mnLENX/cD/cQnsfOPkLeRFWSAK6xTRpzKZjMeID/F4fM1FZGZgSBQ9csNlglzS0FAl8sNRlKLPLagKPQrJhUDFxb6RBBQc9tJ4VgoYHQGkOkvcX6pJ/wA1DeoXRbqi5UfTQQDRnokJsHkMKxBa4QZygrkcRkV EORcEqIQmScBVaRPeDA0QAVTGgfQzgVJTBQmBW63kKb1zR62WFUQCAPWcuUrwxxlqIaKnk l0CAFbSVAmjmE2AABBjLBdGDUv7kvrkEiNGiQnRJSabKJ5Vmw0Qbi1MTuhliDAHAC wFoLLKhqsFyz7btVoIhpk0BM4zHa pin8kfwP/AATSLOCAF wDekeQxshIWWjQJeWBKAlV/wAy4guB1lKGxZhhIR9Ft6M1JOLk6NhbZeE9bVkdQ 58RizjmDwC5cA4orMM5gUMWJC3iB4WSvOI6PC73xAqhEBFNIHiotv6YPPTaEmeKATAKHw9Dojf0MnrRZgET3ktJyPoQHCAbrzpmMoq5FY pBXC63iC/RQBdikXvXRMCMB6AGfvKTIogh4kt wAvCMtOIl4Hlg6YqzrCZgjgjB2f74cG4BTobVlNZMPPk5WT6/7wUPVcIACDqgAFRACVMqSW1epQwYhAvIbWcnFt2EoCClOD 1a1BhRUaMXecEB8xw7CsBSol4TH0drbIEqQDCF65olg9hwTHUC86 EhpPFGuEX05ECAMmIq3qUhK6kLKnGGagZOF9ARiaAZIwANWTPw6Ol5DxJdAJVhvEk0alJuFGvXpR56dMVydwSJjBLyFjRIaMukAfPg4opyEiUhII/oseBERIaYwBQyoKpzFhAEDyYhCCBZO0tyvUwt NJX1OnO/Bl7wqUAVvW0BJnsKvQB6QUTA1akKnThjYKnLvs flOI8j4FcHvrDqJVEBnCe8zKVp GxI0UmvOcMZGxY3RNIQzCFcsBWbJ38DbnvKX0THML6loiKi83BxNO Bqj4DvLi56bi0AKoedjjCr wo5/XCfRzO1c4Ex0EFQYVzmA1U4KVb8ZvXCvJp8JJooKwQXIvJvWVeJwYl QQfHNQRjWtWZAFAm6t5/riA8I0RQUyXOUQkLaFPlEowteb0g asDyaz9p9TlHoTSCYvBQlFQxnz9t1psgqy9pK0CAoDvMSqop9nQTSsWkEBpYN9P3mdhEYwi4UPG qOGzjEkhrDE NDhlUT ajgwEGw 88nNbqqQTECCecKzbROAQs0gBqbzK2R4SRWFE9nVvx9V2DTtJTDOMqtQzuc/AHdd4EB/AggOONM XOymDxokYcIFcfOT5NBmVI0QDVMiLYvpcFw8Jpg1N5ySLoe6096sFQ5OQQ1F1SW7dGKryn8Nb4W4AUuTEOrIk8laFpLqfC70fkawRQxpiAJ7eBR04hrhFE6rfeE 7ySscxBrGXiT4I0ig arDG7eVRA2yELIfhMo40TKZSUQVKsqtb2whZzwy4AD4CGcmmoHc8CLSUZ5ryf8T0QkAAAAA841GwsZTPaSFpq3jLxiYHjkhSii24cThFUigMWpklr9cwYiVsQgUgAL553vHMZLVWtuklt3ptQ 8P4kFIKD6Xm0M1CdgDEhEHwP/GAJVcygdYKBuZY3OMedMegs8gyxQqQvAh/AufSyLcH15HkOLA6DtJDRLV1gYdqYHiyoW6oCwE4mMRH C HDJywLIOkgERNIJt0DUODszhij1ErSd/P5nHDAaq3gSlSN1lrLP3OkhJNJKTpUQQD2BwpDUrWKBn5cxK1UQi4YehcwXwcE4DEOhrfvIqzjnTpE0IDFViqS8Bm3xPkQwApM32wkWUGMoxDlf4aM/Jo6GDQCBwMgzgJgASYax/Y0CoQeIRjJLN/OcYlasx0plpcJaRsfMVqeqopoTVRiZr0WYxh2qOeNhVOHiDK34EnCdG7zdptLRAcECCA93sYa3LAWBBW0OJSVYlUywtSMxFWI3ISCOpYPuCoTsbbxq5h5rmSZuIAw6ogEAHqPgoi4VdBFVSNFVT/Bypoxw7AJ6x89vaZI3FKk0X9GhpzB2iuW2KUFkTcRaw2gSafhr/8ArzpnSgCY9uj5wAunEs1JUtmkIKO4LClqSVB8Nw4l5OBmFgfQihxBHdVeUNAQSggpZhAvSQDhZQK/yc9BWDrkizUO G0T3PoLQtZgRqY c6SyjDMCUIJ/lHsZBLC0RT7AYpaoZDixTPwzSQsP3hGFDmkIUizAbjg7FucQgejyAgB94x tYH0AMaHg3ZwbFnN9sCGgjN55t96CQQIfiD35w0B0JIiEH4FMzOVrLlHOHl Ta 96RmEARkWfAuct3qeR4uB7QgrSFd3q3ZN7d3ixkapnYPMpDGLRoJBSPLJh4lnl0qBAYcSethUV5GUzQvJPcYCiGkgUACpK97GyAXYRShRzQhBrmw4YbGWqHgzpXy85YpAAgIPRykGhLMCiBgBUpWw BkvvbSlRxbDitCBMNF5WDVXIHTc5kiBlQFFGFPO A0j0KqbWwSx85kZFo7OhdH0k28uXZJBpPRFKxiLRv4SYLK5swyb5wP2oxB/jYhcG94QldfZQJTFfWR91VCwCieOMmOD9x36hnmFLUFL0tPNxlig tKzBSB4iT0fmvJ4OlAdREX f8KAUF8F9/wCFBVh vOMuKI/APeGAeVSouv3TOb48XQMRHx/n/CSiBCu8PJt5vIoYaf2M8N/9a15E7AGwL2AmL8DsYnlT04y7Y24AWbYQBKHLdWQqy3oekdGl4RP Gh46Jf0YRaSHBGgNij 9WPggwBFNPIrJI77QYoo/3ziizrfrCzaEIcgxkBhYK4VvvKWjTxSUxn4qitGCjdEH3GZ3Qq2JwuzMU5fi/AUhrvR2msLBbJA/SFyZGExUFV0eKnjHYBowxteFh5Z cLkcmg7TPpnlVAIBwlHpCvtD9c8WyBWQPZRPZnIPeDoBRD5Jvbj9bAWRcK/GlaBE0V SELV3yY ZQJAZLZrINK/QOXlp/PmNVK/pk1LJ4omClDcFA3LnJxGyw4gEPjRFLeaKs3zsCFGgsL24vAasCm6BnyLymbv3AozwZ9 HDOE9LoP6yIuFUhgkSFp6SA2AdZRtQrXQFGc9HLYziFWXaGPC1ocZjAK0ug4MKwXifiEE7hKlnv51/RqJZrtdbQ3Rzw9vVDlo3gh0Id 6KQqSwwI Fo4wMrkHFFAjaFCJxsx5kkreVJRIYxyzLzW2EPEaIvxJwTKf0rAc PvxYYfYI76gf0WCIAUf6hn4QjYVwGZJgXzU8B/rg2PLBwSmo Cmxoz1aENHNtbUFODrHZdlAkvaqarwZRrOjlQiFk1nrGjSaHwaxC6IAcewa1rweQ2S6JD3hHxtqzKFvrA/1wzoBO0WhCX2Aj3pTxTFhTVD6Fy8UMWmf3UqitT 9Ze2krJTC1dDpTtQyQ3m8IxD4AYhsYVE7 0ufH3t6egpVdRAeAEGdKoLwlj3GSchQnG914oD4q65VVxQXhkhQsox0MC95qPQaEx8Ue3zk2XKqWbgdSOBqOJsy/A6qcgF4wM/oUhTCDpxTWh69AYMqUWiBBHQXkm/B46/tgwAjkl4AeEtBq8 /DoS84njHdcgJBoAZErCOrYQwpheHTGYy6koghRFJyF7OE2b 9jwqPNi0G3zJbGijSKkQwxnSXWVPjAK8TL4nsCAigZkFekXYgPd3hD5n0zgyVVsBjU69BGKgqy44XhajWAplsZn1AuUa/jU/FvBNn9l5QohtgQOeChWDANyQ ueH0FtqGBOWhMJJ0Ae5YNJgmMVRpUQ3LVvaTNw3ggHGsJIQ2GkLQpQVHEUDk5E88ANZEZcGCKdEetHlEzh j2K0RI7bZf0wvtNEXLeqD8CZ/66GfvNLnc6/FK3Ch/lDulEorNdINqFUsyDkiXRrif6DvNeuPTV1Akdr9ZFQE/fcIqEEVjP7grsGSCCksRurqmUo2BiGSLIwTY/elMsi VMHQs5QrTDHGUECTxFRYnVlfbOvDUG/PDjoqepOQQUCEQUlDeLkVEnwrcPPsq2PT5bCNAiX8zQD2Il1LRgP0FHB sGTfQT0NZcaASMxhkLWh/6oLaaf/ObyZOgSC5RCmWNGoBwkI3aYKs/pWTToVfDCJfUS0cuH63ckkrRh 0sIuliVTABr7p2QSm bOnKHjVt4V8cF7XmYayIJvDGHAyi7N2sLbiFEpMz4BtbVhvUDu/iTXOUifCudOC2XMCuF8lD73LVRUeMMIagw/yUzjdCACgzRFg33syn5xa3HSNOtLnBXtVAGoiEEHNYcz tl2vmxND9fP8AqhVOadtUB7kGAmwhEo 8YgZq0wGwFohknL8V9zhQYQnlmFeKU8emU6iYDqzg1JWysdiuLgbQ6IiASPXovsR9CUY0cOC7J8D8BmHU5B892QMNX4n1O9fTIyqUt3Rv6S8IQEccjLj4c/8A5x8ivESGP9YRGfvPMokwyBY7YANO0AJBh2acoGg3qT44pcOydV1mzhQOXndIEo4WNNegBWtxIIKgfP6f9U//2Q==[/IMG]
[IMG]https://ubuntuforums.org/image/jpeg;base64,/9j/4AAQSkZJRgABAQIAHAAcAAD/4QoyRXhpZgAASUkqAAgAAAAHABIBAwABAAAAAQAAABoBBQABAAAAYgAAABsBBQABAAAAagAAACgBAwABAAAAAwAAADEBAgANAAAAcgAAADIBAgAUAAAAgAAAAGmHBAABAAAAlAAAAKYAAAA3AgAAFAAAADcCAAAUAAAAR0lNUCAyLjEwLjMwAAAyMDI0OjEwOjEyIDE2OjU3OjQyAAEAAaADAAEAAAABAAAAAAAAAAkA/gAEAAEAAAABAAAAAAEEAAEAAAAAAQAAAQEEAAEAAAAZAAAAAgEDAAMAAAAYAQAAAwEDAAEAAAAGAAAABgEDAAEAAAAGAAAAFQEDAAEAAAADAAAAAQIEAAEAAAAeAQAAAgIEAAEAAAAMCQAAAAAAAAgACAAIAP/Y/ AAEEpGSUYAAQEAAAEAAQAA/9sAQwAIBgYHBgUIBwcHCQkICgwUDQwLCwwZEhMPFB0aHx4dGhwcICQuJyAiLCMcHCg3KSwwMTQ0NB8nOT04MjwuMzQy/9sAQwEJCQkMCwwYDQ0YMiEcITIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIy/8AAEQgAGQEAAwEiAAIRAQMRAf/EAB8AAAEFAQEBAQEBAAAAAAAAAAABAgMEBQYHCAkKC//EALUQAAIBAwMCBAMFBQQEAAABfQECAwAEEQUSITFBBhNRYQcicRQygZGhCCNCscEVUtHwJDNicoIJChYXGBkaJSYnKCkqNDU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6g4SFhoeIiYqSk5SVlpeYmZqio6Slpqeoqaqys7S1tre4ubrCw8TFxsfIycrS09TV1tfY2drh4uPk5ebn6Onq8fLz9PX29/j5 v/EAB8BAAMBAQEBAQEBAQEAAAAAAAABAgMEBQYHCAkKC//EALURAAIBAgQEAwQHBQQEAAECdwABAgMRBAUhMQYSQVEHYXETIjKBCBRCkaGxwQkjM1LwFWJy0QoWJDThJfEXGBkaJicoKSo1Njc4OTpDREVGR0hJSlNUVVZXWFlaY2RlZmdoaWpzdHV2d3h5eoKDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uLj5OXm5 jp6vLz9PX29/j5 v/aAAwDAQACEQMRAD8A88tdMkuiDJDI8zSHf 92Eckc568hqJtGxJJHHbNvWEykeeMKMkDnvypq1bzxz2s9xMtuvm3BYiSyaZQSSSNw6Hpx6Yx3qWUW39kzDZZ/6rjGnSt2bGH6dOjenWmkrFqmnrqVU0IIbf7RasFZirMLleSzDb347j/9RqP7Ppgt1vvschtZgEjX7QNwfJBz h/CrWlJC1rlYbWQ7yGB0qSUgeYcHI7Y3fljnHD7COOf7QRFFwWTYNJkkQMOTjByDhsHPTH0qjWyMnXdPFjHC8VuYRnDEzB9xPTgHjoetYm9vU1197YxtZS/dhlcAKI9KkjJJH3Ax45xnn9KdclBaH/RraI7igb yXU53BRtJ46H65FCsNWS2OO3t6mje3qa7KbyLcB2S0ktXCB530iQYBH388dT785pJ7eNLyJ3S38pRIzN/ZLqqkAcEY5GQcenfrT0HePY47e3qaN7eprtpUtVlN0TarCkZViNFkCYJAyfT/69JdW6W7STuIZUCH5Do8gWMKpOFJ9evJx3NF12C8exxW9vU0b29TXYW4LxNcSwJAsi5aI6QxjU5wOQfQdf9oirFsy3Kqv2eyAPKh9JkOVI VgR/CeSPxouuwXXY4fe3qaN7eprqoYBqWllGi yxxnIeHTHfzAMZywPTcD/AN881fEFpeW0jBLXbLwpi0eUZBXPDDIU9 /Y0XQ7x7HDb29TRvb1Ndlbqk neZHa23lsGCyppkjk453A9MZ4zjsaiZnW0l yw29242LHJHppEjMy/K2T34J/xouuwrrsclvb1NG9vU12VhZwRKkMbpOFV1cvozuV78kHOcMD7cUj2yxOoEcVxtkAkdtHceX9c9h0x14HvRdBePY47e3qaN7eprrYLe3RHEd3bXBnV5A8ulOxAwB8px7fhUzzWQSRJU09I1KN5n9lSAkfxHrwOn1zRoF49jjN7epo3t6mu1hsQc dGFMcjbSdHlO9cYA9hnPFQz2UF1bmBl yzy4KiLSnXcgJHHc7iVP5fiXQXj2OQ3t6mje3qa7a0VLqAPJBbRspYSRDRXbDe5U//qx0o8m2uC3kyRK0QAYw6M M9ww59QfTgUadguuxxO9vU0b29TXVTTTxyyR2Ok2t9sd98n9nMoUgcjBPBwM47fnWZHqF0XlnXR7N1kK/8umVXHHHYZwf1p6D07GRvb1NG9vU1vW9zqTMzx6DayiR/MX/AELI boF9uOKaLnUdgt/7Btyw5/48juIJyM 3NGg7LsYe9vU0b29TWzPfXtkkEd3otpFt5HnWmwyY456ZqN9eMi7W0vTAO2LfGPyNAWXYyt7epo3t6mrF9fPfSh2hghVeiQptUfhVWiw VdjrtLjkbTiIzOSHHMV ID37HgjOeeuc1aeGee0YEXhUxNuC6iFBOT96M9D6gcVykv/AB4N/wBdT/IUl/0tf vdf5moitDOEbpHRxPLYXsluzP5chVowNRdVXJG4Er6lweRxzViRZEuTGTKsUu4p9n1AAlhnOTxuOFHLcn1PAGBa/8AH/N/17f0FJqH rk/65j/ANGNTC2p0bWsrrNHcRXBThWNxq2cDjPA68Zrkr6e8W7KzXMhkjkLACVm2NnsSf1z6c0aX/x p/vL/wChrUE/3Yf9z/2Y00tS4qzJv7X1PGP7Ru8YAx57dB071C93cyRCJ7iZowMBGckAemPwFQ0VRdkW/wC1dRxj7fdYxjHnN0/OkGp36xCJb65EYXaEEzYxjGMZ6Y4qrRQKyLUup388RilvrmSM8FHmYg/gTSrqmoIqqt/dKqAKoEzAKB0A54xVSigdkXDquochbyeNTwUjcov5DAqP7feCOSMXdxskJLr5rYYnqSM85qvRQFkWIb 8t02Q3c8S iSFR39D7n86dHqd/ESY765Qlix2ysMk9T161VooCyLEN9eW6MkF3PErZLKkhUHPXODUv9r6mF2jUrzGc489uv51SooCyLQ1K/HS9uAS28kSEEtgDOfXAFJPqF5cx XcXU0y5BxI5bpnHX6n86rUUBZFw6tqTMrNqF2SvKkzNx tNk1K/mVVlvblwpyoaVjg 3PvVWigLIu/2vqeMf2jeY9PPb/GkGrakpYrqF2C2MkTtzjpnmqdFArItrqmoLu2390NzbmxMwy3qeetC6rqKZ2ahdrkYOJmGec vqT dVKKB2RdXWNTRQq6leKB0AnYY/WmSanqEufMvrp8/wB6Zj/X2FVaKAsh8s0s8hkmkeRz1Z2JP5mmUUUAFFFFAH//2f/hDTdodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8 IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IlhNUCBDb3JlIDQuNC4wLUV4aXYyIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wTU09Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9tbS8iIHhtbG5zOnN0RXZ0PSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvc1R5cGUvUmVzb3VyY2VFdmVudCMiIHhtbG5zOmRjPSJodHRwOi8vcHVybC5vcmcvZGMvZWxlbWVudHMvMS4xLyIgeG1sbnM6R0lNUD0iaHR0cDovL3d3dy5naW1wLm9yZy94bXAvIiB4bWxuczp4bXA9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC8iIHhtcE1NOkRvY3VtZW50SUQ9ImdpbXA6ZG9jaWQ6Z2ltcDpiZDgxZjY1MC1mYmQ3LTQxMWMtODMzOS1kNzc0MDEyYjFhNTkiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6NTRiODg2YTQtZTg4Zi00NDE4LThhM2YtNGY0MjQ1NDc4YTQxIiB4bXBNTTpPcmlnaW5hbERvY3VtZW50SUQ9InhtcC5kaWQ6NjYzZDgwY2EtOTIzNy00Zjc0LWE5OTEtNzMxZGRjMThiZmI5IiBkYzpGb3JtYXQ9ImltYWdlL2pwZWciIEdJTVA6QVBJPSIyLjAiIEdJTVA6UGxhdGZvcm09IkxpbnV4IiBHSU1QOlRpbWVTdGFtcD0iMTcyODc3NzQ2NDg0NTY0MSIgR0lNUDpWZXJzaW9uPSIyLjEwLjMwIiB4bXA6Q3JlYXRvclRvb2w9IkdJTVAgMi4xMCI IDx4bXBNTTpIaXN0b3J5PiA8cmRmOlNlcT4gPHJkZjpsaSBzdEV2dDphY3Rpb249InNhdmVkIiBzdEV2dDpjaGFuZ2VkPSIvIiBzdEV2dDppbnN0YW5jZUlEPSJ4bXAuaWlkOmJiMzIxNmUzLTg0NWUtNGQ2Ni1hYjk1LWUxYWJjOTI3ZmM2OCIgc3RFdnQ6c29mdHdhcmVBZ2VudD0iR2ltcCAyLjEwIChMaW51eCkiIHN0RXZ0OndoZW49IjIwMjQtMTAtMTJUMTY6NDI6NDItMDc6MDAiLz4gPHJkZjpsaSBzdEV2dDphY3Rpb249InNhdmVkIiBzdEV2dDpjaGFuZ2VkPSIvIiBzdEV2dDppbnN0YW5jZUlEPSJ4bXAuaWlkOjk2NGY2YzE3LWEwZWItNGQxMC1hYmI0LTAwMDhhNmQyZmE5MyIgc3RFdnQ6c29mdHdhcmVBZ2VudD0iR2ltcCAyLjEwIChMaW51eCkiIHN0RXZ0OndoZW49IjIwMjQtMTAtMTJUMTY6NTc6NDQtMDc6MDAiLz4gPC9yZGY6U2VxPiA8L3htcE1NOkhpc3Rvcnk IDwvcmRmOkRlc2NyaXB0aW9uPiA8L3JkZjpSREY IDwveDp4bXBtZXRhPiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIDw/eHBhY2tldCBlbmQ9InciPz7/4gKwSUNDX1BST0ZJTEUAAQEAAAKgbGNtcwRAAABtbnRyUkdCIFhZWiAH6AAKAAwAFwApAAVhY3NwQVBQTAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA9tYAAQAAAADTLWxjbXMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA1kZXNjAAABIAAAAEBjcHJ0AAABYAAAADZ3dHB0AAABmAAAABRjaGFkAAABrAAAACxyWFlaAAAB2AAAABRiWFlaAAAB7AAAABRnWFlaAAACAAAAABRyVFJDAAACFAAAACBnVFJDAAACFAAAACBiVFJDAAACFAAAACBjaHJtAAACNAAAACRkbW5kAAACWAAAACRkbWRkAAACfAAAACRtbHVjAAAAAAAAAAEAAAAMZW5VUwAAACQAAAAcAEcASQBNAFAAIABiAHUAaQBsAHQALQBpAG4AIABzAFIARwBCbWx1YwAAAAAAAAABAAAADGVuVVMAAAAaAAAAHABQAHUAYgBsAGkAYwAgAEQAbwBtAGEAaQBuAABYWVogAAAAAAAA9tYAAQAAAADTLXNmMzIAAAAAAAEMQgAABd7///MlAAAHkwAA/ZD///uh///9ogAAA9wAAMBuWFlaIAAAAAAAAG gAAA49QAAA5BYWVogAAAAAAAAJJ8AAA EAAC2xFhZWiAAAAAAAABilwAAt4cAABjZcGFyYQAAAAAAAwAAAAJmZgAA8qcAAA1ZAAAT0AAACltjaHJtAAAAAAADAAAAAKPXAABUfAAATM0AAJmaAAAmZwAAD1xtbHVjAAAAAAAAAAEAAAAMZW5VUwAAAAgAAAAcAEcASQBNAFBtbHVjAAAAAAAAAAEAAAAMZW5VUwAAAAgAAAAcAHMAUgBHAEL/2wBDAAMCAgMCAgMDAwMEAwMEBQgFBQQEBQoHBwYIDAoMDAsKCwsNDhIQDQ4RDgsLEBYQERMUFRUVDA8XGBYUGBIUFRT/2wBDAQMEBAUEBQkFBQkUDQsNFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBT/wgARCABPAyADAREAAhEBAxEB/8QAGwABAAIDAQEAAAAAAAAAAAAAAAQFAgMGAQf/xAAZAQEBAQEBAQAAAAAAAAAAAAAAAgEDBAX/2gAMAwEAAhADEAAAAfiPmqu9nX1uOThtZMxbkYmR4bWet8Zqb4AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAATeHmuOnk2ucieNVf0Jmeak9X37qch507B5 aj053FpM57Pzx69NyAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABb L5vT z2Zzkqc4/r27qOFVlytyn28kysVe1HrOxjnwW iprQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAO18nys/T7dE9YtzY898ueS3tP3n1vKai9iFnOx9Z7laqLq md2xXz027lpKvvMxO0V31s8aZ0k1Oqaibs9Eko126IirGc93PWUtXPhy111U8/KQpuFS4mTK1XRZOezw 97jedrDBlVVb9yRO83t9e46sqvOkyKKrrm7s3andSLmxsqTU30xFzYu1JzK3d83N7JmbjuasqBq8yaHbsE5TsCtvs51qqvb6TOUDd0q3MZvlT5Fczdxt0C/8XyrX1 6BnTDcspe1PMut 556zzKtVozXmy9iEvm6vtufKFrmb63uRHzZuxqza9e7cuZ5xNrwzzYdJifI2uu7dz0zUQ2m7cjt3kDducjEyzaVdw5xijrpbZMnJ5u tzkbsSExsrRrdivrZOPCWnINq1TNyXk6WtnOL5 66dyi5U7Mksq92DWzIbWUtVrVhuScyMrJm4jNmphq1E/MjUl5kRU3Jw1pbVbQAsvnfM6j3 vKelfWWEvbnk873rnppZRHK11v0bY2bUQFVSpLLec5m76bOejNrK25mcM2JuzajCKx1MZsTU7fMb127N/MSczna6dVMTd5/OHq6VysZytrblGnNrsvX0nCdsTSzVm1l71Ec6WqucmHNad3RW3U89e7IxobW1t1MwlQKX0xT701VGc15mxaywlYokHOXdpEwtrkq67Gazw9DcmDw8PGjPMx0AAAALHwfK7r2 vXHWvrLeCp4S 13vLs M1F1Tqnsu5jLZ590rN24na7VJfTuc8 U7UNhVc3IgT0868 l5VFzOau 9zzsrkr6dNEbNn5nvq755ocdrO PObdjmTszmHS6vnE59OQ6X3U8pjOeXidBXLn57V1OynlsK9vQZPNZdZtXWzFzJ teZxFd zzjcQh1u2pgN53OnVOWGp0bgzn66dQ4Rcvmt69tnDnbulzp02cpUuYuusmIu7aznL1Wvd2Ttfu8lfQAAAAWPh T23s9mXPrS9FxGSb50brym9e6jjabPHOlnsTZ2VsYtplctvWHWgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAXvg Ta 33x5667hNSaj2dqdvys6Sedfl1e7ZTmFZk3dmViqK7AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAn L5PQez3wZ6 1O6dzqccVDpYbEjG1NO6WWZjU6srYyNm0V2AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAB//xAAmEAACAgMBAAIDAAIDAQAAAAADBAIFAAETBhIUERUWEGAgIjAh/9oACAEBAAEFAmTbaP1lDX2Jbzct50yUvjvpn538emRluctz/G9RnLJwIPPjPU9z/GdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM6Z0zpnTOmdM3 Pj9haGAcSjti0W3Ah09xkyodgpRSVi6Dfnq4ykEV7OmAzZuIsIxsFN0BrOvmNO0r4ull8y/6q0tJQwa4VjYA86CYrinUFq61qL vJq/sIefXlqHmU/xYVaqIr9BevXXXTbSta9WvhTjEXUPLoyM0rAK3 q k1 LxenLY7N5ZwYtU8xb3QsGZ1540miA5ihWyKFjyPAdjRjSn nkuBOgE4zundWF/NEgT9VxispBy0h535rQ8 uTDURENfoJHWJ5P4Y35oistefh9Zrz4xpfqjRBPyG9ba8/MCNX5qboB bJ LCqgCf8ANTmqDyDMtWdMRE36NST5qPQdQ82HGvK8lzeWgu2KqCRN3zukxMwDpm185Gv1Dz0JBPTwFUp18Wk4Uqsmp d ev1mvkTyOxxJ5DcdngCAFK1U6MvMxGqfy89ur1OrCUvOMCyPm5SxyK8Jj8xommvNxQSs6gaUdeM3EhaKA4CqCbS/T/ZHGl1AmvLt7jKgOMhERqDpaiNri/kJmEHz65s35/8AC0KBckiUkkYxQT2k7RxWJPzkR2APKsfGw82RACVRtrQvGufbnU7kil5ll1E3mDqrWNPtYwfKdQsUoFBWNXNJhby8G5Aplj6r/Ns2IdUgvy55yas1aGDMZ0ogwY0KJf8ANk7uxeXJZlcm1ZQz5uGXGe4OUTlwc5inmCv/AGnKLFvtFw9soearZwBFcqwOxbil9e7 zIFo6sLqFnULsuwN3BCRmw3uA7QK0zWe8TdtrEg9Wmwd3hoK/dhWwjcx0Re2eXUXtgCYZuA4xU2EijNaRCcloCGxOW l07gbJzWqwtyfIAthax39 42SbTqyk52zldOjeDjTFuCQd3JRfC01v75o6KzaiIH9pZZoLUs21bfFQ9oVhZYrptVNlIJkrM8GB3B5K1tksSZbD5tFsoG3TtxJrVjDbDVk0IRrXELK2cOBi1LJzT0cQYflXwUtoWhC2iAudi9q3rnyWG/sKQFq5YCCNozhNXex/G90X9JZMJhTemCUbQAnrKyUL 2a/M7JkiwHzrC3cObYM8c4AWTSsP27fxadM5uN27DW3zykw0Vo27lzchWBwGjduwgaxYYzd69KULlscC2jJw/8Ja OgXv1G5 qJOJbjZY/0vyyXqI7Ow1o4EPQfQCW4CUUvWEgZdvi8n6Uqy7vpNPhF7AgyB9FoYXX5vldu4tYT0u331LOaRC q67f9LqwDWXZK5n kloVh6ub6yN5MC4fT6BEnp 0QeompGXp5m1v2ctkFfjiNkvc4G K39KxHN iOOErGc7L r5wj64W4EJ0Ip6EigTesmdUdno2A9dsIp n7SjczRFSWw6vUrucnl/R7AK2u5vxvn9vkrHZoMresMpA93JjN qhvcL4WhPekYeXrbnSCivo Mten/6S9T8oH9XMuq29kgSPrDiG96kr6il RYO/ZfMznoiNKAviARXuJCna hJZnXtOJQXkENT9gScP7QmzL3fEkfU70Rq5ifec5fD/AIa1uW/jv8b18d/4/OQjsn/mXf52m6kg6V2mJAjKohasKoM9O1YWzyF9NUiZFD grjqWdmtYHrQFpmt3Cs6mfolTDlfJ72e6WYiC1gGxcvY6BY25NFqiDE5UWVZXrN3S5lmGqzdpVW3B925 aFxbTJY0ba4NbuFJObtVdpOWA4z36JbVsC/r4gK9XkvJ3KHIPoK4RWHSMDrblQFWi8oiuO7Ug2oseqbk8vJdq7gddqyAEqtqCMCPjBWMMkaNr0X5OP0gtnYdU4gfWOsO4RcsmbOP065zQ7gN8kdd30g5uBeTG7K8rYQfcA6q1ZACUha1cSNgoReblKZdcyDLpnCsCRuVRoNX6JFB3gWZwuFNNQtFf1zdhCMwXutshYpoJM gVnCV4lrVyxVlZBeIQW3bVxst21G2l7 sgQdusXJTrt2hLKu1m3qD7FI8mk5G3ponlZVX0x3tUJ2LNb8x2Qx1rPoZzk/enkX/AMpx/wDlZSrsMG8yvzKmCvEbzoysa8kLrOnjwlrQWGVa6B91VbKwmmBEalKGzVY8vCEf5IWjgpkZmMiuxXtlGdj/AFOe9fEVKa0MXzLohSQIIJKA32Ieffhi/nu47CrJXlSTCwsLynQjlBtVeCEJxPSOz2LzTp2AedNPP52UFS10FJ/6mSX/AGg89pqd09GcZtWoWbWwVYh6VyOouWD MtMT3XVr7io1rNzRp2q9dyaMPXo3Ny16Sw1MVk8cPysH1S/cuf8AVP/EADIRAAICAQIEAwYGAwEBAAAAAAABAhESEyEDMUHwIlFhcYGRocHRBBAyYLHhIzBSIPH/2gAIAQMBAT8BnLUm5eYuE3yZoyRpN7WaEhcJyVpmhI0ZGhI0ZI0JGi/M0ZGi dmhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JGhI0JEeaNH8RLN8G0r6uny 5xvw34xqeUrXfQ4P4D8QpZrbb6P3nD4X4u1Kfwy7v2C4H4vg8JcNN3fur6VzMZU0n9SEZKW5vmvIlHiSs3ybEnkglK0/RfIlGbjivUk7d/tZwfD4mLMsV8R8Rp0cOTaUX3sQ3ih8VpWOdX6Go nexGTZw25W2NuO5CTlzJumjVl5F7tftZcx8TFOvUzWWJnfwFLdRXp/JqbbflnWXoKdyx76/YhJySfn9jO7UTLaVikpS786NS2ku9rHLoiUsY2Rnk331a hqNK36/Izu1Ez8xTtpC4lj4j39BT3pmW9IXGsU92mPiU6Rmm6Xe9EZWrZqc7HxURkpKzN1kxy5jm1uR4l9 0XEbVjk1ZlZe1sjxLo1Lr1E7dGXioylSNSt2ZVv0FxNxcWxXvY5O36Ge9GpSTl1Msf1EuJSbHPxKJG63HxKsybdIU96Zq8u/L7mT f1M98VzMujM XqaqqzPqWyUsXQ LXft xKbj8vmRlffq19DKX8/J0Z3aiXK6M3jdGfkPiroKe5KePsNVbClzsfESbRnbIytbmp38fsZMTtI1Bzkr25HEmoScRzrcU7HxKMndC9f/C5oeCj4ug1HdM2 IlFNUVDmbWxqG7YlC7XdCUK2LijwcxYWmj/ABnhTHVbngtUYw2HUdzwWVHYahHmPG2mUrvqeHL1P8fIyhG2PC9xKN7ClHoeAqLdUWo7DfD5FRdlx5FR5lQ2oqMrPAmZJ7CUNqHgeH4GKT35iUGkPCJceRULsaghyrmZRW5cULDkuhJx6jx5ix2M4s8IlGI4wZJQXiY1BbMWPQeOVsbhj7DGF0NwSaFJbI2e5/jXuJYq1LujwI8BnFOhuLtM8MmRUXujBGKuxxT3ZghJIcUzFCVcjCJSZW1GKMU1Q4J7spcjBGETFXf/AJjzHw7jv3Zhu2Y817hQqWV92aW1WdWxwulChRpLqSWSolw7bZGGLs0Rw8WQlSpEYY0KGKocbNPv3UR4eLslBS2HDJ3ZHh0Y K77RpX1Hw fqPh3uKCi1uaI4Xf5Y72aa2NNPZjj4cTT3uzR379PyfDuxcOnffX7mNUaPfftNPn6/Ycc5ZslDJmHhx752OHNkYVucNUqJRUqsfCT3772NMXCrr3t9hwbd31v5UR4ai7Q4W7NPzY Hbux8O ouHTT8v7 5KFj4ak7Fw6Hw7eRpd9 wUKbfmS4eV pOOTIxxVDjaa8yUc235mku/f9zSHCx8KxR5en5X/r5f64c0SjKcdut/0PK2yn8EJSyV n8ijKtxc2OMvFXUjCSnfs pw4uMY7d0Wp7LvcUXlb5Cg7XsX9mEvIxlvXmThcX50Y PIjHw00Pp7iUJNtkYtSTYlPGKRKIo7tsUdlZxIuXLyY03e3dmLt13shR/6NN4pEoSbtd8xqWFCjLJM05VXfQpW2iUG8q72RPxTckjB7bdPsNqfIxdt10QoVJUKLrxjg6kqMbm2V0MNl7/AORw795TvfkU725GElFJGO78iauNIcJXt3YoPaxxbjj3zHGTt f2RTztCi68ZTd99SUZb16CU73KaxVlJciUG7aFF3v3zMa5Lz/kcHv31HGVtrvkKP8A0Yctip36GD X0Q4y2a75kVJLcwl37xxl075CTUUvb/JhLv3GL6Esq278zGXNc/8A6VPYnFslGb X0HGTXfqOMn37P7KkOLtujTWxGCrf/XHmic2ouvUfE8T8jeWz8hT/AEr2GqzKst X5JyePqZSpX3sW5WuQ5tOiE3J0 9xcVkpSW3fOhN3gLl 1FzQ IoR27ozWWJf/JlyXs ZqR5jnToUsht3Rq gp22OVewi1dLr9TVSHOnRqfAtuq/ai/UNRx8XQcFvZtFu 6FBKmaUR4qyqHKKe54Y9 ZFQbaRa/SKCi00aURpZZdRYrwI2h4f2p//xAAxEQACAQMDAgUCBgEFAAAAAAAAARECEiExQfBR0RAiYXGRYMEgMoGhseHxAzBAQlL/2gAIAQIBAT8BooVFKoWxaWstLGWljLGWMsZaWstLWWljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljLGWMsZYyxljFqRVmB017lNFQlXuRUkUwnnJXlpoq0wZ5 pTS1A5uTXMsacJLafsZUlCilL6WpK8Op pPPj y5rnqaE6iqkliyJ5HqLJqSJzr9Lbn/AGFXjJPQdSVLaG4nw3gvxPOZJ3G8wXPR g3iXzTuTrzeCec9xTGSuq2fb7SS27eaSKu7Ql4TL9 bFxvAqtOdSSec9i6WNjqhPnNSYmScwXc exPUc5KXcXaF3PjuTqbwKrnyUy9SefPYeGyWmkxuC7X0LuonOmheXc exMv0HMwi7nwXE77FLVTSLvLIp3JyKqYE2x16xzkEzPOncbhwXRqOrpzI3DgTnQmfylThSXc57l2jHVFTp5t3LsxzSRVToKcSUuXBdgnYVUk4lFyyTmB1RBf0J1kdUMVUwJ9RuJJJE5LiclzhMU7/AIJydUUxqiEo B22uRxkUDgdKZgUTaYeTytQYMeDttkcZbIMPJghGDDKtpHHP1MIlM8rJQ9SVhc3EoNUK3YwmkRSYyYmCFKRcjBhCVJhow5MUnoYKoSk0RKFBC RVJia1QoaJRjQhSY1LVAo2FA11MZRKYsOEUtJYNRx9zGDy857HlMI0cmFAockELwhEb EEeCUCUELwgiC1EEL8O/gqRKIHRiCNRKB0y5FKIF5VCIiC3oQJC9SNPef5HSoZrqRHPfuWjEksLmhaVJNR7/vBz e4qFSKnREYjmxbz57kQJR4NTPv9i1SUq3BbiCOfPcStUEZksW3NOxpPNoIzPOYFTBbKgemOv2YqVTjmkDUuWUoSyzZohbc5IsaEc e4qI/b9i3calDWpAlHPct1507eFqFTDkgt35v3IzIsNPoJWpIVPglgt35t2LefPc2gVMEYj1/wCRubtlKcQZxPuNVOloqTaZuaOR0uI5sbP37jeGtyGogSj5f84Euv8AnUSeJ6CW7FT5UnzQtl1TzA80tDlkY56CTiCMOdYEtCmnqaNM/wBOl0KGKl451LZ/MRrzqKlrnsUyiMRzYact83FTGuo1NU83IdqQ1iN57kqLRbT6kYyi2dR5qkSxSJW6EZq5t/kShPnQh7FsLyjWop3ErVCI5zmRIXlmBLOealKiOdC2fzGcjT2GnnnT zKTYlGTN083LXz9C3zT6/YWFHNh6kf ipamZKU1HOoqefArskZb5sJPHOpSsjTzzqRuUzuKd aHmMwJNfv9xSqk bf2NOI5uZEs0iWB0ptz/trU3fOdCmpwJzHMEtUmvPfsJzHsUuVJmH pLtb5uTsZUIdUKebdxvUT15sjNMSUppZ lEaOBV4nwuxLJku6Cc EiqklyXKJJLk9C7SC6dPpSk9P1KUtURECipeEJaCiMDcEqJ50MSYpwOlNQQRBhQzFP0p//8QAQhAAAgECBAQEAwUECAYDAQAAAQIDERIABCExEyJBUSMyYXEUgaEFQlKRsSQzcsEQIENgYtHw8TA0Y4KiwlOSo H/2gAIAQEABj8ClmfzOxY46gHHXFSp9/6KFSD2P9F1ptrSv9AVVLMdABjbCUjc3mi0Hm9sNfG62taajY9sKnDa9qUWmprtjb 6xxCJuG7BPuKCBriK2MRt6j eCh5ubUU31Hyw6xgKaDmMda4MhC2W6hhqTjLiilwXuCpb7a9cSZdpKPfVIkrX/u6EYzqZi3iMvhnh3NXXbtiORFVGv4l5grZqptp8jrhBCgE1VP7uhGhuq3Wpphcu9GnW61eHqCWBrd7V0x9oIWLtmZTNG5j/AHZIPT6YhzMpUScOP wqIytK6etN mHYbE1/us8L dNDTCZdhYFykTLwwF1KqeY0Pc64jkaViHAtCuvO1rEqPmAPnjNZiJrLDoAVsUggWU79cNaqpWONqIKDVFO2EgaWVF5qqXW/cUYaban8sZM3SkSkq1DqTQ UU20319sXS50RgNYVvBob6Vr2oRiVvFLgJSLiLVCbt9NfKPzxlEhFatJ4hIPEHLQ6dMZDL8O2R0eR2DLc7AtRRppWmPDd5nMjKDeKLS3fTXf6YzokjvYZd2VuikCvbFvxTjQkLcCXFRzigOm npiCRLjeXFxIoaHoNx8/7rZz L WMisuZali3GVtI0LWqBgS0FjVK71OhI gxOHkCTRyJElDpefX01xO2czFbQ3O5a52CE0FR6Yg MlYfEAtxAtxFN7q0pSuEfiI19eVTqKd8ZNkNz5mQxhfan eMy3xBNlTHyAX8l21a mJ0ScyNDFxG0X8Sjox/F1xBmsy1uVl6pq22IQk7cGUFgbdacWz/wDuG4eYHAlFfDkNrgKW/wDU4dZszDGFR2u5iKruNvXCy5h6Zc26pvzAkfphMtG5EUktiuRrSu MlLx/ Yu0t8tAT/LC/tUgBjibWLq5oOuI5c4wWBmtrGanHHy7NLxJCsSClbbranX WJx8TV40vpZT7t2uu2lMGsqhEHiTP5AdqClTjKTcdnWZlTw0B5mBoBr6emJ8zBmGmVGIXkpdzBe/riWWamWEZttmqGLUrSmAy5i Kh1AWrGoAt5utcZeZC8sspUcIJrUiuFmmLwqZljpb/ioT6YLyzRcHhs6Oh/eUQtp WIYcqz5ubhCSThqTSoB7euMpJHLc89NCui1WvSp6dsPxW4TCYRDlqDzUJrikd80VgkLhfKD3pUYy2TXNkySRhmcDSpAI3p39cZV2m8KUJfSlyMy160H1w0bZrxzmvhkFCNqanT174LRzhn3VW0uFpJ2rroeuIoXzLUe4F1jBCldyebbXGWzBnYLJJwmFF5TT L9aY4nGuCM3FGzWh7bgMFcuzPFpRm3xMy5jiCNSfKNw4ToT3wX JI4SK8w4ewKFxTXXbC59ZmaN2tRSmta9ddNsZiXiHix7QoASR332xHGczMIzlxO0nCHIKV/FjKrl5uJNPGJLWtFBT3r9MfC1ZvtHi8MRjy0xMfiPKtVqlLuS49cXLmL4qbgLVjWgpzdffENjPx9eKrDy9sRzy5l4WabgnwwVHrWuJ3kzNskGji0Wq1taVr8vfEmWysomaMc5cqP0J uIocqWfM0YzBhotPbFZXjjQTcBjWtG/21x9oETcSPK3C9EPMw6YT4Z2dbea8dcZP9oasyh2FlSFsuJGuvbHxGYmdbXKMAg/GV0130riYxTNKIp BzJSpp74tkzBTlXWwDmJII1PSmIPHPFkgMxWi6chanmr9MJnZCBlLqMQebemJZsrKrQrsJNGYhbmp9cZqKWdDLDCZLI67jptjLtfERNTaptqtddPTCRySwxyvKYVQk6kGnbEi5lymZsV40X17/AExPdKYhEAa0B3NO4xl5DI9JELkIntaBU61BwU KfifENBpHy6a137YysvH/AH8bvS3a1LsALmpAGENKxDzSbdcQzZxrMvJ1j1O2mJMyZ5lVZeGo4QN317YktzI4SNw6yijF6VKgCu1cPC2Y8Gr2zItwFp1u2pTELzsIo5VuWnmOlQBWg uHe/jMHKhYwNrranWu M0jXxZmFbuEy7/Wv0wIpvDS2pdVJp0pjLzwcSaSVzGYglSD8icCdQQ7SBEjt36Ek9MTyzHVPKibty3E60OFXLcTNIUv4ipUEdSKE6Yhk IIDLc3KNOUHTX160xOZcxIHin4OkYo3tr2xKqB5oowrGULoAw020xFw8yaSoGUWrXViPxdP54yA KeN81JZRotulRr30wkyFRGz2c1dNd/bGbVpZVaJQyHhrR6 XUN1OH8ZBFGOaZ/KWrSgpXtjKsMxpLG7mibW9NTjMM87fs0/Ck5OlaV3r9MEQsWj01b pNmSthkNadsQTZaiSZkBUSMVAVaAadtPpiFzxPBYmOWzt/iw3LTgScZiRqzNSnv/vieLxFPDN6tHQItp9OXSuEj/tHTlWZEF4NPxb7DESyV4SlrOWg9cQRZZQVPixaJUcwWoJ21phvF8BYr6u6XWEkaV17jTFZ1TiMpQkRxvdqKg0Guw3xAzSqUlJtRpQoFPfQYfLxVAglVSFKmjkigr70xMrXG6OrWKrKEoRpTQddsL/8AJzHVkpU0DA9O2mIYGo0dC8cdVvNteg5u EsuSdW0puGxnlZ GIU8atLVFOlNtD0xSMFW4Nf3SpyL12 uEgDPLU0VK1xmcuL0igPPTobhoD700xPGwmuCBZapzBfX0weDJxSq2kNbbqetdCa09cQSosgSOS2JVT72uwprthoPEGVBtPJse1f5Ynkh5srdbILbqab nvj4hDULFpw7WFtegGmhxlomBkjcrwxVanTSvXau BwLwl4oocbhu38WJg95UoLrFDIFIppTQadseNHzWeYutAFoNTXTpjKgSoqEeGGeMVFCNa9NxrjMTSZgoRNbIt2t4NdsS5pmR GBcWkRKDppXDSIlsw8O5yn3aLpX5Yy3FItArHGbGO3Vd/zx8UZjpPdvz8TTX9MSRycVTJoVMdDt00007YNVlduFqrwXcm9aEfXGUk4kfCapRAq9NNRT9cFixky0jV3W48350rTEt0NvCNG8Re1e unbDSzNE3h3NThOtpYa0GmppjKujUjozxklFFF0NfzprgLMiOjuYeAzqt5u2oCD5u2JBloVy0bCjCME/U1IwALJi0AqI4UcWdK6emMuiqwG0cojs2H4gMDMBJjU6S0O/vjMRn4g8oEoKeUUpr20wbJeEyrbzgKooRoB6E4sjFz0LczAe pxwOEeHx HbUfvKf5fLE/EsKhhM9ZU1J2O u/THFcWtxOCWjtQl60oab64WaEKrMrGplTYaNWp/XByrloxfaVpRQbq/rjMkuzcvjNEOWhHWmLGitbh8U3MAAvqemInWaMRoE85T236YPF4zxt4Rqmla1p74zgtNV8afixrynvrscCCCV5Xkeuq3UJ6 mIAiglVIR3iQcoFDzEainfEomWRED2sAKIG7aaYzOXyq CKySsN6UpvhSFPxU9RUUcfhNaYWdmtjktH3SDy0FR/CeuIs08fxKXllFdyWpsDXfGbfMWPOviSgONPkdcNEweJZQCVYUuHTCcOTiR5kiMBZUOw2pXl0wJoTceNfyMtbzpWmMxceQjmoUpS37v8A2/hwQAqOVC8vDGxoB79O IXN7I6lo42JqQOwxBYOTinhoWUG/Sum/bGcLaxaSSnlYc33h fTFJp45DIm1istK9qd8RHiCsWiEoKjBgaYtETUg9da7HjiexX3oBX88CfjES/iUAV9Ehd/DTZQAP8AfFsU7otQaA9sTLxbVl8wVQOlPlhOK9bBRQAAB WIwJzSPQaDtTXvp3wGaS4hzLza8x3P0xxZWufF3FobbBaoFB6dsQSq/PCKRkqDb/quLFmsW67lUCmtf16Ye Qm 2tNNtsEme6otIKgg/LESLIoWIEKOGux3rpr88PE8tVdrm0FWPqf6ymKB5cvZHGgrY3KQf1/XGXVoBbHo6aUdaEU2rsT1xxAG4xzPxEhHSnkAPzOJVTJ0uBpa tbCpJoNd/TGVkGVMfw9SqxyWjWn HbTbEUdhWwsfOaa9h0xCBAGli0Vy33bw9Ke4xNGMsyq0AgTxfLRrqnTXX2wz5aFYrmZiGYtq2/bthMyyB7X4ltd8cJ4Y5ucSXHetwY/ph4pIGtNKES81QKc2muIyYbgi0rfzk1B1NPQdMLEYGYC6vi7AqRRdOXf1xLM0IETvU0UV9r6Vxm7IjGMxZvJdS35YjnfLM9iuOHGwGrChPlwjIkRsuAuQde53OHLZRdWrbfyUvD6j5b4aJ4CqUFtstDUCmumuOMEVqJaFUBVPa7TXEJlyt 1XZtDRStQCNDriWHhCO9idLToTXXl/yxmAMuHLG65OVV5SuqgYiQZZikagCs3NowYa0202xlBJl9IJFk5XpWnbTTDLDHoZeJSR7qC66g0xmD8JW6Ph3XVIFpGpp6k9MXcDl6jia71pWm3piBJcrxhE19Gk20Oi6aDrTXbEknNzmvO1x/PGZipXjALWu1GB/lgleWTgJAHrWlDWuMm6pKHhSwXyExn1p3 ePjG/eXh U0xMseTReJWhJ1BtpXb0B WNcqUsA4axvQVuB7baYZzQXGumMpEFBjga8rXz61FcGE5eNb1KuUNK6UFO3TDo WeRGy6QERvQ8pGux7YEIy1qKgRGjktdeWm9MReA4KT8cJHNRG5gdRTE Xy8Jiil8yzNc30p mJ2ZGkZrSgVrdQ1dcZTNWD9nt5QdDQ4TLplw WAoInatfEv7fLBjMJh1TrryqR2HfEBCsIlSgZlt4jfeb54MkS3vYyj5jfCpJAspXUs55i911f5YnJQXzJGpNeq01p8tsf8oOHxOPTi/2l11dtvTCK WZ/DkRzxaXXGp 7piXLsEWJzWgrpr74zEIhDtKGF9e607f5YXg5RyqxJGy8StbT/Dt3GMuHyqvwhSt23Lby6afXEpORSkst7VOh57tdP8AXbE6/DJZLHZzeby21qKfpgs0KuOQ0jpH5TUbDGW8AqipaaUF1BQEG3f88NAY1SrV0pSl11DpX64zERhgdZ615LaGlOmAxy1QCG0l1qGuGtNvTGXh4SDhWmr84NFtGhx8MFqLw5JPS66g001xnphAztPWvPyCvcU1wJLEXQi1lRhrvTlx9nloro8obrA1LmrWu3t WFWLLPHIkvEasnn9G5e2JhwfOKCr16U10179MXnL/wD6da17bemIi0VUSBoCqvbuTr6b4ZzBezTCWjScq615R0PrjNGTLOHnhWMHibAU1PLrsO39F9ps2upp/VoBU mK002rih0P9TlBanb/AIZxl4pmT9mjS12F63XXPt16fLGXXhAXVEslDctQatt3od mHaNUEOYzIHD/AOknfrrp WMw8TRiRkIrwj1Qii6d tBjLNl5Y4lEUiSOYzrVaLsu /8AnjLqpjMgLXWqQfSp64yCzzqghmZpYyrVKm3agp0OMxSVg YU8RWVg1bLdKcvbfGY/bIxG8FkZbim03IdRTTY7Yjzs1vBCvayvuShptriWPiSJnHb4gNqaPXTm32/XGfEuYaQSs9oa pWygp0374amctkMhdJuGfDjuXw/ofTGVSbiSZVHlPw tFFeTqMRCMmL7PGYWWym2o9 2M8qTcaSdloUkl0Wjfi9xptjKyZfOmVky6xsebQj IYrK4jQxyLcQTSqEDb3xDl5JrmWYTmRYzbcGHz8tenXGbSPMqksqxgmsoBorA0NKncebGYzEpGbil1VUR6r7 X eIOJLZloeJw615blPbXc4jy0c9XMzO8qvLQaim /wA9cZxoM0ZYZzqddRT198TJmJOEGaNwxUnytWmmIMwmZ4JM8DtytVAikNsOvpgRz5j4ldQ0Vrani3X60 788SLkAYMvIoDJTff1PfBmM6vliv3DLeKEGmopr2GmMqCaMg2F3hmwjtpr HHxDRM0XxAY/hK9eWmM4OOWeZebRqE2Ecum1ejYy3DuSBI7WUrRxRqgCla164SMnwYybE/DXGTgllAMbqxWjEjxbvbb54kjOaVxc7OqI1JgUoF1HQ/rjNO Z4sUgAgUIf2fXtSmn8sJm5GjEWo4rPWtR/h5hh4U 0pI4zneJU33Wfi2xn0 NRmkZbNZvIFIptqffTCP9mI2WNtH031H I9sfZN ZCNl5BVaOUVOpIp5vbE0cOdWSRprhHRuUA1BXSlcGWVrpD1whmlbMRjLLpLU KoqP/LGSVnNscXNNIW0fhFdKajU9MOQL8/fcMwLiN67s36jGZkzo4mcH7o08/LbQ 2hwGzpQ5aOJEReHpst3Q uMj8O8aSwqUNsdH3brTscQZrMNoJhI7fPXGYGYvSSdbNr9FHKWbqbv0w8uXzEsamKZN2uqa269tqdsZXOvmqtFlwtioxfiW06inrviFI5vCWdZAtr1XxrjptsemuJ1bORGTjLIP3rVFpFKsK/nhX zFbLctr6b/8AkcZSoheVYw1FQ78L73fnpiAZvhpw8w0hjEZowI9MTtw1ilkiPh2Hlbmtpp/D2xmS0MQyMKhkYKFOhrT1rqPniON2qkdbF7VxkcpNcYw1ZuoHPdt3O1cTiOWTi5gMzXLQXWAaj5fInEfxObfkGXe6QM2qeYYysy5rhHjRSPytyBY7SNB19MJFmZ/iujRWsebilr9afd9a64lTI1gy0oFyU3 pwpfPtbBAFTi3kSv1u0JpX9MZcGw5lV87xkgG37wprr74ltYFvib49GtA4l1zCny06YzoeV51lHdiWYrTqPKOlcL8LBSIIR4TU9q1X/XfGUUzUeNKbNynh07aa/hxIk0pOX JMixJcLqt94bU uLv3lI40DQ8i6DXQjEZV2iVYwlrIRQByaaV6fI4 z4Zyvw0ER04el9W30Pp0OCQHXL/ABFQw24f8NMZyOOThZaVVNsF6lmt22ApXvTEhGWjtsomrUOux5N6dfrhZGV4zYwvZqgHpSgqO3zwk6RqsvxF7OQajm3pTanSuHi8Pe8hYmFXsGqdtcTS1S6RrmeONgGW48vvT5Yi/cCMRaBomJWSm79xWu2JofiwshmDx8EOLNdSNNPlrj7TZczL4tIolLGlm1T60H1xHwcy7qkAivYklurb v6f8M4ykMilnREllRPM9zfoFpXEBTMni5ioRbeW6hIFfeg eM0 mYtmWGMvsSNXP8vnj7QbmgVZG4YA5VWhIY/4emLb8w2n3UFTzKLx/h5vpjIUhl8TMNC0qa8Ty0K9O CCtwVvK/X3pj7Q/Z H8JzKqM3ONqan8RGMxBDBxXhiYlEEj/eQDSoJOp20xFmGYTEnmyxtFP8AyJ mPiVLQX5iylOSNS1N u CyGZaJxGSReZBYx1 a4gjMkpMkbG1V 8Kdaba7/XH2czBqeEs0Y2a5Sf/AFxN9pRRuqiX91SihffrhniiECHZAa0/uocZZpJuecB5Gk0sUtav5443DHDNSDXUgAn9AcSrm5THHlnVbF15m3p8h9MZtYaOkEjICxoXp2HemJIwY0VxR/FFKgjlPrUjEbcYq5ZlaPh81QKkL LtiZWZTwns312rtjMySTPGYVutWO6uoHcd8WHMVqt68OO6qVAVt9tfpjLMJldphXUqif8A2LYs4wOcMlixLQg7fe2xIJGRvhlt1fsLrR8scFY1vJYb9VpX9cRGV0hEqO63HsK64keSVVzPG4CQgjVtPX1xmIszOI5o9lUVu0/2/P8AuoRiGfLqsYzFsUSaMOWgG/yxEGl58u3KbRUf544KJe3F4rtXzMxCj/XrjMQyuqS3FZKIvm2J9/XD1KOzDQmNdDUGu2p03xlEtjmNxSK6NKk/P364mjma5jJe9QK3e My VjvhpbLqvv19sSxKt9qcJxVfKhBp mMpmW8KDyQzJaH66VHN3w32g1ZVD0Mkhu107/LD8RllVkKWlBQcpXTTTfCtxVqP kvoa7b6DXBy8bCwK7EBFGlpuP5VxNmjSSGKTiOTb5vbEmZaknCUBiKLaNenyP91P/EACkQAQEAAgMBAAICAQMFAQAAAAERACExQVFhcYGRobEQYMEgMNHh8PH/2gAIAQEAAT8h/vgyW5C1vDq4KAWvRkLJso7yfMRzLkI5Hjn8Wjq XI8cZAMCq GVBQmkcfvdytcT1nolvPu8dOsVQ6GfwDu0mVIoTkcjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyPHI8cjxyjfMAhmF5GycVP4ycwtYJp/tlETKNGw9 HJUbBeBuun7ia5SWERJ7eJhwVBqKm39fmI6LVKVK EPVGdYcQ4WGIEiCpeHxyj CEH9ygA4uuccP2Qz/kGR5MAmKggI9SB6uU8ICNAVy726tOMmcaqEevjqoD9MPnDF/P 1pe02KZyacEtke5FD jOz5eQWnP/AJZTL7zLgJLmoXxrjnEgRAtlING1ymA2ggERycD73jXfyMCmz0aPL4wSb064eIadE5eJiTSFIXYxaUhMuSVSzhfpufvBE52TRT1E3Pi7x6DZ4hUAq3KIYVpRo5Ait69JvL HQZwOWBRH5d51YaZwH Q/h/taU/8AmmAqpGXsb7eQ42cZoQg3QOqiq6Hyy4 IGm3sekFfcrl1MC3ZMBthOHjAKdikxd0AFd4A947N3Tq9Zolv/Cib /45SIg1BOx9tB4vGE5BTY6OwdtB1xk2pI0Kk1 sFaQ3BB/ccBTWpDtEQuh2c5qh6 E3lUjr8XBF1l39PpbdYHVgR MPQZX Um8UhdkdRHydv9Y7Byk2M1 sARJEpAayVZpfZlYokIaWmqKQQfoYd7foLRM0azgfmDa55ugoNjDca2L1gUcnbRpNc3WGyGYcKMWycw2ZVQ6qABUJGVOOLrOL4Z5EEVpOwvVwYpm9RDnwv9PmSFNUtwtf2sxmShlwUlCct/rjO6MV7i14B2HpTOB8stR8oXXu MZALnCE5g2PcziKZEMJxzop8usHIF8jBEcNO/G87GftxRctVI/LiJzSOokaI RmbuugEPKmrz8z7CJqBtAH/mwxE p4eONnfecAErOBf7uI693EhReuadhj7/ALQyxZHXOPFtIwZwXBP50dyv8bBIq6GJuDnNWckUp0n9wmdBiKtXT/kD7ib1iDUpu/nKifi FrQbhBfhvBaKYFPIsJVNH5dZccpiCHh/eFRhsC7rbJ8zhUr7Cv8Ap0HbLAxABua/rw/MsfHCfBIV/QuWzwS9viBf D7rITjB03XcJA2/jnBhcVQS2h8kxZAEJ0CSo9BtMQVuWsisrthAneXHQhuhXS8zaOxXQgtrrVpDAnaO4OqPGVGP0w0AboYbTCMYyCTR6OM5eNIm6lnjxwSUEqVCzppcXLtAlrtpEr25DdE6a2eWf2x2tsSdhsA5cYiHCo7QBsOpMmE40VJdm8R5z/OF/wAWNvnd4yumLxhQzidv9YVCgG226fmYGmOgCrpnYa6Nod5qqpaFOUECqFxQ1jKMt70Lzzq4iPaGprVCn9HvWIxKoIGQ0UIAP5xY3pKMdIivwp3M79iyQ8CG7 psXEMABAl1R7pB1ZMXlZFpXwBE/T /CDwgaBgAl0vzWW2zKEYjUesz9pj8AUfJ Z4wuJJ5HVT13bNoXvNF4sIGlPaWxmsKqzzWjZEgWKkauVlhKSGoOnFZw8YFrqYI05kfwcEgzSa4KDZ1dC/ML2WPCxs27XQ6aGOpe170ID VDIT4iDm47DR3G5XJktARsL/d/wCgd2hW4M2lVApdgeT6cT4CQ0eciob1YZtsObVlI8ta1xjTBMab0acAk5 5rjUB7vAGu3azJV2C7CmuvZidsNG3DZcLkwB2qxFClzXsbnZlbYMQGwgh9B 8oxtoaHSO2YYF4DSCt8iDLLixmYyQFFGJscuAtLe721Dsqb3xrFaVa4D9ZCUnma5JyIR1 7jJhaHVSKJTppbg8/l9EBjjrl5iOYFsXghnCTeaRZe6UO5esqlpDCaFKR/PeUI0S0Bw3HZUmAUDA1iobN67cWI2t0pbimy7cmGyIIQVcEeGuHONllJ1c9kMH05wTam Fd3wPW40WiQsoJdmhZLlDpVkwKKKksd4XQnYPTOhGkd8Z8dN/EVdIcejNB4pwCga5nGEoQceRDGthowYXAGlFt5GROesIJxoLQO5apTrKKFwdg0HP/pj3ef0mD08RpzYJaEGiiTaD6nOPS8097HmO9bYiZD5lA69vxZiiBMLQS8OhDy1gWVm2W1bZdlecclpkm5kIGjow1jOB76OnUI3w9mLOA6 o76BjE1gNPYYLoNdPb5m1z1HRNSKB1Zg4rpWtT9rrNAgayjDYvRdUx3SaCDaBBA6KO8VGoEWBUoBr1xie/DPyX X8sd3GFw6fQ02HESAffSCfyN/OEYhJjxGE6TB1srhnyIfR/jFvcHDV0So885q1hTxoUZtqO8l2eQRBIdCHc3M4Fo2wIXO37xiTJKr8H2dbzjDwlw5o662cYTkNwppECTaYA0ff86f4cMppUSqFenRt31iqTLaC9sAcN4xE26MQY7ezQ2bwrxISNoxS60hcjkkETLpBAeDrHoyMkNW rgolp4dMOD8J3lYGPBW2BpXVSYRI6u5v49f0ZvVDzxDJoKsHxgd1nkJ3D5o5wcGiROqG1xTIYXGxdviJsrG/ebWBtNV5RYvFwCpOkhIblYcedYs6chV2cpynu84lJel4Qin6ckCyWP1BtvlyqjeSWSsNp27yQjLqCqYwA4O7yQDkaZL3i5LCKW6AHODLBHmPg XLWPYLoOBS82OcdUwFgABAA0B5nE3aV7nQ5Vqc4ULWkirwk5TmgoiVnXDRy6fMSnEiAapIcBXRiFtE1W7RFu7LcP0xPgOg/ljQuO6i8Fd7j/0l nBBDs4bNB5tTGuLLwalxUXLnjPGctiDwDsOzEGBdpVgaaVA4fnNB0004dfFydu8EyV9m8Yup c42x3qGwUc9l4eMMo6hUf/MyYNWTkWFU4aQzT86cCGzIgfV3UL3YMloOvpFLXnxDNATqJRnTbJOhzd5P4lc2vpOc7Bh0sMwwDZ0T97mMRuUshPFuFh43yKJc N3N5CPqcpqwnJ266ysdaK2uI7bPDTxjV5UVBUEG IYCUBKY1A/l5 4NmjuOcpOT2U4yVvZWgsqnZyP4YlR4i54hJFZrZj8Mt CPK/oXebqkoJRdbZVrz8mMDjkaTSEqFf6MEm9Ml1W33qdPMH9KBu1P4GVdLvG0vwYoALmuyKMjvN9z7BX9GQkn/AN8BwB5pKk0Kcs/vBTocxBEEE qwdpLTmD0tnH3DRTAWqugKukBw7zaMkWSegg6bfveNbiMEC Yk36YvzLBjPmHkeXBu5MB23J3muJI JLe46neDwjBoq7tunjrHt2 QMN9dc3vBla2QUmkHj3AyukaLd5r9/MVgI43afq4UMW6XIvL/APXzKntW3Gwgb24M vSJxHfL68ZWKnSyppGy2Y8ULg3JP EzxnAwqiID0cZENlrX0PTXx3k0oGPJB9Pzm2nGUNg6ah1kGO2BBJaqFunbFHuiFuipyVOweTLpQAg6ShR1dxTKIrYONPKug5kwGe24h6AOOo5xwCSq3cOy9037rCxALR7sANO0fMY2NV GBajOnGxwXoahRsCCB1O3GTuGXUkdrKOO 8qINIdOKGltu8MnYkQAjNKB7/Wd0a8jU8jrZkX8mqXVon7qe4apAV 7VOvHGENplvLQQ6SEQrZnslf5V3bdOT5rHibODblb IacHPeUUtpkbDGv ODLEbIdB0RrfmQ A NM7l6uGX7iZZpjkPl/0of6cYbU3AKudup4NXzGQYMR1H/SnuR6YskxWbD/ALYwcZIFt02Fl9kM6YXVNFXFDViDbpDKz1awk8NLV 2Esnac02Y2VUH b2QfwFDTbSXXbEcLFppsa Jx3ib9g3ux4ciYooi6LCKXC2hbzhWaPi0RHscWawQogdgdVNU3pPmI59CTyG1uXf8APNrwImSaemuNpvBFuzDTreOD4u8TJkq0aJLRrTrGTkm9CrKv5OAJCyoG7hfRduNYbpk9Ipo7DjzBakJhWwF5HBlTPeZIihxYFpxlTAn9k98ZoJeguuC/1cPo lMYTvxOKmHBWxVV9uPIRMDUzTygGo6EYaQmR5GhanHWTtk5DcqXacudzFqapa/I g5NozFfeKKAd9a7wrbJoECSaRgg5MHeSBEouOwFpeeTETKto09tlWvPcmfw8yQq2ocAcmPydsCVKHJtB7eshHRPilQwaBScFmTX2fHGIk/SOZPpvXIaY esDEpF9MNP1jf8gjYFlIjplHDiyNR7aRbv3XFxaERypKwuwvMq5fAjLOQc9vxmgm8CKoo2YN89TLgEwzchuO1UYSbxIslfOgD gwZgrDLXfxF7FwwCjqbgY8zVY9ZX/V3qXIda5f8AOcoGLe3wJq/jNOov JqMJIgfkwkyt5TY6kQ7tuNYZC32WsLEY1T29QorQ6Za O3G3wdoZ11CuBs0avLxg8tBL4pqSuyTjGxmnI4Cavwb5x8KqrOYnPj8y98ZKJ61jr3N3FyKaq3Qmk76hhhMAYEbI93bY/OzE/RCEghjp9dM4p7BDun8ZQoF6EkE7gbOFMjK0IG7LSq0R5GGLD4Qa07bzwznLdrSa8p2V9fZgXgBBRQrsU4LlMN0reKL77 4axeKiJRsDrsJlZvFFeRGDjz4/GCq/Z/YOJ2LUhMoULAzWXcm6CTjH1BJVreMeDmW40hNsdB1K 1XlyjVPJKLOwRJhSLDeKJNk84zvvV8aNzpp mMi673ahziOxyZaVe6N6Kq/nrrIOIMiyjcaaD0YdsIoJVQ4ajR/beUJLsR5dItFeWVcpKa2AxU/wCDNjXQIkGrWS2aHW831tWeqJbRdVIveWp1jyak8gTyayik7peoQCbPwYqLFcuS3iN73wdTQoGer/xH/bhgHCIbCh8Qo9cEooE7ROZoLv8Apks/jSCDk0fhlCPbrsleUhy1FETQOSc9v23ltDr9I7CbWfxzlFPG8geKX HDFJ2LGJSiImnVybQs68SkK10yR/jNkdMLH0fcURxTQQ269Bv cEbTRpPXigfvN2KBOw Q/KaxQHCApSG q/nWCKFtvwT0bwNPMmNKoNAd/nf7/wBqFLuYWTQMOQl2xo/GHajaEA6 qDBOAAOKjYKOv4GapYUdSlNwsMJ2sQfR3HV mDei57MC7a01tMNfi DsHvJ/DrBlgod6tjrjFUvsyPTgrXweTzESpvgHnYc5ExBqvoy n M1Qoy4VV5SmYccJHdB/hwNLrHv8AwGuesCSF0vsemmGwM11Uy9dP9qGwVjog3Wy Hk94PnZ3YaizTqNM1HCii1G/Wftk7BCkAkQ0hRG33HmdOWXnRJ23jOxRfyEUb7/TcMNTUM0 pt0MzntoloTuvR1kk5ZSfwA/tk0CDR79E sdKSNSexs841hWrrROwOkuVD qi2g5U1b1m9x7zsDNt/WIyGjQIC tBqTG5QIBCIATrg/2p//aAAwDAQACAAMAAAAQUjYeeNBLbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbGIUOw Kf8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wAJ86xzKwf/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/APPp4S/JenkLVTGx 4qqFE7DICh82oe9ZvD3EiulbRdh5TfPAhv/AGz12YS5sN4LTg66fxI/hLUEO2bYVDQvoAF8pIM2bCVo9npZ8f8A/LEhBtxan7EbPZsc36QbQ4YUw9f1kYiaCcGF8yKqe9OX4b//AP8A/wDiaIm9xvpnk vfeVD98Yo6OyiXq6Z7vN/EWcpjoGY/sEw7/wD/AP8A/wCQbANtCiP/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AFsaXzxf9r//AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD3cXt/KlOf/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/AP8A/wD/xAApEQEAAQMCBgMBAQADAQAAAAABEQAhMUFhUXGBkaHwscHR4fEQIGAw/9oACAEDAQE/EEcyl7tKICmb450klSKEQE863T3pRgyOo1unvSr0SVunvSkkqRUdlPelIiotvV6JP9xSJYjnSdlPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70rdPelbp70oTzqVoZKETGZZYLowhFS5NEA2bmNEbZ3odCpAyiSAYJCmoWxMUN1SVQiJSJYsAeCpySARUIRELXIOrGtQxZtC7D3zSPPixnlw5TvSTDm949 lCBwkROsBPLNt8USRhXXiqcoLUNNFnwMcypNIgYncfcxrWmCzOZbLxgyPmgUav8A5afYomLnSlk8Xdq495FRBos7Xg7nsVwETjODM85OM01LqVZqe8Npjnw607Nro6THHPallBc48Lvl TNIk4v1hi3POtObDli/9phlljYIGc9NL9qkoRi3MnxTwdX6asHFrpMFu74xRLgH61/8sreZRPHEdMr1tTKGjHmPmkCUtcjmNCN/qhRco2Bhp1iKghO0fERQypw88qcw9E05WaTzUetZtTqI6t1FsXP2KlOFxjw 0VFAuId18hmggGV29I90pJ1fxhpJJenBGEO/6HWkgNE9UNXMo/Yq1cI YFjua06BmPKluUS8yjgRd04Fs44ne01gQy7C/knOkmURnsL8/eKA5GHa8x8Pagsi/gCJ QoMQH6n1UzpE S3Zn1oBLUHacm9ntTYGcezURgx prHCaAwXtPeIOyPrRgOZ8Me ajiWXx7qwUpCLk8cTG9YhaB741x0 pl4tb5H1bzUKGsfGPPDE4pw8I447T4jehyAvpwwP3UjWU0SZ/B 6EgGzzntSrw57H77NKBG3H6q8QSqdlPpeVRCVpQ6KctKWJ6OtIgjhPVQ KtiOPKCP0KuA8vP8oZhMB6M/j4oTa/xWPBNBGYSdh1jjTFOpg8/RQkEwT0ifeTQGofFmO8UlxaUWYYO79E1Mny7DfnNs0zA0HvQmUZFdr9HVERGaMyWs10Rw2pC8D8mhDBfxeY KVeFuLgkmuv7tQqGlv87zy60kGDBHkH4RqVILX8KfXanAGZ8R 1MgjKdAu8u40s2x80eIZpSsYQ9HpotSGE9BfM1hFz9q9AWJ989q3hE7EzHeKXaGoPGWG3RnlSOvOmt sR1ONAwbED4Hlab3oELlr0n3XamCGqHxfyezAyLIjzz/ykpoeZCPPsNAAMP6keH6moBsfuJi tTmAz/V i23oZYLQOuuPvE4o0av8AlLAk48dItzvrGKBb6X I71lSjHNkDylLFYhXODP0c6tCL7aYzjid7UkhNY8TNYAySeP3SalHF/0M86iiElm7aXnOvFpzqm99c/2pm3w6Qb9fNJOSkc5tzhZ2zUYDuL8m1AEM6 8q5pQ5yA45RUTkeeV2szUWKxi7w3vhoYwR0/KZKspOuMT9ce1HUE24yPlHjrU5zvroZ4lnOIaFzhVNcyzm2RmKmWihMSVud8vV5zO9Flm8F1uv28dahLtTCbl/M9igFHT d6hizvi034Y2xUPMnmOvXSiWKXR0B9xzw1cnP9TM3vJzqQjfXPF 5xV45EjnZ6uN6gnL8fp461HBfPPnUKXffMuHnOKhOBHS34VO/ukQnHPFntcpUniznMs35zilJeI6QY7TQacuu7Hle9F8uV/7yoZZf/f7tUqcJz0DpiMVqmY0dZjvDbNLBujJiz8R0qFZ475u/r3pb0YbpjFjaLkf7TBuymDGYlZvC60jdb4zdeHOXvTcSWqACJ0oAtP9vfn5tRQlmpbO6HbT580Os6b4LeKcckNZYAOOyelLtpY1yE/HjnQiom3cg goOWpjjqftABHNKy B6Tj7SkrON8WPoO1IA5SC7cCpUP7rEa4OxTKmvFzM/Mtt6EsJ8xQAyP1L9tQE4w42LHHFSIFznxf7c5UyGOPQDWzaCKi4OHTxpRKG/v8AKgZSOR1k62njrQfKgHPJzRdLy1eHhz4vSZnN5mjHaeOyz1hvs1wUzHW6/DRWJhz286XvTE4o8cE/3O9CgY57b8qsxFqAs39/KTgmrIRj36pVTWlpT2z9FTopj37aMxSYiPfV7tJEdY8YoBDig4gxfrxpcZZvSaEr73sXzQRZb9zQMQY9 jsVNNss68vi3K1AQF/ pk0EShhnyf5tTaGFZHhefcVHgCA5HvioJajxI8sazzo/keS d6DmH3nSQTZV6o BSMZxLjizx/amCdz6A34VKcfxr4oTWJE7x4tirLfG624Z30qEWePmMcotnrUsDF5iLa/tCTXAL7bTWtTAnkfqoOQQjjhG 3bSj1uZz7/t6GET48nC2KsR8brbhnfSjBf3lPCpXJL5Vve dqBzM2DfAcduFJBsc7lznW9M0uU6cYmOGKRL9WnFXjm9E1Ofnj47U6aIg6za sxraKBa9wjHLHBsXp0hgXEWyvHXV/4ZHhnzH5RmYJ8s IDpUNSbrvdW eNA9ihRcseFfvfFSMrIj1/jPGllmiva/FpOsVebLbwrzq0im4nC53V4nGkKM6zjW/670xJuETF8DM7S0UtfbGXnx40xukJ3T8pKuJXuvCaDJC5ekfr43oLTNvtfuKDjtfgOgBUwVhnwn3SN3 Wg8O1QtLYE7p dc1cJkI20QfTzWADLDjYzw80A4AdgPqoGeI8futJIbl/KNr5ktUhqMxprm2CpBqAOwHZjSMtCE6vPpyodeiccxx1takEryvebN93hQOdo8BmdqIZXPxPusYnRMcYxw/qgksp4az7sUc6xBO5E0BSxnnfN6yj54Rx/lXX5ugfFOy6E2w2viSfurQTaPtfbxQSL8e7GL2x5askdVxxE 6CwYx1iM8cRytSChtLys66Y6f8QWBv/1UM1If9VMv/mvBXMI4XbS2CyUHm3mOJP5yvQyg3gHWXL4O9T3EVnhJnjaIzDUVGYRybTrzi7QSTE27acKkQaIbcI8cqAIseAp3sIbxegRuM44jje/WmG2ottATm3Spe4raYgi3P57DYIgZtkn7cnWli0LQE4YL 37tRaaynaDnrPzSGLpHipIBY2OO2OlHGJCvdUxsh0qQoJhXZFosYSItiyeZ11oYMTw4r0twxWFCAOOBwn6oUsZRcaI6245pw6Ri1r2CNuWKK2uB3i/mlp4DvEfFGG7MY1SPSSmRMKqO0Aa6jy0zSQNyUR6yEacCW2pFnOeNIQgVYtxhbDEjfhTgW8B11vvRkGI4aL9RMWcUpM3l8knnJbrpFQARNNIZnhqB5HONM0GIJSG1oVddT 1nFgpJyz8ofvNGxe5/0YnlUN1UNIkmelznHKkYLBGmZe3G1OgpfeVQLlMYmVXsTrTKSB8zGb6YOrrQA4KxAi8uSn4jlilu8UtbF2tsflDqWGOnutRkW7pPzN VGWOt9dOmZzypKd5Nr9aXkXzUZKxJ5T0udCCjAGHbEae3b1YvVmeEkw8tKl4uHhlD5HOKiQWiDBq6HPSnQUtCrrc909IqRxeLg38fdR3B5u5vwiLUwhSkOuhL0cc2KEMIn37pjWW6ID2vFLCMQdD4wkjnpU98HTUJ4Pqk4zOMcTPmkWnfpzcH6zUgNyVhvSxFr2DGgE7PGl3u488eOHCKu9B1gehFppbAGO14Y4ySYoiK868I58f8pZxadvDDkzfsUNY5icTYCDnA51vNFTJq3SfN6bZwnv8A4bl lJy6l7XSLm2uKCjlB3tl3jFJxoIljjDrCTmiMS68No1xnviovUnG0IdlHpQkTMfC7XZ51HOJGd8t4S9LDzi OLuYaMUvmc3vpeI4acLVEErYYu2j416UAnIHd/LrHGoGEOeW1uFjp/8AO3oUkarHlYjdulMWIDHImP7yoWwRdHFx2hqVDCdS2Y5N2rWDC87DBveOdLwnR5pJImKvBwHTgL3mNooFFnkcXCM1YhzdeVKoTB9a8KE8YOcoU5EPWlAoe 78qnNc KluWmd49zQQD/5TzqQQxMHJfkDbpTIF4Y8x82omyMk/ETz qjOoi5aPNqZR5B6FmeWKVEYQza85dMeTjRQTUHv90Igzv/KdfqIk53jnPCowmFLS4U4bUjlLCahjuvKgnmzTlbeSasgbMfP5VyoWAzzFPirwLP8A5QQTepYUxZekvfLTkDOecz83pVFk8f6qCNAjkXO2nCrhwhO8flA2rxc6/tAUnCOlFRX/AGhYjN46l8s8quYXubzvV2tiGEezP73qzEbdOHirsyfN/wC0F2A6Ex90Wh/5T//EACkRAQABAgMJAQEBAQEBAAAAAAERACExQaFRYXGBkbHB0fDh8WAgEDD/2gAIAQIBAT8QwlQBytU201FUm0n/AIDbj/yADSRq9H31qmxfH7yVlUNJH/LAAAAAAAAAAAAAAAAAAAAAAAAAAAAFwqZU 22riU/FCR z50KHu4VPBM5fa1heEbYvf7 VATHgvrfE54VNGafWP3WrJN/W/sdKizkeAjqN6KyIDojxkbbMazEdQdEw9N9Am8zpc60jOIH WxDVkZI3RL9lxrC6cIu6vRQwi9 txbgA8OVRJDJe7U3gtwu47oNSkAxiToY9dnPGhgS8 3jjDHXOnYSXcb7B0WOVIofrv5SZxkGq9sfrpEjt53QTjE86SETFzuUsFctMcehsx4U0IQwMdf8ALpJcuKsvaHrRIdiezpPfZRh3k6TL1iONCBgLHCHzxoIjK 7PzQzlRcbh3TxXucLeJORgtSh2EO/LKoUcaisXhdWNKMi4S9JToiowjKNfJ9F6vsF/wfCpp4onSakjGE9B5RQiC8gc6DA5iaNoEF3Y mmAgsel1Zw3N6xOm/H17ihW19bS mFIijGNbO2tpqFocZ0x6TSybbI5z7YTQIDD8HzpQAI4 lHSphFww6aQOtMmAFSnsfnuoIJz3W9hRjLIY6g aQsMNfuFSkOTlgPmiXFK8sfv2FCDvnkOeEXUuFsJ7 t NKxGYvSPfG2FypUHMOTI8dcaMJatDzNmvxzppHJTmIdJaSBjfv6OrsuwH4w 5Uo5XOQfIFClBh e O6lY8biLPYpH2yz1h0ibkqJte0c/wBMJoSJsQ7bX1qwzJ0jupThQszpdzlTlRjUse3llt40NncRzCdWhBnbpI9EjmbawHu6SX1pJYZ24USRs/I5K/lIhtjs9kh40xCYzpB5qCF0PWy6yNcKLwwI1eSkJmakDOz0EvqVYXIx2PSpF5Tox3tQ8ie51kTjS4YjPRt1eZXM0aL41rEm41iekNYwpcBgi9A7zbd0q2mBOi bqUKF5j46UKDNflb3Sti74L8pQ51ArNtGwQXrTccwnjjhxSCkC5j2D0mXnUkA v6zi1MhduHVDTPhtq0jEJ44 n6KYnIkz090Shn2hZ34am2oNsU vZu2xRFFkfsPPKiYcD2HnjumpIM5OlnlMHOgeaPuV6VCLnpfETcmpTBsn12elRgXMnoL4aSAYyEcfy/9qOfLa4 mrkbI1Y0/lSAMfS NzrUhzdJtp/w2KsqZ3ea/biKUSxJoweipEMrNV7X4FRJcGPT0YVYDz1cObQsjZpf9pJRcDRk91YExt1DuRu21Lk237374VBEXDwOOeJUw70HKe193WoVk9h3I0ogIYfq9xbbKAXMg6MRpG KGblASYTHPM04WN1A9R0jtpuoGRTAb0d8uvCd9YZynW3opAVz73batt9BamY9IvyTrTILy zxahAzzHKJ6ycahmdpPZfZZLeaBoMumBywjfhRA3w6McLTjUAm/vHe2lYzs/euDhQBDjF cPXDfQKGd/nWgtDGlOJ1lnnk9Kavs5YRBywipOF4Y5rPVKkIyJ8T2OhSEltvxv0xasecDUH1voEGPucec476LCPwh3S FXybzrCmk9d9QiOMX4MdZtvw3Ui55yl99qsJZGi9dt JbtpSTLkaHxRBZUMnKfXotuKTlnfoP6HMoCQwP4aoVIjx0x7aOxoNExFM8W71iahQ5Oc n6KCgwQeS21w/KsUww5TacwwXs yoBdlqibzOn5QITFua 3rVgHJ1X3WAyDtOfN61ZXMHS0W6RVkj77SiYcB5TyG7bRaG9eavfWi02y9YXWHdRBxP6 29bCp7vld1MWOTPOE7LVy N9QusUJkb45kuhnkUGTbzyxz5rYbqRTPnY BwyGlRdgPJQ8lDAMYk4Xvo9KEgZMHHH7lVmDB7bOtQldv3zjUUQYfeaSYqKbY1CaIOP1k7LUbGygCpUEz99Y6UFgbqDBS0yY/dN2FYzv/lAIj7H20FSY486xLffL1ags/be96CiMv8AkZPGolVxmeRY01owCZIjQJ0/axRwnmuPbVoFyiZ5DHqszb7W/WrAmYA35/f2g3gB5K aSDN5HoBV5C2/V80dwEaY8qAAWCNJ90RCX0B4plO/pn7qECZgjflj01oA3XldmKuHaiCpw/BrpUAWz vmkhGYj4oxp FfOFbU39geKCiGPb77GpWwdraINaCJffqvnfRNsf0drbJpGVNo9AX2 lREZEaB4qATIjiX99elJknH8aRq2wqDO9 O3FsyotQ3CJzyvOeGtQIr7v7rFHEPREc1mgEH8saWoBDfrSVLf48T13FKiTGR6HX0UYnIimSleIN2N9acxb502N 6kJFxR6f0pKs36W0FWvPWcNmMcCoCmQ 31cTFB0OeNEORI5Q8JpATD0HgoC8zfwHiiEwnLdj3V0ypZ2yNEfEUtf5ZvqedCc7U6PvxSpGcIjlqxUEQbAOqT9oIybyvNle7Vi xPVuLQRJss9BOdtaIzfLnlny1atydr1ydd BWETjQk99E89akUfsHwcs6gJb3jf27aZET9I KBKH6Bfb KI3PmPWtCG/XF50ErhGkfc6Am P6 aiVdpHf21ZCyAncnjHHVog3XmelmgrCk/za24tKi/ajRHxerAnbrOGwvhRBByPQiNZ4/wDk3j/rOKx/9mlAl/8AmFvGsQbQ5E92Xg0MYIOweTpnRJG8udgzwvpRlznsRyxoBM/38ollu91NgTbUl1tQ4GcY43X5jOeyoYM4PLVmY8qnLiMN/E907gcsZnROlKpSbmh5II2hakERMRPxvMfFCMwBO WfFXy6n77ptlTOGzqwbt6RGWY6QHWeu2aO0k8lSBDDzI9zpThRmsW2cmTQENrqtTnuYOkHYq6mwcNr7m1DDDNdZPHShzGEdGiN63gI6zQMGQcEu6yecKFtL208lCCRN54 l88LRQELLETt7rw7r76A7MeUrHS22p4Gbx Q3xDi0hF5DnGHhCaYw1jFMAXbAHimDJB2D3MMc8Cp9gI52v8AXtYvSL3ieXPmG6bYUbAkiNnDLxlRi1h6RoOG3ZNEg3JVw3YbrRk1KZeP6OjUk2jsARnlfKlgTD9Ol5322UQiheYSkPIfNt6jO6D9cqAjAfbNuNMA3tUZ7nOjuMV0vhp9agkccHWi3Ih0gqZhtnZcjDkM8VQrJiHe/wDcyiwjHDZkOk/WpwQwIOQDfeTnjhSFJtnD5hnepTLh/Z0alMN/DKPNBZusnrWgIMJI6aJ7IL0yDGWDqGiLwvQpzMaEGlQITAtx2NmJO2kYDA9rrM8iM6UImAeJZ38tTkmTr KEhDI5QJ63UN2obaeSpRl5tyhJ44vF3UykW/prE 6USYK HNknvUACWHS6XfZh640JSfWf5spUT667DbDLOoMsQTdmOcphbLApBLm6QHilkrz6HC0mPcqF1jAdp8xURzfniaFhcDbg3T0YzpIP23DTZhxpEyb2y3k/zk2aIjJBwkgPUM8ONFLgPM9LWXtHKzMLW2sSjdgXwu4hSXRjl1NYnbehZJIb8ITz7pYSQrLuzg5gcCslC6Eh1lef/wAxrpU2BB3V ZUgESwPGwvnnpg2avJY6yPKiYzJ0i3Fm1ChvFwvlOb5j1uGEyjMb/lQCzoWw3kaoPIF3rsoTfQ19C7UmzZj/LVi17dbOHGKReLQQc5dKUEZfvrdM9WVFyHqN0v1oVN0/vrGgApf8o7lYg3dWXtDzoEK1h7dpqRSM1Ok e9BjvNMXhVixNzm3w6NQYbhJ7e9Gu60YfymcqlDOIg7BZz5TzNtTwjKd A akAFv7 dajX20C8C1RhTL2ncaJG4PWPdMkZp5Rj97qQkz/T96f5SDDUXVi9yh2ThUE2ekeqDIZWO oaULTBnXHkxhhUQQWvPfDZjQ3JbQt4owOD3QC9IJ4MOkNKcFx/n5UoYZ/fTSjanWPRUL/bfb1oItgAcpPIUipvjmi6xU4 f4ev8p//EACQQAQEBAQEBAQEAAgIDAQEAAAERIQAxQVFhcYEQYCAwsZGh/9oACAEBAAE/EHDGSeVIP5XhDO3aDZT90S/zmbtBKrxgSiVP4v739fY4qgH R/44RiUOksU FQWfg/n/ABwGo0zMANVcA6k/IER icUOA0BRQN1CFahxDqmcltzH0bjmcQyQgIFQoCR6JLepvyAiP4/9W7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u5WG1/8AOgVN9PlTRL6m8hMYPwjT6UFXP50MeLxjWJCUIuyhbIQL5AATso/efzl S4itOzL C/OHwt1nQqiWEJIW8UF7ikrsky1gNPZMvpiSOFIcxxjiQEkWSESeEdopM6Qg7GTZCbKM8QHO zwTRUDo0yjkUluNxgctrdHHph5rARvUqj0qWmPpiKT/AO/9WCwJPQno/k6INgW6cIqD8F0EqpmG NATFGexcJAkCgBtsiQhUQFy2PaQlGQAq9D/AAQXGTZkBBbDiqFysBrXRMwhQ1gCLYQjUbWVMIL9xvzAsBAOAUeVlAJzSAFmWpire3HRlwZkhCgTRVLi6HDWFdMkEzls1ZUVGFSCJXq5PqbhziraNfRKEIdyS4S Dj0p4H/qwTZBnYghfbR0YIwBHxXi9XzBzHsyKRigu47eAxs1yyA2el zm2Ee5jgpzSbj2kPygE8vEMxcjCzzV/QP5yicCdya2vyT9Xjdbc9dgCpB4pBrs6o1EET2P4LoaW68fTE5/txeDLhLHZR1Mcj7zmIRDJxBEsCSN7y9D6YiioKIjwS m7NSA Iryn ivykTQk2hTN66zd3/AF/2z4S35x17BbVAbTQ38XbruJDxHiz/AL6ZqoOk6GPAE1RdDDuMZGlBC7A8z2yUMwFHDkqDeTd/BNQURPC5eHqi7HIC0IQwhHEl FlAb0qj6GnMzcBBuAdRqRHgn05LAeSoMTUsBQKBPZnhmKCKow9FhDEpAt4knJZs45JKIgKgdKxFvDZ4mYKYgIFouAobAeyNgiABEqB44Nq3kkKyOo1BFvQttSndt0ZBECgZgKgGOJM1AKhg1XgcSIcRREBJow9cfX8yL8iChVDmJRJJVGDCrJiXObKgZtSCQSaaUCDycYUQBWQq6KaYJvLVE0xdpnjB/A7Ri88btPmfEDnkBR8GeH wjI1YLxniUL4OBsK1FIuFCDYCTY0E0tQN5OPLcA/CEFFVBo7S4BcrUPTCobFx4UkZkZ20/wCAvNK90AlIIEMk6gQspqYAhDtqgE8ErYMfgBwWmr5OGDepMmTHb8t b0ZioFjSF8NZjIXrELMSgBB44Fn1xDyvS56VlxBgG8ahtQQhcSqc/wBeIzUrWYG2PQFBDeER1TLABQHf68/qfIkhwIeic94LOEInWQgMAfRpbcwCG OkD1vydMiCeJOGnFksvnF1oWx2ECpldUsnUKp2jvHUbOtwY8wAWktoYryGx7IARpylw8itOHtVHBcVG1gJubzNlZQAkEloLcO3lyD1bpklDjuDAwCnMNUFYMFzjhNjUKIy2ugd5RNIHYs4Bn0mnLENX/cD/cQnsfOPkLeRFWSAK6xTRpzKZjMeID/F4fM1FZGZgSBQ9csNlglzS0FAl8sNRlKLPLagKPQrJhUDFxb6RBBQc9tJ4VgoYHQGkOkvcX6pJ/wA1DeoXRbqi5UfTQQDRnokJsHkMKxBa4QZygrkcRkV EORcEqIQmScBVaRPeDA0QAVTGgfQzgVJTBQmBW63kKb1zR62WFUQCAPWcuUrwxxlqIaKnk l0CAFbSVAmjmE2AABBjLBdGDUv7kvrkEiNGiQnRJSabKJ5Vmw0Qbi1MTuhliDAHAC wFoLLKhqsFyz7btVoIhpk0BM4zHa pin8kfwP/AATSLOCAF wDekeQxshIWWjQJeWBKAlV/wAy4guB1lKGxZhhIR9Ft6M1JOLk6NhbZeE9bVkdQ 58RizjmDwC5cA4orMM5gUMWJC3iB4WSvOI6PC73xAqhEBFNIHiotv6YPPTaEmeKATAKHw9Dojf0MnrRZgET3ktJyPoQHCAbrzpmMoq5FY pBXC63iC/RQBdikXvXRMCMB6AGfvKTIogh4kt wAvCMtOIl4Hlg6YqzrCZgjgjB2f74cG4BTobVlNZMPPk5WT6/7wUPVcIACDqgAFRACVMqSW1epQwYhAvIbWcnFt2EoCClOD 1a1BhRUaMXecEB8xw7CsBSol4TH0drbIEqQDCF65olg9hwTHUC86 EhpPFGuEX05ECAMmIq3qUhK6kLKnGGagZOF9ARiaAZIwANWTPw6Ol5DxJdAJVhvEk0alJuFGvXpR56dMVydwSJjBLyFjRIaMukAfPg4opyEiUhII/oseBERIaYwBQyoKpzFhAEDyYhCCBZO0tyvUwt NJX1OnO/Bl7wqUAVvW0BJnsKvQB6QUTA1akKnThjYKnLvs flOI8j4FcHvrDqJVEBnCe8zKVp GxI0UmvOcMZGxY3RNIQzCFcsBWbJ38DbnvKX0THML6loiKi83BxNO Bqj4DvLi56bi0AKoedjjCr wo5/XCfRzO1c4Ex0EFQYVzmA1U4KVb8ZvXCvJp8JJooKwQXIvJvWVeJwYl QQfHNQRjWtWZAFAm6t5/riA8I0RQUyXOUQkLaFPlEowteb0g asDyaz9p9TlHoTSCYvBQlFQxnz9t1psgqy9pK0CAoDvMSqop9nQTSsWkEBpYN9P3mdhEYwi4UPG qOGzjEkhrDE NDhlUT ajgwEGw 88nNbqqQTECCecKzbROAQs0gBqbzK2R4SRWFE9nVvx9V2DTtJTDOMqtQzuc/AHdd4EB/AggOONM XOymDxokYcIFcfOT5NBmVI0QDVMiLYvpcFw8Jpg1N5ySLoe6096sFQ5OQQ1F1SW7dGKryn8Nb4W4AUuTEOrIk8laFpLqfC70fkawRQxpiAJ7eBR04hrhFE6rfeE 7ySscxBrGXiT4I0ig arDG7eVRA2yELIfhMo40TKZSUQVKsqtb2whZzwy4AD4CGcmmoHc8CLSUZ5ryf8T0QkAAAAA841GwsZTPaSFpq3jLxiYHjkhSii24cThFUigMWpklr9cwYiVsQgUgAL553vHMZLVWtuklt3ptQ 8P4kFIKD6Xm0M1CdgDEhEHwP/GAJVcygdYKBuZY3OMedMegs8gyxQqQvAh/AufSyLcH15HkOLA6DtJDRLV1gYdqYHiyoW6oCwE4mMRH C HDJywLIOkgERNIJt0DUODszhij1ErSd/P5nHDAaq3gSlSN1lrLP3OkhJNJKTpUQQD2BwpDUrWKBn5cxK1UQi4YehcwXwcE4DEOhrfvIqzjnTpE0IDFViqS8Bm3xPkQwApM32wkWUGMoxDlf4aM/Jo6GDQCBwMgzgJgASYax/Y0CoQeIRjJLN/OcYlasx0plpcJaRsfMVqeqopoTVRiZr0WYxh2qOeNhVOHiDK34EnCdG7zdptLRAcECCA93sYa3LAWBBW0OJSVYlUywtSMxFWI3ISCOpYPuCoTsbbxq5h5rmSZuIAw6ogEAHqPgoi4VdBFVSNFVT/Bypoxw7AJ6x89vaZI3FKk0X9GhpzB2iuW2KUFkTcRaw2gSafhr/8ArzpnSgCY9uj5wAunEs1JUtmkIKO4LClqSVB8Nw4l5OBmFgfQihxBHdVeUNAQSggpZhAvSQDhZQK/yc9BWDrkizUO G0T3PoLQtZgRqY c6SyjDMCUIJ/lHsZBLC0RT7AYpaoZDixTPwzSQsP3hGFDmkIUizAbjg7FucQgejyAgB94x tYH0AMaHg3ZwbFnN9sCGgjN55t96CQQIfiD35w0B0JIiEH4FMzOVrLlHOHl Ta 96RmEARkWfAuct3qeR4uB7QgrSFd3q3ZN7d3ixkapnYPMpDGLRoJBSPLJh4lnl0qBAYcSethUV5GUzQvJPcYCiGkgUACpK97GyAXYRShRzQhBrmw4YbGWqHgzpXy85YpAAgIPRykGhLMCiBgBUpWw BkvvbSlRxbDitCBMNF5WDVXIHTc5kiBlQFFGFPO A0j0KqbWwSx85kZFo7OhdH0k28uXZJBpPRFKxiLRv4SYLK5swyb5wP2oxB/jYhcG94QldfZQJTFfWR91VCwCieOMmOD9x36hnmFLUFL0tPNxlig tKzBSB4iT0fmvJ4OlAdREX f8KAUF8F9/wCFBVh vOMuKI/APeGAeVSouv3TOb48XQMRHx/n/CSiBCu8PJt5vIoYaf2M8N/9a15E7AGwL2AmL8DsYnlT04y7Y24AWbYQBKHLdWQqy3oekdGl4RP Gh46Jf0YRaSHBGgNij 9WPggwBFNPIrJI77QYoo/3ziizrfrCzaEIcgxkBhYK4VvvKWjTxSUxn4qitGCjdEH3GZ3Qq2JwuzMU5fi/AUhrvR2msLBbJA/SFyZGExUFV0eKnjHYBowxteFh5Z cLkcmg7TPpnlVAIBwlHpCvtD9c8WyBWQPZRPZnIPeDoBRD5Jvbj9bAWRcK/GlaBE0V SELV3yY ZQJAZLZrINK/QOXlp/PmNVK/pk1LJ4omClDcFA3LnJxGyw4gEPjRFLeaKs3zsCFGgsL24vAasCm6BnyLymbv3AozwZ9 HDOE9LoP6yIuFUhgkSFp6SA2AdZRtQrXQFGc9HLYziFWXaGPC1ocZjAK0ug4MKwXifiEE7hKlnv51/RqJZrtdbQ3Rzw9vVDlo3gh0Id 6KQqSwwI Fo4wMrkHFFAjaFCJxsx5kkreVJRIYxyzLzW2EPEaIvxJwTKf0rAc PvxYYfYI76gf0WCIAUf6hn4QjYVwGZJgXzU8B/rg2PLBwSmo Cmxoz1aENHNtbUFODrHZdlAkvaqarwZRrOjlQiFk1nrGjSaHwaxC6IAcewa1rweQ2S6JD3hHxtqzKFvrA/1wzoBO0WhCX2Aj3pTxTFhTVD6Fy8UMWmf3UqitT 9Ze2krJTC1dDpTtQyQ3m8IxD4AYhsYVE7 0ufH3t6egpVdRAeAEGdKoLwlj3GSchQnG914oD4q65VVxQXhkhQsox0MC95qPQaEx8Ue3zk2XKqWbgdSOBqOJsy/A6qcgF4wM/oUhTCDpxTWh69AYMqUWiBBHQXkm/B46/tgwAjkl4AeEtBq8 /DoS84njHdcgJBoAZErCOrYQwpheHTGYy6koghRFJyF7OE2b 9jwqPNi0G3zJbGijSKkQwxnSXWVPjAK8TL4nsCAigZkFekXYgPd3hD5n0zgyVVsBjU69BGKgqy44XhajWAplsZn1AuUa/jU/FvBNn9l5QohtgQOeChWDANyQ ueH0FtqGBOWhMJJ0Ae5YNJgmMVRpUQ3LVvaTNw3ggHGsJIQ2GkLQpQVHEUDk5E88ANZEZcGCKdEetHlEzh j2K0RI7bZf0wvtNEXLeqD8CZ/66GfvNLnc6/FK3Ch/lDulEorNdINqFUsyDkiXRrif6DvNeuPTV1Akdr9ZFQE/fcIqEEVjP7grsGSCCksRurqmUo2BiGSLIwTY/elMsi VMHQs5QrTDHGUECTxFRYnVlfbOvDUG/PDjoqepOQQUCEQUlDeLkVEnwrcPPsq2PT5bCNAiX8zQD2Il1LRgP0FHB sGTfQT0NZcaASMxhkLWh/6oLaaf/ObyZOgSC5RCmWNGoBwkI3aYKs/pWTToVfDCJfUS0cuH63ckkrRh 0sIuliVTABr7p2QSm bOnKHjVt4V8cF7XmYayIJvDGHAyi7N2sLbiFEpMz4BtbVhvUDu/iTXOUifCudOC2XMCuF8lD73LVRUeMMIagw/yUzjdCACgzRFg33syn5xa3HSNOtLnBXtVAGoiEEHNYcz tl2vmxND9fP8AqhVOadtUB7kGAmwhEo 8YgZq0wGwFohknL8V9zhQYQnlmFeKU8emU6iYDqzg1JWysdiuLgbQ6IiASPXovsR9CUY0cOC7J8D8BmHU5B892QMNX4n1O9fTIyqUt3Rv6S8IQEccjLj4c/8A5x8ivESGP9YRGfvPMokwyBY7YANO0AJBh2acoGg3qT44pcOydV1mzhQOXndIEo4WNNegBWtxIIKgfP6f9U//2Q==[/IMG]

---

### Post by ubfan1 on 2024-10-12
You can just highlight the blkid output with the mouse (left click and drag), then cut it (ctrl+shift+c) and paste it  (ctrl+v) into a message here, no images needed.

---

### Post by CowDoctor on 2024-10-21
Here is the result of the blkid ask.  Next step was to open the root partition and check /etc/fstab.  I am not sure exactly how to do that.  Through the file manager I find a folder called root, then open in file manager and enter /etc/fstab and get "permission denied"  The root directory has a big red X on it, by the way.  Opening the properties show "contents unreadable".  HELP  
Once again, would there be any future in trying to just download the upgrade again?
/dev/sda2: LABEL="Ubuntu" UUID="6496c978-c968-4bdf-8a40-f3b3f0b0233b" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="primary" PARTUUID="77cb2e96-3e43-4e65-8073-3971a676c183"

 /dev/sda3: UUID="748c985b-1fe1-4dac-9dae-b3b8190a8652" TYPE="swap" PARTLABEL="primary" PARTUUID="a166aaa4-de0e-48d0-9f3e-7120808fb581"
 /dev/sda1: LABEL_FATBOOT="EFI" LABEL="EFI" UUID="E980-6849" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="primary" PARTUUID="72ad959e-885d-48fa-a5ee-0ebbb0cc3777"
 /dev/loop1: TYPE="squashfs"
 /dev/loop29: TYPE="squashfs"
 /dev/loop19: TYPE="squashfs"
 /dev/loop37: TYPE="squashfs"
 /dev/loop27: TYPE="squashfs"
 /dev/loop17: TYPE="squashfs"
 /dev/loop8: TYPE="squashfs"
 /dev/loop35: TYPE="squashfs"
 /dev/loop25: TYPE="squashfs"
 /dev/loop15: TYPE="squashfs"
 /dev/loop6: TYPE="squashfs"
 /dev/loop33: TYPE="squashfs"
 /dev/loop23: TYPE="squashfs"
 /dev/loop13: TYPE="squashfs"
 /dev/loop4: TYPE="squashfs"
 /dev/loop31: TYPE="squashfs"
 /dev/loop21: TYPE="squashfs"
 /dev/loop11: TYPE="squashfs"
 /dev/loop0: TYPE="squashfs"
 /dev/loop28: TYPE="squashfs"
 /dev/loop18: TYPE="squashfs"
 /dev/loop9: TYPE="squashfs"
 /dev/loop36: TYPE="squashfs"
 /dev/loop26: TYPE="squashfs"
 /dev/loop16: TYPE="squashfs"
 /dev/loop7: TYPE="squashfs"
 /dev/loop34: TYPE="squashfs"
 /dev/loop24: TYPE="squashfs"
 /dev/loop14: TYPE="squashfs"
 /dev/loop5: TYPE="squashfs"
 /dev/loop32: TYPE="squashfs"
 /dev/loop22: TYPE="squashfs"
 /dev/loop12: TYPE="squashfs"
 /dev/loop3: TYPE="squashfs"
 /dev/loop30: TYPE="squashfs"
 /dev/loop20: TYPE="squashfs"
 /dev/loop10: TYPE="squashfs"

---

### Post by 1fallen on 2024-10-21
> **CowDoctor said:**
> .  Next step was to open the root partition and check /etc/fstab.  I am not sure exactly how to do that."

Like this:
```
less /etc/fstab
```
Should produce something like:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/ubuntu-lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-0ZAaK5oRVBHO3ZRf1fioebvMh26oly5hCDIqf16aLTP7b1xuKPXWiqztjufoeves / ext4 defaults 0 1
# /boot was on /dev/sdc2 during curtin installation
/dev/disk/by-uuid/31ce1973-70eb-434b-9d53-158685cb189c /boot ext4 defaults 0 1
# /boot/efi was on /dev/sdc1 during curtin installation
/dev/disk/by-uuid/DA34-E212 /boot/efi vfat defaults 0 1
/swap.img       none    swap    sw      0       0

```

---

### Post by ubfan1 on 2024-10-21
Looks like a typo somewhere, the actual UUID is as blkid reported:6496c978-c968-4bdf-8a40-f3b3f0b0233b   The error message has ...fb3f0... missing a 3

---

### Post by CowDoctor on 2024-10-22
ubfan1, yes it is my typo.  the UUIDs are identical.  I dropped a 3 when typing the error message.

---

### Post by CowDoctor on 2024-10-26
Dear Friends,
   So sorry this is taking so long.  Here is the response to less /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>  <mount point>  <type>  <options>  <dump>  <pass>

# /dev/sda2
UUID=6496c978-c968-4bdf-8a40-f3b3f0b0233b  /  ext4  noatime,errors=remount-ro  0  1

# /dev/sda1
UUID=E980-6849  /boot/efi  vfat  umask=0077  0  1

# /dev/sda3
UUID=748c985b-1fe1-4dac-9dae-b3b8190a8652  none  swap  sw  0  0
~
~
~
~
~
~

```

What next?  Sorry to be so helpless.
Yours hopefully,
Joe
ps, once again, since I can get this machine kind of running in recovery mode, would it be worth trying to download Ubuntu 24.04 again and see if it straightens things out?

---

### Post by Bashing-om on 2024-10-26
CowDoctor; Ouch 

Your /etc/fstab file does not in almost all respects agree with what blkid reports.

Let's see what we can do to make it right.
Post back:
```

sudo fdisk -lu
swapon --summary

```
so we know what the boot partition is and *IF* there is a swap partition.

[INDENT]maybe, this is all there is to it
[/INDENT]

---

### Post by CowDoctor on 2024-10-26
Thank you.  This, I believe, is the relevant part of the response to the fdisk request:
```

Disk /dev/sda: 111.8 GiB, 120040980480 bytes, 234455040 sectors
Disk model: WDC WDS120G2G0B-
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: BA5E4D98-D80E-415E-A1C7-9ADE1CE33BBB

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 226064383 225013760 107.3G Linux filesystem
/dev/sda3  226064384 234452991   8388608     4G Linux swap


```
There were 38 loops reported, all nearly identical except for some numbers in the first lines.  The above code between loops 7 and 8.
I can copy the whole thing if you wish.
and here is the swapon:
```

oe@Bucky:~$ swapon --summary
Filename                Type        Size        Used    Priority
/dev/sda3              partition    4194300        0    -2


```
Hope this is useful

---

### Post by Bashing-om on 2024-10-27
CowDoctor; Well yeas

All looks good - and all agrees. (why using code tags is so important, as I did goof in reading)

OK go back and verify that the UUID  6496c978-c968-4bdf-8a40-fb3f0b0233b is a typo on your part relaying to the post.

else we got to go hunting.

[INDENT]it's in the process
[/INDENT]

---

### Post by ubfan1 on 2024-10-27
Careful, there's an example fstab posted which confused me awhile.  I thought the blkid and fstab were different, but comparing the correct fstab, they are the same.

---

### Post by CowDoctor on 2024-10-27
Bashing-om,
Yes, verifying typo.  Once again, the full error message when I try to boot, after a long pause:

Gave up waiting for suspend/resume device
Gave up waiting for foot file system device.  Common problems:
 -Boot args (cat /proc/cmdline)
     -Check rootdelay= (did the system wait long enough)
 -Missing modules (cat /proc/modules; ls/dev)
ALERT!  UUID=6496c978-c968-4bdf-8a40-f3b3f0b0233b does not exist.  Dropping to a shell!

BusyBox v1.30.1 (Ubuntu1:1.30.1-7ubuntu3.1) built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)

Once this happens, if I force it to power off, and then try to boot, it will come up with a menu where I can choose a recovery mode that gets me started, sort of.  When I power that off and boot again, I get the error message above once more.  I have to hand copy and type that error message, so typo still possible, but I checked pretty carefully.  It is the same UUID

Next?
Yours  gratefully and hopefully,
CowDoctor

---

### Post by Bashing-om on 2024-10-27
CowDoctor Well ---

As there is:
> 
Gave up waiting for suspend/resume device


And we have confirmed that UUID does exist!

Makes me wonder -
It has been way long since last I looked about "resume"; and maybe a lot has changed since then -
But >
Do these files exist ?
```

ls -al /etc/uswsusp.conf
ls -al /etc/initramfs-tools/conf.d/resume

```

[INDENT]Gots to be a reason
[/INDENT]

---

### Post by CowDoctor on 2024-10-27
[code]
joe@Bucky:~$ ls -al /etc/uswsusp.conf
ls: cannot access '/etc/uswsusp.conf': No such file or directory
joe@Bucky:~$ ls -al /etc/initramfs-tools/conf.d/resume
-rw-rw-r-- 1 root root 49 Oct 30  2018 /etc/initramfs-tools/conf.d/resume
joe@Bucky:~$ ^C
[code/]
Hmmmmm?
joe@Bucky:~$

---

### Post by Bashing-om on 2024-10-27
CowDoctor - so 

What URL is defined ?
```

cat /etc/initramfs-tools/conf.d/resume

```

[INDENT]maybe this - might be other
[/INDENT]

---

### Post by CowDoctor on 2024-10-27
```

joe@Bucky:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=748c985b-1fe1-4dac-9dae-b3b8190a8652
joe@Bucky:~$ 

```

---

### Post by CowDoctor on 2024-10-28
?

---

### Post by ubfan1 on 2024-10-28
Any other files in /etc/initramfs-tools/conf.d besides the resume file?  See [https://ubuntuforums.org/showthread.php?t=2401012](https://ubuntuforums.org/showthread.php?t=2401012)

---

### Post by CowDoctor on 2024-10-28
Thank you, ubfan1.  I got the general idea from that thread, but am inexperienced enough (very) that I don't know how to check for another file.  Can you help, please?
Yours apologetically,
Joe

---

### Post by CowDoctor on 2024-10-28
So I changed to that directory (cd /etc/...) and used a "dir" command and got "RESUME" as the only answer.  Would that be the process?

---

### Post by ubfan1 on 2024-10-28
Yes, that would do it. So no extra files to cause problems.  Lets check the environment variable RESUME. From a terminal (an icon or start one by typing ctrl+alt+t), type echo $RESUME and either nothing or the UUID=748c985b-1fe1-4dac-9dae-b3b8190a8652 should print out.  If it doesn't, something is changing it somewhere. Your setup files look ok, so look in your home directory at the hidden files .profile and .bashrc.  From the terminal, type grep RESUME .profile .bashrc and see if any matches (expect none).  There are other places to look (like .bash_profile) but  I'd expect you'd remember if you set them up there.  I assume you are running the default shell bash, again, if you changed that, I'd expect you to remember. Unless you had someone else set up the machine?

---

### Post by CowDoctor on 2024-10-29
Thank you, ubfan1.  I will work on that.  I bought the machine set up from System 76 and it has worked very well for years.  I am not savvy with code and have not made any modifications of anything except adding and upgrading programs and apps as needed.  echo $RESUME  yields nothing.  grep RESUME.profile.bashrc yields a white cursor that doesn't go away and when I try to get out it tells me the terminal has a process running.  I have waited quite a while.  Nothing.
Next?

---

### Post by ubfan1 on 2024-10-29
There needs to be a space to separate the files .profile and .bashrc in the grep command. grep RESUME   .profile   .bashrc

System76 would be pop OS, a derivative of Ubuntu. Not familiar with what the differences are.

---

### Post by CowDoctor on 2024-10-29
Thank you.  When I do that I still get the little white rectangle, first blinking then steady.  In response to your message, I first tried it with the spaces and it returned no such file or directory, so I tried without the spaces.  Not doing that anymore, but still nothing.  I've been waiting about 5 minutes and no change.

---

### Post by ubfan1 on 2024-10-29
The response should be instantaneous.  The expected response is nothing, just another prompt from the terminal. The assumption is you are in your home directory (where you login, or after typing just cd in the terminal), and you are running the bash shell (last entry in the /etc/passwd file for your username should be "/bin/bash").

---

### Post by CowDoctor on 2024-10-29
Ok, I think that is what is happening.  For what it is worth, I do seem to be running the bash shell as I get bash prompts, but I can't find anything in /etc/passwd.  A dir of etc shows passwd but trying to get there give me "not a directory" or "no such file or directory".

---

### Post by 1fallen on 2024-10-29
```
less '/etc/passwd' 
```
should show it
EDIT: to narrow it down a bit:
```
less '/etc/passwd'|grep $USER
```
Good Luck

---

### Post by CowDoctor on 2024-10-29
```

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:100:102:systemd Network Management,,,:/run/systemd/netif:/usr/sbin/nologin
systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd/resolve:/usr/sbin/nologin

```

---

### Post by CowDoctor on 2024-10-29
Thank you.  What next?

---

### Post by ubfan1 on 2024-10-29
That less output was only the first page, so scroll down, we're looking for your username.  Alternatively, use a different comand, like cat /etc/passwd which does not scroll, or even grep bash /etc/passwd to search and output just users defaulting to the bash shell at login (other than root).

---

### Post by CowDoctor on 2024-10-29
```

mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:100:102:systemd Network Management,,,:/run/systemd/netif:/usr/sbin/nologin
systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd/resolve:/usr/sbin/nologin
syslog:x:102:106::/home/syslog:/usr/sbin/nologin
messagebus:x:103:107::/nonexistent:/usr/sbin/nologin
_apt:x:104:65534::/nonexistent:/usr/sbin/nologin
uuidd:x:105:111::/run/uuidd:/usr/sbin/nologin
avahi-autoipd:x:106:112:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/usr/sbin/nologin
usbmux:x:107:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
dnsmasq:x:108:65534:dnsmasq,,,:/var/lib/misc:/usr/sbin/nologin
rtkit:x:109:114:RealtimeKit,,,:/proc:/usr/sbin/nologin
cups-pk-helper:x:110:116:user for cups-pk-helper service,,,:/home/cups-pk-helper:/usr/sbin/nologin
speech-dispatcher:x:111:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/false
whoopsie:x:112:117::/nonexistent:/bin/false
kernoops:x:113:65534:Kernel Oops Tracking Daemon,,,:/:/usr/sbin/nologin
saned:x:114:119::/var/lib/saned:/usr/sbin/nologin
pulse:x:115:120:PulseAudio daemon,,,:/var/run/pulse:/usr/sbin/nologin
avahi:x:116:122:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/usr/sbin/nologin
colord:x:117:123:colord colour management daemon,,,:/var/lib/colord:/usr/sbin/nologin
hplip:x:118:7:HPLIP system user,,,:/var/run/hplip:/bin/false
geoclue:x:119:124::/var/lib/geoclue:/usr/sbin/nologin
gnome-initial-setup:x:120:65534::/run/gnome-initial-setup/:/bin/false
gdm:x:121:125:Gnome Display Manager:/var/lib/gdm3:/bin/false
joe:x:1000:1000:Joe Snyder,,,:/home/joe:/bin/bash
systemd-timesync:x:122:127:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
tss:x:123:130:TPM software stack,,,:/var/lib/tpm:/bin/false
tcpdump:x:124:131::/nonexistent:/usr/sbin/nologin
nm-openvpn:x:125:132:NetworkManager OpenVPN,,,:/var/lib/openvpn/chroot:/usr/sbin/nologin
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
systemd-oom:x:126:134:systemd Userspace OOM Killer,,,:/run/systemd:/usr/sbin/nologin
sssd:x:127:136:SSSD system user,,,:/var/lib/sss:/usr/sbin/nologin
fwupd-refresh:x:128:137:fwupd-refresh user,,,:/run/systemd:/usr/sbin/nologin
snapd-range-524288-root:x:524288:524288::/nonexistent:/usr/bin/false
snap_daemon:x:584788:584788::/nonexistent:/usr/bin/false
_chrony:x:129:138:Chrony daemon,,,:/var/lib/chrony:/usr/sbin/nologin
_flatpak:x:130:139:Flatpak system-wide installation helper,,,:/nonexistent:/usr/sbin/nologin
~


```

---

### Post by CowDoctor on 2024-10-29
That's the full reply, I hope.  Learned something about scrolling down in the terminal.  I hope this tells you something.

---

### Post by ubfan1 on 2024-10-29
That confirmed you're running the bash shell (so .profile and .bashrc are files expected to be in  your home directory), and that your home directory is in the expected place.  I think we confirmed there is no environment variable RESUME (echo $RESUME did not output anything), and that your UUIDs from the output of blkid match the UUIDs in the file /etc/fstab.  Yet an old UUID pops up.  Next thing to try is to rebuild the initrd file you boot from (in boot with names like initrd.img-6.8.0-47-generic).  That earlier link to a forum thread I posted  had the commands for the rebuild.  There might be an old UUID built into the initrd file you're booting.  The only other possibility is that you boot is from an entirely different device with old info. going back to another EFI partition. Unlikely since I didn't see such a device, so must be the initrd.

---

### Post by CowDoctor on 2024-10-30
Thank you.  It is a little difficult for me to figure out which of the various commands in that thread you are referencing.  May I ask for a repeat, specific, please?  I will look again and try.
Yours gratefully and hopefully,
Joe

---

### Post by 1fallen on 2024-10-30
Hi CowDoctor, I'm the poster (#&thj^%) in that thread, please give this a shot:
```
sudo update-initramfs -u -k all
```
Paste back the return please.

---

### Post by CowDoctor on 2024-10-30
```

oe@Bucky:~$ sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-6.9.3-76060903-generic
update-initramfs: Generating /boot/initrd.img-6.8.0-76060800daily20240311-generic
joe@Bucky:~$ 


```
This is what I got with that command.  I will now try to reboot.  Wanted to send it before it got lost.

---

### Post by 1fallen on 2024-10-30
Fingers and Legs crossed....

BTW your kernels are not known to me, mine:
```
sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-6.11.0-8-generic
update-initramfs: Generating /boot/initrd.img-6.8.0-45-lowlatency

```

Is this a System76 machine or OEM install?

---

### Post by CowDoctor on 2024-10-30
Thank you.  I tried it with just -u and nothing happened.  Will try the full deal.  
By the way, the computer is running Ubuntu, not POP.  System 76 will do either.  When I bought my first machine from them years ago, it was all Ubuntu.  I've been scared to switch to POP as I am not very code savvy and it's hard enough to find drivers for Ubuntu, let alone something new.  I suspect there might not be any difference, but haven't explored.
You saw in the previous post what happened.  It has made no difference.  The machine will still only boot in recovery mode. :(

---

### Post by CowDoctor on 2024-10-30
The machine came from System 76 with Ubuntu installed.  I have periodically upgraded, no problems until this last go round.

---

### Post by 1fallen on 2024-10-30
No I have not read all 58 replies, but that said PopOS has kernels with drivers all ready to go for their machines.
But yes Ubuntu is do-able with some extra elbow grease.

---

### Post by CowDoctor on 2024-10-30
So any ideas what to do next to get this machine up and running properly?  I have been wondering if it would be worth trying to download the Ubuntu 24.04 LTS again?  I don't want to make matters worse.  The POP/Ubuntu comment was just to be sure you all knew that the machine has been running on Ubuntu since it left the factory.

---

### Post by 1fallen on 2024-10-30
Popos use Ubuntu, yes I'm familiar with them and their systems. This forum is full of them.

Ok this method I know first hand works: [https://support.system76.com/articles/install-ubuntu/](https://support.system76.com/articles/install-ubuntu/)
Those repos are Vital to a nice install.

First Do have good back-ups in place, it save's brain damage and grief.

---

