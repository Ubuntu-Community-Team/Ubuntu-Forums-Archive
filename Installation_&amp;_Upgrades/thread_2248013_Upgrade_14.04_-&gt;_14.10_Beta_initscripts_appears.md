---
title: "Upgrade 14.04 -&gt; 14.10 Beta: initscripts appears to be broken"
date: 2014-10-11
forum: Installation &amp; Upgrades
---

### Post by damien_d on 2014-10-11
Dear all,

Last night, I updated from 14.04 to 14.10 Beta1 via update-manager -d.

The installation process failed, and there are quite a number of packages that appear to to be configured because of unmet dependancies. The root of these appears to be initscripts:


```

damien@damien-desktop:/var/lib/dpkg$ sudo apt-get install initscripts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
initscripts is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
863 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up initscripts (2.88dsf-41ubuntu18) ...
insserv: warning: script 'K01vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'vpnagentd_init' missing LSB tags and overrides
insserv: Starting vpnagentd_init depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service vpnagentd_init and rc.local if started
insserv:  loop involving service rc.local at depth 9
insserv:  loop involving service vpnagentd_init at depth 1
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package initscripts (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing package util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of e2fsprogs:
 e2fsprogs depends on util-linux (>= 2.15~rc1-1); however:
  Package util-linux is not configured yet.

<Many more errors like the above follow>

dpkg: too many errors, stopping
Errors were encountered while processing:
 initscripts
 util-linux
 e2fsprogs
 procps
 kmod
 module-init-tools
 upstart-bin
 ifupdown
 grub-common
 udev
 initramfs-tools
 mountall
 plymouth
 upstart
 friendly-recovery
 mdadm
 dbus
 consolekit
 brltty
 bluez
 resolvconf
 accountsservice
 language-selector-common
 systemd
 libpam-systemd:amd64
 cups-daemon
 evolution
 dbus-x11
 gcr
 gnome-keyring
 x11-common
 libice6:i386
 libice6:amd64
 libsm6:i386
 libqtgui4:i386
 libsm6:amd64
 libqtgui4:amd64
 libdbusmenu-qt2:amd64
 gconf2
 libgnomevfs2-common
 libgnomevfs2-0:amd64
 samba
 winbind
 libnss-winbind:amd64
 libpam-winbind:amd64
 libphonon4:amd64
 libpoppler-qt4-4:amd64
 libqt4-designer:amd64
 libqt4-designer:i386
 libqt4-help:amd64
 libqt4-opengl:amd64
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The status of the package appears to be as follows:
```

