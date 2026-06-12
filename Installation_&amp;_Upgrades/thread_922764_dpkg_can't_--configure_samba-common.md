---
title: "dpkg can't --configure samba-common"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by fuzzyworbles on 2008-09-17
Hello ubuntu community, to whom i've contributed nothing substantively useful. I've got a problem with dpkg/synaptic/apt-get that I *really* hope somebody can help me with: 

Every time I upgrade or install something, I get this:
>  
chris@fuzzylogic:~$ sudo apt-get -f install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up samba-common (3.0.28a-1ubuntu4.5) ...
mv: cannot move `/var/run/samba/upgrades/smb.conf' to `/VAR/RUN/SAMBA/UPGRADES/SMB.CONF': No such file or directory
mv: cannot move `/etc/samba/smb.conf' to `/ETC/SAMBA/SMB.CONF': No such file or directory
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 3.0.28a-1ubuntu4.5); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4.5); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba-common (= 3.0.28a-1ubuntu4.5); however:
  Package samba-common is not configured yet.
dpkg: error processing winbind (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 samba
 smbclient
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'd guess that the problem is "mv: cannot move `/etc/samba/smb.conf' to `/ETC/SAMBA/SMB.CONF': No such file or directory" but I'm not entirely sure what I'm supposed to do about that.

I've been using samba and installing other packages for quite some time without incident. I've tried using synaptic to completely remove everything, then reinstalling the packages, but with no avail -- I just get the same error. The example above is another feudal attempt make it install and configure itself.

I hope my coworkers don't need to print anything while this is busted!! :-\"


--- edit

alright. it's fixed. after seeing [http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg185153.html]("http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg185153.html") i realized that 'oh yeah, i've got a script called ucf that does just that, too (changes everything to uppercase). i changed the name and things went smoothly. i didn't delete my post - if that's even possible - just in case somebody else comes across the same freak error.

---

### Post by jamestrowbridge on 2009-07-11
I fixed my issue by doing:
```
sudo apt-get remove --purge samba-common
sudo apt-get remove --purge samba
sudo apt-get install samba
```

Be sure to use do the:
sudo apt-get remove --purge samba-common

Part, I tried it a BUNCH of other times without it and it didn't fix it at all.

This is on a Pentium III box and running Ubuntu 9.04

Thank you.

---

### Post by rugbeeprop on 2009-07-29
Thanks.

---

### Post by lisati on 2009-07-29
> **fuzzyworbles said:**
> 
I'd guess that the problem is "mv: cannot move `/etc/samba/smb.conf' to `/ETC/SAMBA/SMB.CONF': No such file or directory" but I'm not entirely sure what I'm supposed to do about that.


One thing to note for the future is that Ubuntu, like other Linux-based systems, is more sensitive to case than Windows. Ubuntu sees /etc and /ETC a referring to different things. Your system is more likely to have a folder called '/etc/samba' than one called /ETC/SAMBA', which is why a simple mv won't work.

---

### Post by bionnaki on 2009-07-29
hello.

I am having a similar problem after today's update, although I do not appear to have the uppercase problem and purging samba did not help either.

here's my output:

> Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main samba 2:3.3.2-1ubuntu3.1 [4527kB]
Fetched 4527kB in 5s (902kB/s)  
Preconfiguring packages ...
Selecting previously deselected package samba-common.
(Reading database ... 123882 files and directories currently installed.)
Unpacking samba-common (from .../samba-common_2%3a3.3.2-1ubuntu3.1_i386.deb) ...
Selecting previously deselected package samba.
Unpacking samba (from .../samba_2%3a3.3.2-1ubuntu3.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up samba-common (2:3.3.2-1ubuntu3.1) ...
update-alternatives: unable to make /usr/share/samba/valid.dat.dpkg-tmp a symlink to /etc/alternatives/valid.dat: No such file or directory
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.3.2-1ubuntu3.1); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 samba-common
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)


any ideas?

---

### Post by meluzi02 on 2009-10-02
I have use the code to remove samba-common but and had this response[B]


Package has no files currently installed.

