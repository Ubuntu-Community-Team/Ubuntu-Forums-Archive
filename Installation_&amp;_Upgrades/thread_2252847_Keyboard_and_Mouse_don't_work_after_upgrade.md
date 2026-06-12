---
title: "Keyboard and Mouse don't work after upgrade"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by febros on 2014-11-15
Hello

Yesterday I upgrade Ubuntu Studio 14.04 to 14.10. I had some issues during the installation, but everything seemed fine at the last. Obvioulsy it was not: after rebooting mouse and keyboard don't work.

Anyway I can switch to the command line with Ctrl-Alt-F1. And then the keyboard works unless I switch again to GUI

Right now I've got this, without running any command:

~$ [ 332.230495] usb usb1-port3: disabled by hub (EMI?), re-enabling...
[  343.843872] systemd-udevd[3032]: Failed to apply ACL on /dev/sr1: No such file or directory
[  343.843888] systemd-udevd[3032]: Failed to apply ACL on /dev/sr1: No such file or directory
[  343.848918] systemd-udevd[3032]: Failed to apply ACL on /dev/sr1: No such file or directory
[  343.848943] systemd-udevd[3032]: Failed to apply ACL on /dev/sr1: No such file or directory

How could I start fixing this?

---

### Post by febros on 2014-11-17
I've tried several things, none of them successful.

Please, notice I have no idea about what I'm talking about, maybe it's non-sense: I think the problem might be with Xorg, since none of the environments I've tried work (Xfce, LXDE, gnome). I've also changed Lightdm for gdm, and mouse and keyboard work fine on Lightdm until I log in (on gdm only keyboard works).

When I run startx I get this message:
...
the XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:   Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) AIGLX: Suspending AIGLX clients for VT switch

---

