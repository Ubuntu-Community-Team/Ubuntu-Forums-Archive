---
title: "Trouble upgrading to Feisty"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by geovino on 2007-07-05
When trying to upgrade to 7.04 we get this message:

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3

How can we correct this?

We are able to get on the internet.

---

### Post by linuxwizard on 2007-07-05
It is recommended that you remove or disable any extra repository that may have been added besides the Ubuntu repositories. I don't use automatix but I believe you have to uninstall it also before upgrading.

Warning Regarding Alternative Installation Methods

Warning: EasyUbuntu and Automatix are third-party utilities for installing the most commonly requested applications in some Debian-based distributions. They are not supported or recommended by Ubuntu. While they work well for many users, they have also been known to corrupt systems and leave them in a state where they cannot be upgraded to a later Ubuntu release.

---

### Post by geovino on 2007-07-05
> **linuxwizard said:**
> It is recommended that you remove or disable any extra repository that may have been added besides the Ubuntu repositories. I don't use automatix but I believe you have to uninstall it also before upgrading.

Warning Regarding Alternative Installation Methods

Warning: EasyUbuntu and Automatix are third-party utilities for installing the most commonly requested applications in some Debian-based distributions. They are not supported or recommended by Ubuntu. While they work well for many users, they have also been known to corrupt systems and leave them in a state where they cannot be upgraded to a later Ubuntu release.

I have had good luck with Automatix. I mainly use it just to install the audio/visual files so I can play music and video and dvds. What is a better way with Feisty?

---

### Post by linuxwizard on 2007-07-05
Using these will get you all the codecs you need to play anything.

[https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-badformats](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-badformats)

[https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


Use the individual packages to install libdvdcss2 and w32codecs

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

