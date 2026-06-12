---
title: "Linux proprietary ati driver 9.1 is out"
date: 2009-01-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hardhu on 2009-01-30
But it seems it has no support for xorg 1.6:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_91_linux.pdf]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_91_linux.pdf")
Has anybody tried it on jaunty?

---

### Post by rajeev1204 on 2009-01-30
I was under the impression ATI drivers are open source now.

---

### Post by inportb on 2009-01-30
> **rajeev1204 said:**
> I was under the impression ATI drivers are open source now.

There are a few opensource drivers for ATI/AMD graphics chipsets, including radeon, radeonhd, and avivo. AMD continues to provide the binary fglrx, which this thread is about.

---

### Post by Kazade on 2009-01-30
Does this version work on X Server 1.6? My Jaunty install is essentially useless at the moment without any hardware acceleration (not even 2D).

---

### Post by inportb on 2009-01-30
Ah. I hope you weren't expecting to make any use of your Jaunty setup.

---

### Post by Kazade on 2009-01-30
Well, I could deal with only 2D acceleration... I always switch my desktop at Alpha 3 when it is stable enough to use, but I can help with bug reports etc. The mistake I made was in the past I had an R300 based card which was well supported by the open source drivers... I recently upgraded :(

I've just been chatting in #radeonhd and I'm gonna give the r6xx-r7xx branch another go. I'm guessing 9.1 doesn't support the new X Server then.

---

