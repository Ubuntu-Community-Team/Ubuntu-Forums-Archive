---
title: "Full-disk encryption on netbook"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by Cadmus on 2011-01-29
I managed to get a cheap refurbed netbook recently (Samsung N150) and I'm wanting to put Ubuntu on it. As it's also likely to be used when travelling and have things like chat logs, photos, and other such things I'd like to do full disk encryption. Also I've been pointed towards 10.4 as apparently the 10.10 netbook desktop isn't to everyone's taste.

So I tried using unetbootin to make a bootable 10.4.1 i386 Alternate usb stick, which hit the problem of no cd drive. I found an item to add to the boot (cdrom-detect/try-usb=true) which got it a little further, but at a copying stage it threw an error saying it couldn't copy off the disc.

Finally I tried making a unetbootin of the mini iso (does mini even support full disk encryption?) but that seems to hang after selecting a mirror.

I feel like I'm missing an obvious solution to the problem here. Can anyone point me in the right direction?

EDIT: Well it seems I was just impatient on the mini ISO and after a few minutes it's gone onto time-zone, though of course this could get rather tiresome without a local mirror, especially given this may go through more than one iteration. So any advice on my situation is appreciated.

---

### Post by Cadmus on 2011-02-02
The trick was to pull the USB stick just before the partionner starts up.

---

