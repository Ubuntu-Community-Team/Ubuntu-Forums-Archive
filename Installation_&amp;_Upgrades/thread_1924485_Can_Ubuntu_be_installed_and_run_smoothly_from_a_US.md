---
title: "Can Ubuntu be installed and run smoothly from a USB 2.0 External Drive"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by Rakib Ansary Saikot on 2012-02-12
I need to get a Portable Hard Drive, and I can't decided between a USB 2.0 portable hard drive and a USB 3.0 portable hard drive, since the latter would cost me a quite a lot of extra money, as my motherboard doesn't have any usb 3.0 port, and usb 3.0 adapters (?) are quite expensive!

---

### Post by mastablasta on 2012-02-13
well i have a an internal disk that is well over 10 years old and still working fine.... my point is if you plan to make a PC change later on go with 3.0, if you plant to stick for a while with this maschine then go with 2.0. 2.0 can be used later for data anyway.
 
i think it works fast enough. if the external disk has good read and write speed and nice cache it owuld work even better.

---

### Post by efflandt on 2012-02-13
USB 2.0 hard drives are usually significantly faster than USB flash memory sticks. I often test new Linux versions from USB hd before installing to my internal drive, which turned out to be wise when KMS (kernel mode setting) was first made the default and my video would not work with that, It turned out to be a simple **nomodeset** boot parameter, but I did not know that at the time.

As it turned out, when I eventually tested the internal 5400 rpm drive in my 2006 laptop, it was actually no faster than the USB WD Passport.  And the internal drive of my old 2004 desktop was only about 50% faster.  Depending upon how much RAM you have, once things load from disk, they reload from memory cache much faster.  So at the time, I never noticed any big speed penalty running from USB 2.0 hard drive.

I don't know enough about USB 3.0 whether BIOS of a computer without it would even know to boot from it.  Maybe someone else knows if systems can typically boot from a USB 3.0 add-on card.

---

