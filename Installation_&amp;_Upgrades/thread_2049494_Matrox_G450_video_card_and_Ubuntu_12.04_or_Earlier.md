---
title: "Matrox G450 video card and Ubuntu 12.04 or Earlier Version?"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by WindsOfChange on 2012-08-28
Hi Members,

Its been a long day! In fact I've been at this for days trying to install Ubuntu 12.04 LTS with no success. I keep receiving an error message during install. The error message basically said, “The installer encountered an unrecoverable error". 

"I Think" I narrowed it down to my Matrox G450 video card that was purchased in 2001. It is a dual screen video card that works well on my system. I'm still running windows 2000 on this particular system. 

I just got off the phone with matrox and they told me that the Matrox G450 card will not work on any version of Ubuntu that is 11.0 or higher. The tech was kind enough to point the way to the linux driver download but said it was for older versions of Ubuntu. 

Does anyone have any thoughts on what "older" version of Ubuntu I should download thatt will work on my system that is running the matrox G450 graphics card? I don't need the dual screen function. I just would like to be able to successfully install Ubuntu. Or if its even worth the effort. I do not like going backwards in regards to installing an older version of Ubuntu but what are my choices please?

I found this link for older versions of Ubuntu.

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Thank you.

---

### Post by darkod on 2012-08-28
Depending where you live I would say it's much better investing in a more recent card, than using an older ubuntu. Besides, you don't have many options.

The only older still supported version is 10.04 LTS but that is supported for only one more year too. (EDIT: In fact, less than a year, only until April 2013).

Basically only you can answer if that's worth it or not. What about a cheap second hand card on Ebay or similar?

---

### Post by WindsOfChange on 2012-08-28
Hi darkod,

Yes your correct. Time to get a new/different video card. I'll go with your suggestion.

Thanks darkod

---

### Post by kostkon on 2012-08-28
The matrox people you spoke to were right. [Mesa has removed the drivers for legacy cards]("http://www.phoronix.com/scan.php?page=news_item&px=OTg0Mg"), .i.e.
> The drivers/hardware that no longer have mainline Mesa driver support are listed below.

i810: Early Intel 8xx series IGPs
Mach64: ATI Mach GPUs
MGA: Matrox GPUs
r128: ATI Rage 128 GPUs like the Rage Fury, XPERT 99, and XPERT 128
Savage: S3 Savage GPUs
SiS: Crusty SiS GPUs
Tdfx: 3dfx Voodoo graphics cards
Unichrome: VIA IGPs (Well, the ones where there was actually support available.)

So the driver is not available anymore in Ubuntu and thus you will not be able to have 3d (albeit a primitive one for 2012 standards), neither dual screen support.

Although, I don't believe your card is causing the problem in this case. Under normal circumstances Ubuntu should load fine in 2d mode, even with a Matrox using the generic vesa driver.

What are your system's specs? Did you check your live cd/usb on another system?

EDIT: Hmm, [12.04 still offers the driver]("http://packages.ubuntu.com/precise/xserver-xorg-video-mga"), so that's good. Again, the card is so old that Ubuntu will only work in 2d mode anyway.

---

