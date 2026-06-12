---
title: "torrent seeding problem"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by florus on 2010-10-11
I have downloaded the 10.10 i386 iso using Transmission. I left the torrent with a ratio of only 0.65 as I had other commitments, and when I later tried to use my iso to seed the torrent, Transmission gave the error message "couldn't add corrupt torrent". The md5sum is correct, so what have I done wrong?:confused:

---

### Post by lovinglinux on 2010-10-11
Have you moved the ISO file using Nautilus?

Have you tried to re-check the torrent from Transmission torent options?

---

### Post by florus on 2010-10-11
> Have you moved the ISO file using Nautilus? No, it is in Downloads.

> Have you tried to re-check the torrent from Transmission torent options?
There is no torrent in Transmission, so I have no options available. I presume I am wrong in just trying to launch my file in Transmission. Do I need to relaunch the torrent from the Ubuntu site? and if so will the ISO download again which would defeat the purpose of the exercise?

---

### Post by lovinglinux on 2010-10-11
> **florus said:**
> There is no torrent in Transmission, so I have no options available. I presume I am wrong in just trying to launch my file in Transmission.

You can't do that. You need to load the torrent file in Transmission, not the downloaded ISO.

> **florus said:**
> Do I need to relaunch the torrent from the Ubuntu site?

Yes.

> **florus said:**
> and if so will the ISO download again which would defeat the purpose of the exercise?

No, Transmission will detect that the ISO file exists and will re-check it. Once re-checked, the torrent will be listed as 100% and the seeding will begin.

Next time don't delete the torrent file and don't move the downloaded ISO if you plan to seed it.

---

### Post by florus on 2010-10-11
Thanks, lovinglinux, it all makes sense now. I have not used torrents before, and have a great aptitude for trying to do things the wrong way.:(

---

### Post by lovinglinux on 2010-10-11
> **florus said:**
> Thanks, lovinglinux, it all makes sense now. I have not used torrents before, and have a great aptitude for trying to do things the wrong way.:(

See my tutorial [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). It explains how BitTorrent works, among other things.

---

