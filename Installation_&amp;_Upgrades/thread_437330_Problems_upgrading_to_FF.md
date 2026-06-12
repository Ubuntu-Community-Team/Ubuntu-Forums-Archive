---
title: "Problems upgrading to FF"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by C.Barr on 2007-05-08
I'm no linux expert by any means, but I do need the latest version installed so I can be up to date for testing websites in linux, and also this limit my use of Windows, so thats always a plus. :P

So I open up Update Manager and click the upgrade button and it tells me "Failed to fetch file:/usr/pluto/deb-cache/./Packages.gz File not found". 

Ok, fine.  So I download the alternate CD image, mount that and it says the same thing when I tell it to grab updates from the net.  So I now try it withotu grabbing updates from the net and it spews back a huge list of files it failed to get:

```
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/s/samba/smbclient_3.0.24-2ubuntu1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/s/samba/samba-common_3.0.24-2ubuntu1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/s/scim/scim-gtk2-immodule_1.4.4-7ubuntu1_i386.deb MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/s/scim/scim-modules-socket_1.4.4-7ubuntu1_i386.deb MD5Sum mismatch
```
Thats just about 1/4 of the list, I didn't want to make a gigantic post with all of it.

So, there you have it.  What can I do to upgrade from 6.10 to FF?

---

### Post by starcraft.man on 2007-05-08
Just a question here... and I might be wrong... but why would you have to upgrade your entire system to test webpages with the latest Ubuntu? I had firefox 2.0.0.3 installed in edgy, and to my knowledge there isn't a difference between it installed in Edgy and Feisty... so why do you "need" to upgrade to test how pages render?

I'm also not sure why you mounted the ISO... isn't it logical to burn it so you have a spare should any catastrophe happen? That said... I don't really know why important modules like samba would fail to download, I highly doubt that the servers hosting those files were down... so maybe there is something wrong with your install?

I just try to make sense of things, but maybe ya should try a clean install with that alternate disk? Might be the shortest way to a working version...

Just a diagnostic question, but you didn't happen to use Automatix2 did ya? People keep posting all these problems upgrading when using that...

---

### Post by C.Barr on 2007-05-11
Sorry for taking so long, I've been busy.

You're right, I don't NEED the latest, but I'd just rather be up to date with it.  I thought about just wiping it and doing a clean install, and I may just end up doing that anyway for simplicity.

I did in face use Automatix...so that must be the problem.  I suppose I'll have to avoid using that in my FF installation, unless some conflict there has now been fixed.

Thanks for the help.

---

