---
title: "Need to build offline driver base for legacy video cards"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by DRPend on 2008-01-28
[SIZE="4"]I genned up a couple of dozen Dell GX110's (Old PIII 733's) with Edubuntu (Dapper Drake) for some local schools and several of them had add on video cards. I was in a hurry so I just set the BIOS to use onboard cards and kept going. Near the end I figured out that the wrong Display adapter was being added in the xorg.conf and eventually figured out how to install the appropriate drivers. They are mostly old Nvidia cards and one or two ATI cards.  The systems don't have a lot of ram, so it's good to use the cards. As well it's confusing people moving the systems at the schools. My problem is that I've never used Debian based systems to add stuff without having an internet connection. I used apt-get for the restricted modules and the legacy drivers.  Can I just untar the libraries onto the system and drop them into local /lib files?  It seems I'd want to use dpkg somehow to keep from confusing aptitude.  Any suggestions?

Thanks[/SIZE][

---

