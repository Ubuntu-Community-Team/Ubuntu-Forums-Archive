---
title: "Restarting a hidden system"
date: 2019-07-14
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2019-07-14
I spent quite a few hours getting a Kubuntu system set up, and when I powered down the computer it was still working correctly.  But now when I power it up again, I get the Kubuntu banner -- and then a blank screen.  I don't want to go through all thework of setting that system up again, since I'm sure it's all there, just hidden.  I can get a Kubuntu system running from a memory stick, and from there I can access the hard drive.  Is there a way I can get my previous system back?

---

### Post by VMC on 2019-07-14
From grub boot menu, edit "e", edit out "quiet" splash" from the linux line of grub.cfg, then F10, and see what messages appear or where it hangs up.

---

### Post by pwabrahams on 2019-07-14
Well, after poking around the net for a while I actually managed to solve the problem:

1. I booted into the recovery system (a Grub choice),

2. After the gears whirred for a while, I got to a menu with, among other choices, **resume[B]**[/B].

3. (after more whirring of gears) I got to a command prompt.  I logged in and immediately went into superuser mode with **sudo su[B]**[/B].

4. (This is the really nonobvious part.)  I typed **apt-get install xorg**.

5. (More whirring of gears) I typed **reboot**.

6. My system came back to life!!!

Perhaps the Sages of Ubuntu will be able to provide an explanation of all this.  Meanwhile, I think this is a recipe that works for the nonexperts.

---

### Post by cruzer001 on 2019-07-14
nomodeset?

[https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)

Not familiar with KDE so just some guesswork on my part.

---

### Post by again? on 2019-07-15
> **pwabrahams said:**
> Well, after poking around the net for a while I actually managed to solve the problem:
4. (This is the really nonobvious part.)  I typed **apt-get install xorg**.


Perhaps the Sages of Ubuntu will be able to provide an explanation of all this.  Meanwhile, I think this is a recipe that works for the nonexperts.
xorg is a default install [metapackage]("https://help.ubuntu.com/community/MetaPackages"), which means it's just a list of dependencies.
If you remove one of those dependencies it will remove the xorg metapackage as well.

If I try to install xorg...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt install xorg**
[sudo] password for glen:         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg is already the newest version (1:7.7+19ubuntu7.1).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

Maybe somewhere in your customizing you removed an xorg dependency needed for a graphical boot.
Show xorg dependencies...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt show xorg** 
Package: xorg
Version: 1:7.7+19ubuntu7.1
Priority: optional
Section: x11
Origin: Ubuntu
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 57.3 kB
Provides: x-window-system, x-window-system-core
[COLOR="#FF0000"]Depends: xserver-xorg (>= 1:7.7+19ubuntu7.1), libgl1-mesa-glx | libgl1, libgl1-mesa-dri, libglu1-mesa, xfonts-base (>= 1:1.0.0-1), x11-apps, x11-session-utils, x11-utils, x11-xkb-utils, x11-xserver-utils, xauth, xinit, xfonts-utils, xkb-data, xorg-docs-core, gnome-terminal | xterm | x-terminal-emulator, xinput[/COLOR]
Recommends: xfonts-scalable (>= 1:1.0.0-1)
Suggests: xorg-docs, xfonts-100dpi (>= 1:1.0.0-1), xfonts-75dpi (>= 1:1.0.0-1), x11-xfs-utils
Homepage: http://www.x.org/
Task: ubuntu-desktop, kubuntu-desktop, xubuntu-core, xubuntu-desktop, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Supported: 5y
Download-Size: 3,076 B
APT-Manual-Installed: yes
APT-Sources: http://ftp.iinet.net.au/pub/ubuntu bionic-updates/main amd64 Packages
Description: X.Org X Window System
 This metapackage provides the components for a standalone workstation
 running the X Window System.  It provides the X libraries, an X server, a
 set of fonts, and a group of basic X clients and utilities.
 .
 Higher level metapackages, such as those for desktop environments, can
 depend on this package and simplify their dependencies.
 .
 It should be noted that a package providing x-window-manager should also
 be installed to ensure a comfortable X experience.

N: There is 1 additional record. Please use the '-a' switch to see it
```

Search your apt history in **/var/log/apt/history.log**  for "xorg" and see what was installed at the same time.

Or maybe you just encountered a bug???

---

### Post by pwabrahams on 2019-07-15
Even as a nonexpert, **xorg** seemed to me to be something that should have been there.  The fact that bootup died after displaying the Kubuntu banner was proof positive that *something* was wrong.  So given this particular misbehavior and the fact that I was working with a crippled system in trying to deal with it, what would have been a wiser way to go about it?

---

### Post by again? on 2019-07-15
I am not saying you did anything unwise attempting to fix your system... 
just tying to help you find out how you got there.
Did you check in /var/log/apt/history.log what packages were pulled in when you reinstalled xorg?

---

