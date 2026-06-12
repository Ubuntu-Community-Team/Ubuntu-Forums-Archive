---
title: "dual boot ubuntu on laptop - xserver problem"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by illusion on 2006-12-27
Hey,

I'm installing ubuntu 5.1 on a hp pavilion dv6110 laptop.  The reason im using 5.1 is because ubuntu 6 and xubuntu 6 just freeze during installation.  I am creating a dual boot system, and I have used qtparted to repartion the ntfs drive successfully.  Then through the ubuntu installation have used the free space to install ubuntu.  Everything is fine through the installation, until it asks for the desired resolution for xserver.  I select a resolution but then when I start ubuntu after the installation from the dual boot menu, it displays the message "xserver not configured properly", and kicks out to a command line login prompt.  I have tried 'dpkg-reconfigure xserver-org', and going through configuring it that way but with no luck.  

Any suggestions or input would be greatly appreciated,
Illusion

---

### Post by dbbolton on 2006-12-28
boot from a live cd, mount your linux partition, and post the contents of /etc/X11/xorg.conf

---

### Post by illusion on 2006-12-28
Hey,

Just a note, in case someone runs into something similar.  I was able to get ubuntu 6 installed on the pavilion dv6110 adding the following boot parameters (press f6 for options on the initial screen). 

noapic nolapic

thanks for the assistance,
Illusion

---

