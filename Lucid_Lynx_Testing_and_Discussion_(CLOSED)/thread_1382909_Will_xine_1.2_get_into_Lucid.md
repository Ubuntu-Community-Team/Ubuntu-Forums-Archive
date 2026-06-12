---
title: "Will xine 1.2 get into Lucid?"
date: 2010-01-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-01-16
There's been an announcement on the Nvidia Linux forum that xine 1.2 gets VDPAU support and an RC should soon be available.
Does anyone know what are the odds for it to make it into Lucid?

> 
Hi all,

VDPAU support has now been merged in xine-lib 1.2 branch.
We hope to provide a 1.2rc1 soon.

P.S.
1) VDPAU is not, and will not be, part of 1.1 because it's not ABI compatible.
2) In order for a frontend to work with 1.2, it only has to be recompiled against it.
3) vdpau_h264 has been reworked and is now more spec compliant, and also better handles streams that are not. In short, it should now work as good as ffmpeg.

[http://www.nvnews.net/vbulletin/showthread.php?t=124791&page=10](http://www.nvnews.net/vbulletin/showthread.php?t=124791&page=10)

---

### Post by mc4man on 2010-01-16
> Does anyone know what are the odds for it to make it into Lucid?
slim to none, leaning towards none, though I guess it's always possible
You could file a wishlist bug and see what response you get.

(during the course of [re-enabling aac decoding]("https://bugs.launchpad.net/baltix/+bug/496010") thru xine-libs (libxine1-ffmppeg), I made mention of moving to the 1.17 version which even that small move was not acknowledged so to speak

---

### Post by kahumba on 2010-01-16
I see, well, at least it will make it into Ubuntu 10.10 !

---

