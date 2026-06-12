---
title: "Custom PXE Lubuntu Install For Kiosk"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by Lubd on 2012-02-10
Hi all,
 
I am setting up a kiosk style system. Chrome browser only. Diskless machine, no persistent data.
 
 
I want to customise a lightweight distro, probably Lubuntu, and use a PXE boot from a server. I want zero manual intervention necessary on boot.
 
The server and PXE is set up and I can do the necessary custom config of a Lubuntu system but I am unclear as to how to create the necessary custom boot files.
 
How do I generate the necessary boot files for the server from a custom Lubuntu configuration?
 
Do I need to create a live usb Lubuntu install running, configure the system on the kiosk machine and then somehow export an iso or file set of the newly configured system?
 
Confused. :confused:
 
Cheers for any advice.

---

### Post by Rodney9 on 2012-02-10
This page has many tips and links for setting up a kiosk -

[http://ubuntuforums.org/showthread.php?t=1891594&highlight=kiosk](http://ubuntuforums.org/showthread.php?t=1891594&highlight=kiosk)

[Distro Watch]("http://distrowatch.com/") has this one: Webconverger 11.2
	Kai Hendry has announced the release of Webconverger 11.2, a Debian-based, browser-only live CD designed for Internet kiosks: "11.0 was a great and popular release. Thank you! 11.2 builds on that with: Firefox 10; Linux kernel 3.2 with TCP proportional rate reduction; removal of confusing tab groups from Firefox, making things simpler; stop accidental downloads of unknown mimetypes, therefore saving precious bandwidth; for developers - build upgraded to live build a42 from Debian Live and source has moved to Github; 10 second retry on net error for cases where network isn't quite ready; more (non-free) wireless firmware - realtek, libertas, brcm80211 and atheros, which means your wireless kiosk will almost certainly work.

Rodney

---

### Post by Lubd on 2012-02-12
Hi,
 
Thanks for the info. Unfortunately I checked out Webconverger and found that it could only do live boot from usb or cd.
 
I want live boot functionality but with a PXE net boot.
 
Has anyone any idea if this is possible with Webconverger and if so how? Do they offer this as part of their customisation service, do you have to roll your own install, or is it a simple config file tweak?
 
Details urgently needed please.
 
Many thanks.

---

