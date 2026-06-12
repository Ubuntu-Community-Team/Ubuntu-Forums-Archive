---
title: "Alpha 2 CD not working"
date: 2009-06-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Aries K on 2009-06-25
Hi, I want to install the 9.10 alpha 2 and after the loading screen it just goes to a blank screen while my computer hdd indicator light stays solid. At first I thought I had a corrupt CD but after 4 tries they all do the same thing. My 9.04 CD works just fine. Anyone else have this issue? I am itching to try 9.10, thanks in advance.

My computer is an Acer Aspire M1640.

---

### Post by Therion on 2009-06-25
Did you download via a Torrent, or http?  I'd suggest using a torrent if you didnt.  

Also, are you burning your install media sloooooooowly?  8x or 16x, and no faster, for this job.

---

### Post by Aries K on 2009-06-25
> **Therion said:**
> Did you download via a Torrent, or http?  I'd suggest using a torrent if you didnt.  

Also, are you burning your install media sloooooooowly?  8x or 16x, and no faster, for this job.

I downloaded via http. What torrent links do you recommend? I did burn my CD at 48x so that might be my problem. I'll try it at 8x. Thanks for the quick reply.

---

### Post by Therion on 2009-06-25
> **Aries K said:**
> I downloaded via http. What torrent links do you recommend? I did burn my CD at 48x so that might be my problem. I'll try it at 8x. Thanks for the quick reply.
Try the slow burn first.  We need accuracy here, not speed.  

If still no joy, ANY torrent link is better than an http download.
Torrents self-verify for file integrity AS they download, ensuring an accurate final download to burn from.

---

### Post by meeples on 2009-06-25
i tried to install it via usb pen drive yesterday, 

i could get to the live desktop but whenever i clicked anything i got a bunch of errors :(

so i guess its jaunty and then an upgrade for me :)

---

### Post by Aries K on 2009-06-25
Reporting back: I downloaded via torrent and burnt at 8x, still doing the same thing. :(

---

### Post by jerrylamos on 2009-06-25
Karmic Alpha2 boots to black screen on i845 graphics on IBM ThinkCentre A30.  

Same CD boots O.K. on i830 IBM ThinkCentre R31, Radeon Thinkpad T40, and Radeon Compaq Presario.  Of course there's lots of bugs, see the forum....

Will look up launchpad bug# tomorrow.  It's #385947

Jerry

---

### Post by Aries K on 2009-06-25
Well I appreciate the help everyone although I never got the CD working did get 9.10 by going the update-manager -d route since there's more than one way to skin a cat :D. The upgrade went successfully and so far so good. I DO think this a bug though since it worked on my other computer which is a Compaq Presario w/ a Celeron D.

---

### Post by cariboo on 2009-06-26
Did you try any of the boot options available by pressing F4 and F6?

---

### Post by Aries K on 2009-06-26
> **cariboo907 said:**
> Did you try any of the boot options available by pressing F4 and F6?

Yep, I even tried low graphics mode.

---

### Post by psyke83 on 2009-06-26
> **Aries K said:**
> Hi, I want to install the 9.10 alpha 2 and after the loading screen it just goes to a blank screen while my computer hdd indicator light stays solid. At first I thought I had a corrupt CD but after 4 tries they all do the same thing. My 9.04 CD works just fine. Anyone else have this issue? I am itching to try 9.10, thanks in advance.

My computer is an Acer Aspire M1640.

You could boot into Jaunty (if it's still installed), run the usb-creator and make a bootable USB disk from the karmic alpha 2 iso. That will at least rule out burning failures.

---

### Post by WishMaster on 2009-06-26
I have a similar problem...
Since Ubuntu 8.10, I have not been able to install from cd. Tried all kind of burners under Ubuntu, even in Windows, even tried burning on different computers, different (new) cd's: cd never worked fully.
My "solution" was to install Ubuntu on a USB stick (using Windows), boot from usb stick, and install from there to hard drive.

Now I have tried KK alpha 2 (xubuntu)  to USB, and it gives the 'loading bar' going back and forth, and the just a black screen.
Acer TravelMate 661 LCi
Pentium-M 1,4 Ghz
	  512 MB RAM (2 x 256)
	  Intel i855GM chipset 400 MHz FSB with integrated graphics

When I try the same usb stick on another computer, it just boots fine and I can use xubuntu.

My guess: it has something to do with the intel i855 graphics...

---

