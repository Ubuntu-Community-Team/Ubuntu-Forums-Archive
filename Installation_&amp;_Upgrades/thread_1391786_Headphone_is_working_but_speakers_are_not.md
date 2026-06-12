---
title: "Headphone is working but speakers are not"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by chirag64 on 2010-01-27
Hello, I've Ubuntu 9.10 installed on my desktop dual boot with Windows 7..

_[This is my motherboard.]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2859")_

My motherboard has 6 slots for sound devices and I use a pair of speakers and my headphones together, so they all take up 3 slots, i.e. 1 for speaker, 1 for headphone output and 1 for headphone's mic...

I'm able to listen from my headphone as well as speakers at any given point of time on Windows 7, but recently when I installed Ubuntu, it only gives audio output to my headphones, and not my speakers...

Any ideas how I can fix this so that I can receive audio output on the speakers as well as headphones?

---

### Post by prodiman on 2010-01-29
Try this: Go to Ubuntu Software Center and search for GNOME Alsa Mixer. Try configuring the settings there to see if it would help.

---

### Post by chirag64 on 2010-02-03
Hey, I tried disconnecting my headphones so that only my speakers are connected and i even tried the software GNOME Alsa Mixer, but all of it didn't work...I'm guessing its still not able to detect my speakers since my motherboard has 6 similar ports....any idea how to configure Ubuntu to recognize what kind of device i'm connecting?!?

---

### Post by chirag64 on 2010-11-07
OK, there are specific ports on my motherboard for Speakers and Headphones and mic. I had not inserted the pins in the proper ports. Although this cud be configured easily in Windows 7, I was not able to do the same in Ubuntu.

I put the pins in the right place and now all my audio devices work fine on Ubuntu as well :)

---

