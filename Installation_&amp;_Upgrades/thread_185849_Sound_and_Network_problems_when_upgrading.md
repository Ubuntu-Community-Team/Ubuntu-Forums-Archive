---
title: "Sound and Network problems when upgrading"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by lpet_de on 2006-06-01
Hi,
I just upgraded a Kubuntu 5.10 to Dapper by changing the sources.list and doing "apt-get dist-upgrade". Not sure if that's the recommended procedure though.
The Computer is an old 366Mhz Celeron with Network via PCMCIA-Card.

Mostly it worked fine, only the sound was lost completely and in most cases after boot the local network is not configured.

The sound problem I could solve myself, it was simply that the kernel-module for the Sound Chip was not loaded. In this case the Chip is "ESS Technology  ES1969 Solo-1" and the module for it is called "esssolo1". I simply added a line "esssolo1" to /etc/modules and now the sound works again. At least it did until the first reboot, now I get the windows (after KDE has started) "Sound server fatal error: cpu overload, aborting" whenever KDE wants to make a sound (startup, closing windows with unsaved data, ...). Not always, sometimes the sound is there, but in about 50% of the cases.

The hint that it might be the Kernel module came from here: ;) [http://lists.debian.org/debian-user/2005/07/msg02794.html]("http://lists.debian.org/debian-user/2005/07/msg02794.html")

The Networking-Problem is this: The card is found during boot and identified (correctly) as NE2000-compatible. In /etc/network/interfaces it is written that eth0 is supposed to be initialized via DHCP, but that did not happen. An "ifconfig" after boot only shows the lo-interface.
If i do "sudo ifup eth0", an IP-Address is gathered via DHCP and everything works fine.

Any Idea why this isn't done at boot time?
Dmesg-Output and the output of the "ifup"-Command are attached.

Greets

---

### Post by lpet_de on 2006-06-01
The Sound problem is fixed now. Here: [http://lists.debian.org/debian-qt-kde/2004/02/msg00151.html]("http://lists.debian.org/debian-qt-kde/2004/02/msg00151.html") people advice to hand-select the Hardware (ALSA/OSS/...) in the KDE configuration module. That worked fine for me, just instead of "Arts" (as in the posting above) I had to choose "OSS with Threads" to make it work.

Now sound works completely, system notifications, media players, ... .

---

### Post by VinnyM69 on 2006-06-01
First off, great distro and great release.  One minor problem. I'm a former Breezy user and did a clean install today with the Dapper release.  I noticed my sound works of for Gaim, but doesn't work with amaroK.  Sound engine shows as wine and I believe it was arts or Gstreamer in Breezy. Device Manager is showing a VIA Technologies AC97 controller and VIA 8235 ALSA Playback Device.  

Any help fixing this would be greatly appreciated...........TIA

---

