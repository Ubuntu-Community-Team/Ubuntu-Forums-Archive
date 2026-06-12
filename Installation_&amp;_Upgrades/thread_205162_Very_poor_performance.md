---
title: "Very poor performance"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by Jayke on 2006-06-28
I have been running Windows XP on this laptop for a while (1.6Ghz CelM, 256 MB RAM, ATI X200M) and figured I'd multiboot it with Ubuntu. Since version 5.10 of Ubuntu wouldn't boot at all (X-server error) I decided to go for Dapper. The deskop CP boots just fine, but once it's booted the performance is horrible. It takes about ten minutes to open Firefox, and I gave up after 30 minutes of loading the installation-app. While doing this, it appears to load a lot from the CD. Now, I'm pretty close to the minimum RAM amount since my video card borrows 64MB or so from the RAM, but surely I should still be able to use the system.

I'm open to suggestions :)

---

### Post by aysiu on 2006-06-28
Do you realize that XP is running from the hard drive, but the Ubuntu Desktop CD is running completely off the CD itself and your computer's RAM?

Yes, a full desktop will run a little slowly out of 256 MB of RAM. Install it and you'll see a much faster performance.

I would *not* use the Desktop CD for installation. I would use it to see how well it detects your hardware (but not for assessing speed, for the aforementioned reason).

To install it, use the Alternate install CD, which requires less RAM. The Desktop CD for installation is ideal for 512 MB of RAM and above.

---

### Post by Jayke on 2006-06-28
Of course I realize the difference, but at the same time, being completely unable to use it for installation purposes is not what I would call a reasonable difference. Still, I suppose it's possible that the RAM-Drive memory used leaves only marginal amounts to work with.

Your suggestion sounds interesting however. Would there be any difference between the resulting post-install systems, comparing the desktop CD and the alternate CD? If so, what differences?

---

### Post by aysiu on 2006-06-28
Well, I've used the Desktop CD on systems at work that are similar to yours--similar processor speed, Celeron, 256 MB of RAM, and I saw that it was deathly slow. I don't know that it took ten minutes to load up Firefox, but...

1. It took a long time, probably at least two minutes
2. Loading more than one application at a time virtually froze the live session

That said, you'll probably notice the installed version of Ubuntu is considerably faster. Even on my 766 MHz 128 MB RAM computer, Ubuntu works at a decent pace. Sure, it doesn't fly (except with Xubuntu), but it has reasonable response times for one or two applications at a time. With 256 MB of RAM and 512 MB swap partition, you should be good for speed.

The Desktop CD and Alternate CD install the same end-result Ubuntu but in different ways. The Alternate CD isn't as "friendly" (it's a text-mode graphical installer), but it's less resource intensive, too.

---

### Post by Jayke on 2006-06-28
I see, I'll go ahead and get an image of the Alternate disc then. Thank you for your help, it is appreciated :)

---

### Post by aysiu on 2006-06-28
[QUOTE=Jayke]I see, I'll go ahead and get an image of the Alternate disc then. Thank you for your help, it is appreciated :)[/QUOTE]
In the meantime, even though it runs slow as molasses, use the Desktop CD just to see how well your hardware is detected--internet, mouse, video card, sound, etc.

---

### Post by Jayke on 2006-06-28
I think I managed to check hardware compability for most of the devices that could cause problems already. The wireless was a bit problematic, but it seems to have been detected so I suspect I'll be able to solve that problem eventually.

---

### Post by aysiu on 2006-06-28
[QUOTE=Jayke]I think I managed to check hardware compability for most of the devices that could cause problems already. The wireless was a bit problematic, but it seems to have been detected so I suspect I'll be able to solve that problem eventually.[/QUOTE]
Great. Then I'd go ahead with the Alternate Install CD.

Here's a great guide to getting dual boot working with the text-mode graphical installer:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