Package: initscripts
Status: install ok half-configured
Priority: required
Section: admin
Installed-Size: 250
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: sysvinit
Version: 2.88dsf-41ubuntu18
Config-Version: 2.88dsf-41ubuntu6
Replaces: libc0.1, libc0.3, libc6, libc6.1
Depends: libc6 (>= 2.4), mount (>= 2.11x-1), debianutils (>= 4), lsb-base (>= 4.1+Debian11ubuntu7), sysvinit-utils (>= 2.88ds1-64), sysv-rc | file-rc, coreutils (>= 5.93)
Recommends: psmisc, e2fsprogs
Breaks: aide (<< 0.15.1-5), atm-tools (<< 1:2.5.1-1.3), autofs (<< 5.0.0), bootchart (<< 0.10~svn407-4), console-common (<< 0.7.86), console-setup (<< 1.70ubuntu9), cruft (<< 0.9.16), eepc-acpi-scripts (<< 1.1.12), fcheck (<< 2.7.59-16), hostapd (<< 1:0.7.3-3), hurd (<< 0.5.git20131101~), ifupdown (<< 0.6.8ubuntu27), libpam-mount (<< 2.13-1), live-build (<< 3.0~a26-1), ltsp-client-core (<< 5.2.16-1), mdadm (<< 3.2.2-1), nbd-client (<< 1:2.9.23-1), nfs-common (<< 1:1.2.5-3), portmap (<< 6.0.0-2), readahead-fedora (<< 2:1.5.6-3), resolvconf (<< 1.49), rpcbind (<< 0.2.0-7), rsyslog (<< 5.8.2-2), selinux-policy-default (<= 2:0.2.20100524-9), splashy (<< 0.3.13-5.1+b1), sysklogd (<< 1.5-6.2), util-linux (<< 2.20.1-5), wpasupplicant (<< 0.7.3-4), xymon (<< 4.3.0~beta2.dfsg-9)
Conflicts: libdevmapper1.02.1 (<< 2:1.02.24-1)
Conffiles:
 /etc/init.d/bootmisc.sh b1cc3129e3045bb60bd18d99c5dc1357
 /etc/init.d/checkfs.sh e7a96199d9cbfd1adf52c266e4de4b9b
 /etc/init.d/checkroot.sh 357dbe3f32fe4cfac41954e939b1c51a
 /etc/init.d/checkroot-bootclean.sh f968128c0fc7bc81433e71eec88e30ff
 /etc/init.d/halt 6ae1b3b1b8198567a5e32116077f12a2
 /etc/init.d/hostname.sh 2180072dbb4e2f42f7ad4df4a2f9888d
 /etc/init.d/killprocs 5e404d35091fab6c4889302736ed4602
 /etc/init.d/ondemand 88514d9c047b32c4ff3cf0042e216bce
 /etc/init.d/mountall.sh 93370d23da24b8674efcd9b88405137d
 /etc/init.d/mountall-bootclean.sh c7f42e6137e70db123b47d88af0b4862
 /etc/init.d/mountnfs.sh c7b2d1c95c5278c3a71953dbf43a15bd
 /etc/init.d/mountnfs-bootclean.sh 678549e24b023008c84afa0086eee296
 /etc/init.d/mountdevsubfs.sh 7e57c115548eb29a48c68da103c6d53e
 /etc/init.d/mountkernfs.sh 7e3c46a6b9e52ca0b987b59a98d5b5b8
 /etc/init.d/rc.local 18cd07959adfa8411ca17fe7c2ec3d96
 /etc/init.d/reboot 1b9db1ef7bfd79b128ef85d5065721a6
 /etc/init.d/sendsigs 8376da0c226dcc989f6829230b1d5b50
 /etc/init.d/single dc13cb373c5c098a8fb95424701373e3
 /etc/init.d/umountfs 07e4c8c8d9136f36745feb4776edc6f4
 /etc/init.d/umountnfs.sh b369d5215733f79ee2bf58cc966c5931
 /etc/init.d/umountroot 677b1eb8358469b50044663bfbee5699
 /etc/init.d/urandom e6454386bfce38efb5987dd06cb3b21d
 /etc/default/devpts fc857c5ac5fb84d80720ed4d1c624f6e
 /etc/default/halt 18d9844cf8ca8608e2a559a4555e593a
 /etc/default/rcS db3696fc6caa33a1d72b33fa3cec7c42
Description: scripts for initializing and shutting down the system
 The scripts in this package initialize a standard Debian
 system at boot time and shut it down at halt or reboot time.
Homepage: http://savannah.nongnu.org/projects/sysvinit
Original-Maintainer: Debian sysvinit maintainers <pkg-sysvinit-devel@lists.alioth.debian.org>

```


The system more or less works, but it is rather clunky in places.  Is there a way this can be fixed?  I don't like the idea of purging this package and then reinstalling because it is so deep in the system ...

  -- Damien

---

### Post by grahammechanical on 2014-10-11
I have been running the development branch for more than two years. There are two times when I might upgrade to the development version. 1) within the first 4 weeks of the start of the development cycle when the code is still close to the code of the last release. 2) After the Release Candidate image is available. And then I only upgrade to test the upgrade scripts. In between I install the daily image. Utopic release candidate comes out on 16th October with final release on 23rd October. In my opinion it is a bit early to be testing the upgrade process. And that is what you have done.

What can you do.?

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

And hope for the best.  Or install a daily image.

Regards.

---

### Post by damien_d on 2014-10-12
> 2) After the Release Candidate image is available. And then I only upgrade to test the upgrade scripts

I'll keep that in mind of next time.  If this is a bug, then I don't mind filing it (after all, someone has to test!), but in the meantime, I am looking to fix this issue.  If the initscripts package is broken, then a big needs to be filed.  If they are OK on most systems, then we need to work out just what happens to be so special about my system that they do not work.

Nevertheless, since this issue is bit out of my expertise, I'm hoping that someone may be able to point me in the right direction.  I have tried the usual set of instructions (e.g. [http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)) but without success, but since this didn't work, I need a little bit of help in properly diagnosing the system.

  -- Damien

---

### Post by damien_d on 2014-10-15
(Note to Moderators: Should this post be moved to "Ubuntu Developmental Versions"?)

---

### Post by damien_d on 2014-10-17
Solved!  The offender was the proprietary Cisco VPN client. Time to try VPNC again.... You can find the details at:
> [http://forums.debian.net/viewtopic.php?f=30&t=53192](http://forums.debian.net/viewtopic.php?f=30&t=53192)

---

