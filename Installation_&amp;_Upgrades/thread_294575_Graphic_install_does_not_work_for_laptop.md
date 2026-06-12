---
title: "Graphic install does not work for laptop"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by mjhacker on 2006-11-06
My laptop will not boot properly to the live CD - the screen is a bunch of gibberish with lines and such going through it.  I have a MSI 1029, with a Radeon X700 video card.  Is there any way I can get the install to work, or to install with a text-only installer?  Safe graphics mode does not work either.  Thanks in advance.

---

### Post by ReaderRat on 2006-11-06
Yes, use the Alternate CD for (K)(X)Ubuntu. It is all text, and installs with less memory. Do you have at least 192 --> 256 Megs RAM? If you don't there are other distros available for limited resources.

---

### Post by mjhacker on 2006-11-06
I have 1 GB of RAM...

Does anyone else have this proble m with their laptop?  Not being able to do a graphical install?

---

### Post by ReaderRat on 2006-11-06
> **mjhacker said:**
> I have 1 GB of RAM...

Does anyone else have this proble m with their laptop?  Not being able to do a graphical install?
Yes, I do. I am waiting for some new discs to try another laptop install. I believe we may need to do set up our video drivers during the install. I will try that, and then ,if it doesn't work, use the Alternate CD (text mode).

---

### Post by mjhacker on 2006-11-06
> **ReaderRat said:**
> Yes, I do. I am waiting for some new discs to try another laptop install. I believe we may need to do set up our video drivers during the install. I will try that, and then ,if it doesn't work, use the Alternate CD (text mode).

I would think that Ubuntu, having as good of hardware compatibility as it does, would not flip out with a laptop display... 6.06 worked okay through safe-graphics mode for me on the same laptop, but 6.10 just doesn't.  Well, if no one else has any ideas, I'll just download the alternate CD.

---

### Post by mpbb77 on 2006-11-06
Well, wellcome to the club. Yes,a fresh install from CD with X700 is a pain. Please read the posts, maybe you can be lucky, some people succeeded by changing the driver in xorg.conf to radeon and setting a 640x? resolution.

Otherwise you have to get a console screen by any way and install the usual fglrx driver and launch the graphic install. Even then I only succeeded with root privileges.

Good luck

---

### Post by Caz'ar Xiladys'varion on 2006-11-06
Yes...I have this same problem too...I installed with the alternate cd, but have the same problem after it's installed...so is the only way to fix it changing the driver in xorg.conf?

---

