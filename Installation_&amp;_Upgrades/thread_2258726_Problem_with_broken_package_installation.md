---
title: "Problem with broken package installation"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by cjsmall on 2014-12-30
I have a recent fresh bare metal installation of  Ubuntu Server 14.10 suplemented with the Xubuntu desktop packages.  Everything was working fine.

I was configuring the system from scratch and decided to install sendmail which I have used for decades.  This was done using the Synaptic package manager.   It turned out that the base installation had already included postfix, a program that I've never used.  At this point I'm not sure of the details of the installation, but I believe that postfix was scheduled for removal and then sendmail was to be installed.  Something went wrong  and I started getting installation errors that seemed to, at first, revolve around the spamassassin package.  As subsequent packages were being installed, more problems developed.  In an attempt to walk back from these errors, I removed the sendmail packages and reinstalled postfix.  Unfortunately, this did not correct the problem and the errors began to multiply.  I have investigated many articles that explain how to correct package errors and have tried all of the usual suspects without success:

```
**apt-get -f install**

**dpkg --configure -a**
                
**apt-get update**
a**pt-get clean**
**apt-get autoclean**
**apt-get autoremove**
**apt-get check**

**apt-get -m update**

**apt-get dist-upgrade**
```

I will attach the full output from **dpkg --configure -a **below, but it concludes:

```
[B]Errors were encountered while processing:
 lsb-core
 apcupsd
 apcupsd-cgi
 ebtables
 udev
 mailutils
 smartmontools
 xserver-xorg-core
 gsmartcontrol
 systemd
 libpam-systemd:amd64[/B]
```

In addition, I have a couple of totally unrelated dependancy packages for an uninstalled xtide predictor (**xtide-data** &  **xtide-data-nonfree**) which are scheduled for removal.   However, they cannot be removed because they generate the following typical error:

```
[B]Errors were encountered while processing:
 xtide-data
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
```

I have tried to force the removal without success.  I  cannot install most new packages because **dpkg** wants to remove these packages first and fails.

So my question: Is there a reliable procedure for correcting this condition and getting back to a stable state?   If so, great.

If not, then, at this point,  I am prepared to reinstall the entire OS just so I can move forward once again.  Is there a way to do this from a live system without having to revert back to the install disk where I will have to rebuild my RAID array, etc. and lose all of my current configuration?  Note that I did try an **[B]apt-get upd**ate ; apt-get dist-upgrade[/B] and this fails with:

```
[B]Errors were encountered while processing:
 /var/cache/apt/archives/spamassassin_3.4.0-3ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
```


Thanks.


[HR][/HR]
```
# dpkg --configure -a

dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on lsb-invalid-mta (>= 4.1+Debian11ubuntu8) | mail-transport-agent; however:
  Package lsb-invalid-mta is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.

dpkg: error processing package lsb-core (--configure):
 dependency problems - leaving unconfigured
Setting up apcupsd (3.14.10-2build1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: start runlevel arguments (1 2 3 4 5) do not match apcupsd Default-Start values (2 3 4 5)
update-rc.d: warning: stop runlevel arguments (0 6) do not match apcupsd Default-Stop values (0 1 6)
invoke-rc.d: not a symlink: /etc/rc2.d/S03apcupsd@
invoke-rc.d: dangling symlink: /etc/rc2.d/S03apcupsd@
dpkg: error processing package apcupsd (--configure):
 subprocess installed post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of apcupsd-cgi:
 apcupsd-cgi depends on apcupsd (= 3.14.10-2build1); however:
  Package apcupsd is not configured yet.

dpkg: error processing package apcupsd-cgi (--configure):
 dependency problems - leaving unconfigured
Setting up ebtables (2.0.10.4-3ubuntu1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
invoke-rc.d: not a symlink: /etc/rcS.d/S02ebtables@
invoke-rc.d: dangling symlink: /etc/rcS.d/S02ebtables@
dpkg: error processing package ebtables (--configure):
 subprocess installed post-installation script returned error exit status 102
Setting up udev (208-8ubuntu8.1) ...
invoke-rc.d: not a symlink: /etc/rcS.d/S03udev@
invoke-rc.d: dangling symlink: /etc/rcS.d/S03udev@
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of mailutils:
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.

dpkg: error processing package mailutils (--configure):
 dependency problems - leaving unconfigured
Setting up smartmontools (6.2+svn3841-1.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
invoke-rc.d: not a symlink: /etc/rc2.d/S03smartmontools@
invoke-rc.d: dangling symlink: /etc/rc2.d/S03smartmontools@
dpkg: error processing package smartmontools (--configure):
 subprocess installed post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on udev (>= 149); however:
  Package udev is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gsmartcontrol:
 gsmartcontrol depends on smartmontools; however:
  Package smartmontools is not configured yet.

dpkg: error processing package gsmartcontrol (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of systemd:
 systemd depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package systemd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on systemd (= 208-8ubuntu8.1); however:
  Package systemd is not configured yet.

dpkg: error processing package libpam-systemd:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lsb-core
 apcupsd
 apcupsd-cgi
 ebtables
 udev
 mailutils
 smartmontools
 xserver-xorg-core
 gsmartcontrol
 systemd
 libpam-systemd:amd64
```
[HR][/HR]

