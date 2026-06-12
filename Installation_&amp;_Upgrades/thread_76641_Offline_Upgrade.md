---
title: "Offline Upgrade"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by punkrockguy318 on 2005-10-15
Is there any upgrade disk for Breezy?  I'm running Ubuntu 5.04 on four computers that do not have connectivity to the internet.  How would I go about upgrading them to Breezy?

Lukas

---

### Post by Strangerdave on 2005-10-15
The only thing that comes to mind is get on the mailing list and get yourself some of the free CD's that they send.  Other than that, if you could get to atleast one computer with internet and download the iso, burn the image and get it back to the comps with no internet you'd be laughing.

-SD-

---

### Post by punkrockguy318 on 2005-10-15
[QUOTE=Strangerdave]The only thing that comes to mind is get on the mailing list and get yourself some of the free CD's that they send.  Other than that, if you could get to atleast one computer with internet and download the iso, burn the image and get it back to the comps with no internet you'd be laughing.

-SD-[/QUOTE]


Yeah, I do have a Breezy disk, I'm running Breezy on this PC right now.  But do the install disks also do upgrades without reformatting?

---

### Post by archivenz on 2005-10-15
just make sure that the breezy disk is included in /etc/apt/sources.list 

i think sudo apt-cdrom add  while the breezy disk is in the drive will add breezy to the list


then apt-get update and apt-get dist-upgrade   and you should be fine. I upgraded from 5.04 to 5.10 without a problem

hope this works

---

