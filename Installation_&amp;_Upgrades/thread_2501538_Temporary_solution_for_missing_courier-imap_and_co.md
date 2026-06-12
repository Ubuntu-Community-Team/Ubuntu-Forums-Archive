---
title: "Temporary solution for missing courier-imap and courier-webadmin packages"
date: 2024-10-11
forum: Installation &amp; Upgrades
---

### Post by aathan on 2024-10-11
Those of you upgrading to 24.04 may find certain courier packages are missing. This appears to be due to their reliance on deprecated libraries (PCRE). This solution installs the deleted packages successfully, but may create security issues.

I've sent an email to the courier-users mailing list to see if the problem can be solved upstream. Meanwhile, happy hunting.

[FONT=&amp][FONT=Arial]The --ignore-depends is necessary. The URLs are derived by using the launchpad links below, and clicking on the "version" column links
[https://launchpad.net/ubuntu/noble/amd64/courier-imap](https://launchpad.net/ubuntu/noble/amd64/courier-imap)
[https://launchpad.net/ubuntu/noble/amd64/courier-webadmin](https://launchpad.net/ubuntu/noble/amd64/courier-webadmin)


These commands (as root) will install the packages the ubuntu release managers removed from 24.04. This seemed to work just fine for me, for now.


wget [http://launchpadlibrarian.net/708904399/courier-imap_5.0.13+1.0.16-3.2build1_amd64.deb](http://launchpadlibrarian.net/708904399/courier-imap_5.0.13+1.0.16-3.2build1_amd64.deb)
dpkg --ignore-depends=courier-base -i courier-imap_5.0.13+1.0.16-3.2build1_amd64.deb
wget [http://launchpadlibrarian.net/708904405/courier-webadmin_1.0.16-3.2build1_amd64.deb](http://launchpadlibrarian.net/708904405/courier-webadmin_1.0.16-3.2build1_amd64.deb)
dpkg --ignore-depends=courier-base -i courier-webadmin_1.0.16-3.2build1_amd64.deb


[/FONT]PS: I could not tag this thread with courier-webadmin because I don't have permission to create tags.


[/FONT]

---