---

### Post by schragge on 2014-12-30
The most important dpkg error messages tend to be at the top, not at the bottom of output. In this case, it's probably
```

dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on lsb-invalid-mta (>= 4.1+Debian11ubuntu8) | mail-transport-agent; however:
  Package lsb-invalid-mta is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.

```
Try to install lsb-invalid-mta, at least temporarily, to work around package manager problems.

---

### Post by cjsmall on 2014-12-30
schragge:

I have actually tried to perform this operation previously, and it fails.  To install **lsb-invalid-mta**, postfix as well as the xtide packages are scheduled to be removed.  Because of the corruptions, the package removal fails at the pre-removal script step as seen below.  The mail transport dependencies are totally hosed, but there is some underlying error that is stopping all sorts of normal package operations from occurring.  For example, the master xtide packages are already removed, so emoving the xtide-data packages shoud not be dependencies or dependent upon anything.  Yet their removal fails.

```
#apt-get install lsb-invalid-mta 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  re2c
Use 'apt-get autoremove' to remove it.
Suggested packages:
  lsb
The following packages will be REMOVED:
  postfix xtide-data xtide-data-nonfree
The following NEW packages will be installed:
  lsb-invalid-mta
0 upgraded, 1 newly installed, 3 to remove and 1 not upgraded.
25 not fully installed or removed.
Need to get 5,238 B/1,040 kB of archives.
After this operation, 5,908 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ utopic/main lsb-invalid-mta all 4.1+Debian11ubuntu8 [5,238 B]
Fetched 5,238 B in 0s (15.8 kB/s)          
dpkg: postfix: dependency problems, but removing anyway as you requested:
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is to be removed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is to be removed.
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is to be removed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is to be removed.
 lsb-core depends on lsb-invalid-mta (>= 4.1+Debian11ubuntu8) | mail-transport-agent; however:
  Package lsb-invalid-mta is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is to be removed.

(Reading database ... 315654 files and directories currently installed.)
Removing postfix (2.11.1-1) ...
invoke-rc.d: not a symlink: /etc/rc2.d/S04postfix@
invoke-rc.d: dangling symlink: /etc/rc2.d/S04postfix@
dpkg: error processing package postfix (--remove):
 subprocess installed pre-removal script returned error exit status 102
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by cjsmall on 2014-12-31
Follow up:

Today I threw up my hands and did a complete fresh install of the  system.   Everything went well for the basic packages until I ran  software updater.   A few packages were scheduled to be updated,  including udev and it has now faild in the exact same manner as the previous packages, reporting:

"subprocess installed post-installation script returned error exit status 102"


 I am afraid to install or remove any  other software for fear of corrupting the system further and I  currently do not have a usable system.  Does anyone have a suggestion as to how i can triage this problem affecting this one package before it cascades again into a corrupt system.  How do I identify the underlying post-installation script error that is being generated?  Thanks.

Here is a link to the bug report I submitted on this.

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1406735](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1406735)

---

### Post by schragge on 2014-12-31
Look, the message
> subprocess installed post-installation script returned error exit status 102
says me precisely nothing. It's just a message from dpkg that something went wrong with postinst script for udev. Ok, from the exit status code I can infere that it's probably either invoke-rc.d or update-rc.d that caused dpkg to fail (they tend to error out with this exit status). What I really need to know is the **actual** error messages from invoke-rc.d/update-rc.d. They should be somewhere in the dpkg output prefixed with *invoke-rc.d:* or *update-rc.d:*.

[highlight]Update[/highlight]
Ah sorry, found it in the LP bug report you linked above:
```
Setting up udev (208-8ubuntu8.1) ...
invoke-rc.d: not a symlink: /etc/rcS.d/S03udev@
invoke-rc.d: dangling symlink: /etc/rcS.d/S03udev@

