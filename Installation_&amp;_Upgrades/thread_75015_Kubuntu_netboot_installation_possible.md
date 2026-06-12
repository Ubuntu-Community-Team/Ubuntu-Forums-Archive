---
title: "Kubuntu netboot installation: possible?"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by preater on 2005-10-13
Hi all,

I have an [IBM Thinkpad X22](http://www.thinkwiki.org/wiki/Category:X22) which I'd like to install Kubuntu 5.10 onto.  The Thinkpad X series are 'subnotebooks', meaning as standard they don't have a floppy or CD/DVD drive, so the usual installation method isn't possible.

The machine does have a PXE-capable network card, so I thought I'd install Ubuntu by booting the installer over the network.  The mechanics of this aren't a problem for me - I'd be doing something like this: [Ubuntu PXE Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install) using Breezy, netboot files are [here](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/).

I'd prefer to go straight to Kubuntu rather than installing Ubuntu and adding on kubuntu-desktop - much less downloading. :D Is a network install of Kubuntu possible?  I can't find any instructions or files for PXE boot.

Thanks in advance.

Andrew

---

### Post by preater on 2005-10-13
Oops, just read [bug 10209](https://bugzilla.ubuntu.com/show_bug.cgi?id=10209).  If you were wondering about a Kubuntu netboot using PXE etc., it ain't possible.  Yet.

Andrew

---

### Post by bodyguard on 2006-03-30
fixed see [https://launchpad.net/distros/ubuntu/+source/debian-installer/+bug/16507/+index](https://launchpad.net/distros/ubuntu/+source/debian-installer/+bug/16507/+index)

---

### Post by GSMD on 2006-05-05
Didn't work with Kubuntu 6.06 Beta2.
What I get is a server installation with Ubuntu boot screen.
Anyone managed to install GUI Kubuntu via pxe?

---

