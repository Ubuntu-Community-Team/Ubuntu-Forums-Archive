---
title: "Update totally screwed up apt and didn't complete."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by EnterDaMatrix on 2007-10-19
Well, I ran the update and about halfway through installing it crashed. Immediately after gnome and all the task bars crashed. I'm very reluctant to restart. Now when I try to run synaptic it requires than I run "sudo dpkg --configure -a". I run this and here is the output:
```
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not installed.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
Setting up cvs (1:1.12.13-8) ...
install-info(/usr/share/info/cvs.info): failed to lock dir for editing! File exists
try deleting /usr/share/info/dir.lock?
dpkg: error processing cvs (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not installed.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-fonts-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not installed.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on texlive-common (>= 2007); however:
  Package texlive-common is not installed.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing gettext (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up ed (0.7-1build1) ...
install-info(/usr/share/info/ed.info.gz): failed to lock dir for editing! File exists
try deleting /usr/share/info/dir.lock?
dpkg: error processing ed (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not installed.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
Setting up wget (1.10.2-3ubuntu1) ...
install-info(/usr/share/info/wget.info): failed to lock dir for editing! File exists
try deleting /usr/share/info/dir.lock?
dpkg: error processing wget (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not installed.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on wget; however:
  Package wget is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
Setting up screen (4.0.3-0.4ubuntu2) ...
 Removing any system startup links for /etc/init.d/screen-cleanup ...
install-info(/usr/share/info/screen.info): failed to lock dir for editing! File exists
try deleting /usr/share/info/dir.lock?
dpkg: error processing screen (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of msttcorefonts:
 msttcorefonts depends on wget; however:
  Package wget is not configured yet.
dpkg: error processing msttcorefonts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on screen; however:
  Package screen is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up gv (1:3.6.3dfsg-2ubuntu1) ...
install-info(/usr/share/info/gv.info): failed to lock dir for editing! File exists
try deleting /usr/share/info/dir.lock?
dpkg: error processing gv (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2007-7); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2007-7); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kernel-package:
 kernel-package depends on gettext; however:
  Package gettext is not configured yet.
dpkg: error processing kernel-package (--configure):
 dependency problems - leaving unconfigured
Setting up nano (2.0.6-2) ...
install-info(/usr/share/info/nano.info): failed to lock dir for editing! File exists
try deleting /usr/share/info/dir.lock?
dpkg: error processing nano (--configure):
 subprocess post-installation script returned error exit status 1
Setting up time (1.7-21build1) ...
install-info(time): failed to lock dir for editing! File exists
try deleting /usr/share/info/dir.lock?
dpkg: error processing time (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of po-debconf:
 po-debconf depends on gettext (>= 0.16); however:
  Package gettext is not configured yet.
dpkg: error processing po-debconf (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing m4 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up cpio (2.8-1ubuntu2) ...
install-info(/usr/share/info/cpio.info): failed to lock dir for editing! File exists
try deleting /usr/share/info/dir.lock?
dpkg: error processing cpio (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on cpio; however:
  Package cpio is not configured yet.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kommander:
 kommander depends on gettext; however:
  Package gettext is not configured yet.
dpkg: error processing kommander (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alien:
 alien depends on cpio; however:
  Package cpio is not configured yet.
dpkg: error processing alien (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on po-debconf; however:
  Package po-debconf is not configured yet.
dpkg: error processing debhelper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on cpio (>= 2.4.2-2); however:
  Package cpio is not configured yet.
dpkg: error processing dpkg-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on cpio; however:
  Package cpio is not configured yet.
 ubuntu-standard depends on ed; however:
  Package ed is not configured yet.
 ubuntu-standard depends on nano; however:
  Package nano is not configured yet.
 ubuntu-standard depends on time; however:
  Package time is not configured yet.
 ubuntu-standard depends on wget; however:
  Package wget is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-2.6.22-14-generic:
 linux-image-2.6.22-14-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on initramfs-tools (>= 0.85eubuntu12); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing console-setup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-generic:
 linux-restricted-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of volumeid:
 volumeid depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing volumeid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-2.6.22-14-386:
 linux-image-2.6.22-14-386 depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-2.6.22-14-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of devscripts:
 devscripts depends on dpkg-dev; however:
  Package dpkg-dev is not configured yet.
dpkg: error processing devscripts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brltty:
 brltty depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing brltty (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-generic:
 linux-ubuntu-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.22-14-generic; however:
  Package linux-restricted-modules-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dh-make:
 dh-make depends on debhelper (>= 5); however:
  Package debhelper is not configured yet.
 dh-make depends on dpkg-dev; however:
  Package dpkg-dev is not configured yet.
dpkg: error processing dh-make (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on dpkg-dev (>= 1.13.5); however:
  Package dpkg-dev is not configured yet.
dpkg: error processing build-essential (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alsa-source:
 alsa-source depends on dpkg-dev; however:
  Package dpkg-dev is not configured yet.
 alsa-source depends on debhelper (>= 5.0.37); however:
  Package debhelper is not configured yet.
dpkg: error processing alsa-source (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udev:
 udev depends on volumeid (= 113-0ubuntu16); however:
  Package volumeid is not configured yet.
 udev depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-386:
 linux-restricted-modules-2.6.22-14-386 depends on linux-image-2.6.22-14-386; however:
  Package linux-image-2.6.22-14-386 is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
 ubuntu-minimal depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
 ubuntu-minimal depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of usplash-theme-ubuntu:
 usplash-theme-ubuntu depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing usplash-theme-ubuntu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of usplash:
 usplash depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing usplash (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmtp6:
 libmtp6 depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing libmtp6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on libmtp6; however:
  Package libmtp6 is not configured yet.
dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)

```

I originally had Edgy on this computer and I had upgraded from that successfully. Hopefully there is a way to resolve this because this is my work machine.

---

### Post by Hoppiesbox on 2007-10-20
I'm having a similar problem here:
[http://ubuntuforums.org/showthread.php?t=582616](http://ubuntuforums.org/showthread.php?t=582616)

Have you solved this problem yet, or found a solution?

---

