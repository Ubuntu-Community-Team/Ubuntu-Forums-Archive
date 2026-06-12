---
title: "Ubuntu 11.04 Beta 2 Live CD - Blank Screen"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by kj4ohh on 2011-04-23
Hello,

I am trying to get 11.04 beta 2 to install on a system that is currently running 10.10.

I had one of the early alpha versions running but ever since alpha 2 or so, I can't get the installer to boot up.  It always goes to a blank screen or my monitors go to sleep.

I have checked the ISOs md5sum to ensure it's a good copy.

I have an AMD Radeon HD 6800 series card.  It works fine in 10.10

If I use the "nomodeset" as a boot parameter on the live cd I get dropped to the shell.  I copied the /var/log directory to a usb stick and I am attaching the Xorg.0.log file in the hopes someone can figure out what's going on...

When I get dropped to the shell and try to do a "startx" I can an identical log file, under the name Xorg.1.log.  Both log files have the same errors.

I had to compress the log file as it was slightly over the allowed size for a text attachment.

---

### Post by mörgæs on 2011-04-23
Alphas and betas are only made for finding errors. Please open a bug report here:
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

By the way, why do you want to install a beta, if the alpha installs all right?

---

### Post by kj4ohh on 2011-04-23
> Alphas and betas are only made for finding errors.
Yes, I know I'm a long time Linux user, since the late 90's

> Please open a bug report here:
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) Already tried that, clicking the submit bug link brings you to a page asking you to use the ubuntu-bug application, which would upload info for the wrong version of ubuntu I'm trying to report on.

I didn't try to use ubuntu-bug from the command line once I was able to get to the shell from the 11.04 live cd.  I may give that a shot.

> By the way, why do you want to install a beta, if the alpha installs all right? After a few updates, it stopped working and I haven't been able to get a live cd to install since alpha 2 or 3, so I've stuck with 10.10

---

### Post by mörgæs on 2011-04-23
If you install any kind of 11.04 (an alpha, for example) and apply all updates, you will get to the newest version in one step (that is the beta as of now).

---

### Post by amaster on 2011-04-23
Maybe it's related  with [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/674984/comments/16](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/674984/comments/16) (see #16)

try to install xorg's drivers for radeon card.

---

