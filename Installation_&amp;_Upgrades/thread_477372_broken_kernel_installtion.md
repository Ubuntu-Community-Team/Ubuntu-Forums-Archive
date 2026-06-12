---
title: "broken kernel installtion?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by kristus on 2007-06-18
Whenever I do something with apt, I get the following errors. Besides taking alot of extra time each time I use apt, I  guess it indicates some kind of breakage in my system which I of course want to have repaired. I have tried to re-install linux-image-* et. al. without success; the errors remain. What should I do? I guess it have something to do with me migrating my whole system into a dm-crypt partition not long ago. Here are the errors highlighted by synaptic:
> E: linux-image-2.6.20-16-generic: subprocess post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.20-16-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-image-2.6.20-15-generic: subprocess post-installation script returned error exit status 17
E: linux-restricted-modules-2.6.20-15-generic: dependency problems - leaving unconfigured

Here is the complete log of apt-get as shown in synaptic: 
> debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gnome -- is libgnome2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Selecting previously deselected package mozilla-thunderbird-enigmail.
(Reading database ... 119312 files and directories currently installed.)
Unpacking mozilla-thunderbird-enigmail (from .../mozilla-thunderbird-enigmail_2%3a0.94.2-0ubuntu1_i386.deb) ...
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gnome -- is libgnome2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Internal Error: Could not find image (/boot/vmlinuz-2.6.20-16-generic)
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.20-15-generic (2.6.20-15.27) ...
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gnome -- is libgnome2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Running depmod.
Finding valid ramdisk creators.
Using /usr/sbin/mkinitramfs to build the ramdisk.
cryptsetup: WARNING: invalid line in /etc/crypttab - 
Failed to symbolic-link boot/initrd.img-2.6.20-15-generic to initrd.img.
dpkg: error processing linux-image-2.6.20-15-generic (--configure):
 subprocess post-installation script returned error exit status 17
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-15-generic:
 linux-restricted-modules-2.6.20-15-generic depends on linux-image-2.6.20-15-generic; however:
  Package linux-image-2.6.20-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-15-generic (--configure):
 dependency problems - leaving unconfigured
Setting up mozilla-thunderbird-enigmail (0.94.2-0ubuntu1) ...
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic
 linux-image-2.6.20-15-generic
 linux-restricted-modules-2.6.20-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.20-15-generic (2.6.20-15.27) ...
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gnome -- is libgnome2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Running depmod.
Finding valid ramdisk creators.
Using /usr/sbin/mkinitramfs to build the ramdisk.
cryptsetup: WARNING: invalid line in /etc/crypttab - 
Failed to symbolic-link boot/initrd.img-2.6.20-15-generic to initrd.img.
dpkg: error processing linux-image-2.6.20-15-generic (--configure):
 subprocess post-installation script returned error exit status 17
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gnome -- is libgnome2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Internal Error: Could not find image (/boot/vmlinuz-2.6.20-16-generic)
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-15-generic:
 linux-restricted-modules-2.6.20-15-generic depends on linux-image-2.6.20-15-generic; however:
  Package linux-image-2.6.20-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-15-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured

---

### Post by kristus on 2007-06-19
It seems all this was due to my /boot not being mounting while performing some random kernel update (kernel 2.6.20-15 --> 2.6.20-16). Shame on apt/ubuntu/whatever for noticing that /booot wasn't mounted!

The fix was to move all the stuff from the unounted /boot to the mounted /boot, as it should have been from the beginning.

---

### Post by Pstevens on 2007-07-20
Newbie questions coming up - please help!

> It seems all this was due to my /boot not being mounting 
What does "mounted" mean?

> The fix was to move all the stuff from the unounted /boot to the mounted /boot, as it should 
> have been from the beginning.

How exactly does one move stuff between a mounted and an unmounted boot?

I have almost the same error messages on one of my machines.

---

