---
title: "Ubuntu 17.04 alternate installation iso not found"
date: 2017-05-31
forum: Installation &amp; Upgrades
---

### Post by escrod on 2017-05-31
The Ubuntu installation guide mentions an alternate installation CD

I'have been able to find it for Lubuntu and a lot of references for older releases.

**Where can be find the Ubuntu 17.04 alternate installation iso?**


Reference:

[https://help.ubuntu.com/community/Installation#Alternate_Installation](https://help.ubuntu.com/community/Installation#Alternate_Installation)

Alternate Installation[INDENT]
You may not wish to use the standard LiveCD for one of the following reasons:

    Your computer does not meet the hardware requirements, or the required drivers are missing from the standard LiveCD. The LiveCD is designed to support most standard hardware, but this won't cover every possible configuration.

    Or, you may simply prefer to install a more customized version of Ubuntu different from the standard install depending on your taste. 

Ubuntu has you covered in this regard, and towards this end you can use an Alternate Installation CD. Refer to the Getting Ubuntu page for download locations. The Alternate CD allows more advanced installation options which are not available with the standard LiveCD.
[/INDENT]

---

### Post by howefield on 2017-05-31
releases.ubuntu.com should have them.

[16.04.2 release]("http://cdimage.ubuntu.com/lubuntu/releases/16.04.2/release/")
[17.04 release]("http://cdimage.ubuntu.com/lubuntu/releases/17.04/release/").

---

### Post by escrod on 2017-05-31
These are the lubuntu ISOs. I'm looking for Ubuntu ISOs (Unity)

---

### Post by howefield on 2017-05-31
Sorry, yes, I misread your post.

I don't believe that alternate installation iso images exist for Ubuntu these days, other than the above linked Lubuntu images.

There is a minimal iso image if you have a good internet connection or perhaps the server image.

[http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/)
[http://archive.ubuntu.com/ubuntu/dists/zesty/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/zesty/main/installer-amd64/current/images/netboot/)

---

### Post by escrod on 2017-05-31
So the only alternative for using a custom LVM setup is using the server installation CD?

---

### Post by oldfred on 2017-05-31
Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

12.04 was the last Ubuntu with an alternative installer.
They said they would include the LVM & RAID installers in the Desktop installer, but it took years before LVM is included in Desktop and RAID seems to be partially supported in desktop installer (server installer usually required).

So you should just be able to use the standard desktop for LVM installs. The LVM option on desktop menu erases entire drive, but you still can use Something Else.
Also applies to Ubuntu, but from Mint.
[https://community.linuxmint.com/tutorial/view/2061](https://community.linuxmint.com/tutorial/view/2061)

---

