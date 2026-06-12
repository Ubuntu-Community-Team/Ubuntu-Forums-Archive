---
title: "Dapper upgrade grub issue"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by AZMel on 2006-06-14
I upgraded to Dapper from Breezy using the Alternate disk and also ran the apt-get upgrades to ubuntu and kubuntu-desktop. 

When I reboot my monitor only displays "VGA Mode Out Of Range."  It will get to the KDE desktop but it will not show the grub splash screen.  When I shut down all I see is the text shutdown, not the graphical shutdown.

What should I look at to try to fix the VGA mode issue and the boot/shutdown graphics?

Thanks,
Mel

---

### Post by AZMel on 2006-06-19
Am I the only one with this issue?  :-)

Mel

---

### Post by zxee on 2006-06-19
I'm not sure if the error you're getting is a monitor quirk or something else, but as far as I understand what you've described you could try typing (in a shell or the commandline)
dpkg-reconfigure xserver-xorg <enter> and then select the video driver and monitor resolution(s) appropriate to your system. Hope that helps.

---

### Post by ozstriker on 2006-06-20
I have a similar problem, also with a 2005fpw. However it's with a Nvidia card (albeit an old one), so it could be down to something else.

---

