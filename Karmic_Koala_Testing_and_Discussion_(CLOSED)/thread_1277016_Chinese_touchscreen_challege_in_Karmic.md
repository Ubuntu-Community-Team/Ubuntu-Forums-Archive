---
title: "Chinese touchscreen challege in Karmic"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Halverneus on 2009-09-27
My wife just bought a netbook from China and we put Ubuntu on it. Everything works out of the box except the touchscreen (which I verified working in the WindowsXP install that came with it.) I have tried the ev drivers and several other methods published in the net with no success. I receive no response at all from touching the touchscreen. I have performed a sudo cat xxx to everything in the /dev/ directory without any response while touching the screen. The Windows driver is called nuvotonhidtouch.inf, which doesn't seem to exist anywhere on the internet. I have attached the output from lshal (lsusb only comes up with my webcam and card reader, so I didn't see the point of attaching that). I have submitted the lshal to the ev folks, but looking at the file, I cannot find anything that shows Ubuntu recognizes (or even identified) the touchscreen. Thanks for any help!

---