```
So, please check where this symlink is currently pointing to:
```
ls -l /etc/rcS.d/S03udev
```

---

### Post by cjsmall on 2014-12-31
[**[COLOR=#000000]schragge[/COLOR]**]("http://ubuntuforums.org/member.php?u=1783515"):

Thanks for the reply.  I did look into this link error message and it doesnt seem to make sense.

# ls -l  /etc/rcS.d/S03udev
lrwxrwxrwx 1 root root 14 Dec 30 21:58 /etc/rcS.d/S03udev -> ../init.d/udev

# ls -lL  /etc/rcS.d/S03udev
-rwxr-xr-x 1 root root 6583 Oct  7 03:16 /etc/rcS.d/S03udev

# ls -l /etc/init.d/udev
-rwxr-xr-x 1 root root 6583 Oct  7 03:16 /etc/init.d/udev

So, the symlink exists and it points to a proper file.

I was curious to see what the exit status of the udev.postinst  command was, so I ran it again and it produced completely different output from the first run!

> # sh -ex /var/lib/dpkg/info/udev.postinst configure ; echo $?
+ set -e
+ update_hwdb
+ udevadm hwdb --update
+ chrooted
+ stat -c %d/%i /
+ stat -Lc %d/%i /proc/1/root
+ [ 2304/2 = 2304/2 ]
+ return 1
+ in_debootstrap
+ [ -d /debootstrap/ ]
+ return 1
+ invoke-rc.d udev restart
udev stop/waiting
udev start/running, process 11860
+ update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.16.

0-28-generic
W: mdadm: the array /dev/md/dymaxion:x with UUID c052a4db:6908e47c:8f2cac48:2b6c1305
W: mdadm: is currently active, but it is not listed in mdadm.conf. if
W: mdadm: it is needed for boot, then YOUR SYSTEM IS NOW UNBOOTABLE!
W: mdadm: please inspect the output of /usr/share/mdadm/mkconf, compare
W: mdadm: it to /etc/mdadm/mdadm.conf, and make the necessary changes.
+ [ -x /etc/init.d/udev ]
+ update-rc.d udev defaults
+ [ -x /etc/init.d/udev-finish ]
+ update-rc.d udev-finish defaults
+ [ -x /etc/init.d/udevtrigger ]
+ [ -x /etc/init.d/udevmonitor ]
+ [ -x /etc/init.d/udev-fallback-graphics ]
+ [ -x /etc/init.d/lvm2 ]
+ update-rc.d lvm2 defaults
+ dpkg-maintscript-helper rm_conffile /etc/init.d/udev-mtab 204-1~ -- configure
dpkg-maintscript-helper: error: couldn't identify the package
1

If you refer back to the bug report link above, the only thing that happened between the two runs was that the:

    # i**nvoke-rc.d udev restart; echo $?**

command was subsequently manually run.   Now, the script is failing at the  **dpkg-maintscript-helper**  command!

---

### Post by schragge on 2014-12-31
[s]Well, in order  for dpkg-maintscript-helper not to fail you must supply the second parameter to postinst script -- most recently configured version of the package.[/s] See diagram for upgrading in [https://wiki.debian.org/MaintainerScripts#Upgrading](https://wiki.debian.org/MaintainerScripts#Upgrading)
Try
```
sh -x /var/lib/dpkg/info/udev.postinst configure 208-8ubuntu8
```

[highlight]Update[/highlight]
Sorry, ignore  what I said. dpkg-maintscript-helper shouldn't fail if invoked with only one parameter. But AFAICS, it works only if invoked as part of post-installation process with environment set by dpkg.

Not sure if this works, but you can try:
```
dpkg -D2 --pre-invoke='set -x' --configure udev
```

---

### Post by cjsmall on 2015-01-02
schragge:

Thanks for the very helpful suggestions.  I have also been working with someone who responded to the bug report that I filed about this on lanchpad.  I did manage to clear the error with the udev package but ran into the identical problem later when spamassassin was attempting to be reinstalled.  Based upon suggestions, I ran the following command (similar for udev) and received this output:

# env DPKG_MAINTSCRIPT_PACKAGE=spamassassin DPKG_MAINTSCRIPT_NAME=postinst sh -ex /var/lib/dpkg/info/spamassassin.postinst configure ; echo $?

+ set -e
+ [ configure = triggered ]
+ [ configure = configure ]
+ getent passwd debian-spamd
+ mkdir -p /var/lib/spamassassin
+ stat -c %U /var/lib/spamassassin
+ OWNER=debian-spamd
+ stat -c %G /var/lib/spamassassin
+ GROUP=debian-spamd
+ dpkg-statoverride --list /var/lib/spamassassin/sa-update-keys
+ [ debian-spamd:debian-spamd != debian-spamd:debian-spamd ]
+ test -d /var/lib/spamassassin/sa-update-keys
+ su - debian-spamd -c sa-update --gpghomedir /var/lib/spamassassin/sa-update-keys         --import /usr/share/spamassassin/GPG.KEY
+ deb-systemd-helper debian-installed spamassassin.service
+ deb-systemd-helper unmask spamassassin.service
+ deb-systemd-helper --quiet was-enabled spamassassin.service
+ deb-systemd-helper update-state spamassassin.service
+ [ -x /etc/init.d/spamassassin ]
+ update-rc.d spamassassin defaults 19 21
+ [ -x /etc/init.d/spamassassin ]
+ invoke-rc.d spamassassin start
SpamAssassin Mail Filter Daemon: disabled, see /etc/default/spamassassin
0


Well, it completed with a successful return value.  I then went back to synaptic and tried installing another unrelated package.  Synaptic then went ahead and configured the spamassassin and related packages itself.  There must be a flag that gets set somewhere that indicates that the post-install was successful and that didn't get set when I ran the command manually, so synaptic went ahead and ran it again itself.

The bottom line is that all packages that were giving me problems are apparently now properly installed and I can move forward with the remainder of the system installation.

I really appreciate your help in this matter, and if there is anything else you would like to have me report, please ask.  Have a great New Year.

---

### Post by schragge on 2015-01-02
Glad you've got sorted it out. Happy and healthy New Year to you, too.

---

### Post by mörgæs on 2015-01-02
Please mark the thread 'solved'.

---