dpkg: serious warning: files list file for package `reiserfsprogs' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-server-core-5.0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.10-x' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ubuntu-minimal' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `popularity-contest' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `apparmor' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmad0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `hplip' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libfontenc1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libglew1.5' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `cpio' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `powermgmt-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `network-manager-gnome' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xsane' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libstdc++6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libvisual-0.4-plugins' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpcsclite1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `scim' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnupg-agent' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `x11-xfs-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-i740' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `zip' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `nautilus-sendto' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono-system2.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iputils-arping' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libhtml-tagset-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `pulseaudio' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `evolution-indicator' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ca-certificates' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `update-notifier-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `strace' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gvfs-fuse' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `vim-tiny' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-debian' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libcdio7' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `usplash-theme-ubuntu' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-server' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-ati' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-siliconmotion' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `binutils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `cdparanoia' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libfaad0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono-corlib2.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `foomatic-db-hpijs' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `php5-mysql' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.10-alsa' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gconf' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libntfs-3g49' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libggi2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.10-tools' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libphp-serialization-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `less' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-client-5.0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libapparmor1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgphoto2-port0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libglib2.0-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libnet-dbus-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgomp1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `wodim' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono-sqlite2.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-tseng' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libtext-charwidth-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxt6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `readline-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-sound-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libcap2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwpd8c2a' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libapr1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `software-properties-gtk' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `usplash' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libid3tag0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libcupsimage2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libqt4-assistant' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwrap0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `cups' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnome-media0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `netcat' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `lsof' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblockfile1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblaunchpad-integration1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxau6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libio-string-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnome-power-manager' missing, assuming package has no files currently installed.
28947 files and directories currently installed.)
Removing system-config-samba ...
Purging configuration files for system-config-samba ...
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/zh_TW/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/zh_TW' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/zh_CN/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/zh_CN' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/vi/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/vi' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/uk/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/uk' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/tr/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/tr' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/te/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/te' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ta/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ta' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/sv/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/sv' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/sr/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/sr' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/sq/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/sq' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/sl/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/sl' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/sk/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/sk' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ru/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ru' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ro/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ro' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/pt_BR/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/pt_BR' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/pt/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/pt' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/pl/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/pl' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/pa/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/pa' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/or/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/or' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/nl/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/nl' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/nb/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/nb' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ms/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ms' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/mr/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/mr' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ml/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ml' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/mk/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/mk' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/lv/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/lv' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ku/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ku' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ko/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ko' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/kn/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/kn' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ka/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ka' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ja/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ja' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/it/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/it' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/is/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/is' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/id/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/id' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/hy/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/hy' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/hu/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/hu' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/hr/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/hr' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/hi/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/hi' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/he/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/he' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/gu/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/gu' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/fr/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/fr' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/fi/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/fi' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/et/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/et' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/es/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/es' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/en_GB/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/en_GB' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/el/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/el' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/de/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/de' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/da/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/da' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/cy/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/cy' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/cs/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/cs' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ca/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ca' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/bs/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/bs' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/bn/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/bn' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/bg/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/bg' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ar/LC_MESSAGES' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale/ar' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/locale' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/omf' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/gnome/help' not empty so not removed.
dpkg - warning: while removing system-config-samba, directory `/usr/share/gnome' not empty so not removed.
Removing samba ...
Purging configuration files for samba ...
Removing configuration file /etc/default/samba...
Removing configuration file /etc/default/samba...
dpkg - warning: while removing samba, directory `/etc/ufw/applications.d' not empty so not removed.
dpkg - warning: while removing samba, directory `/etc/ufw' not empty so not removed.
Removing samba-common ...
dpkg - warning: while removing samba-common, unable to remove directory `/var/run': Device or resource busy - directory may be a mount point ?
Purging configuration files for samba-common ...
dpkg - warning: while removing samba-common, unable to remove directory `/var/run': Device or resource busy - directory may be a mount point ?
dpkg - warning: while removing samba-common, directory `/var/log/samba' not empty so not removed.
dpkg - warning: while removing samba-common, directory `/var/log' not empty so not removed.
dpkg - warning: while removing samba-common, directory `/var/lib' not empty so not removed.
dpkg - warning: while removing samba-common, directory `/var/cache' not empty so not removed.
dpkg - warning: while removing samba-common, directory `/etc/pam.d' not empty so not removed.
dpkg - warning: while removing samba-common, directory `/etc/dhcp3/dhclient-enter-hooks.d' not empty so not removed.
dpkg - warning: while removing samba-common, directory `/etc/dhcp3' not empty so not removed.
Processing triggers for man-db ...
Processing triggers for ufw ...


[/B]

---

### Post by raafaell on 2010-09-30
Thanks, this fixed my problem...

---

