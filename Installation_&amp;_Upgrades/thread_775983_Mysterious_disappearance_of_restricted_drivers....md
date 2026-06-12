---
title: "Mysterious disappearance of restricted drivers..."
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by FokkerCharlie on 2008-04-30
Hello!

A few days ago I started with a fresh install of Hardy (along with a new HDD in my laptop).  It has not been a trouble-free process, but we're getting there gradually.

On installation, the restricted drivers manager correctly installed the ATI driver for my graphics card.  Today I fitted a new wifi PCMCIA card, and the restricted drivers manager also came up with the goods there, with the Atheros software.

I then had a go at getting compiz working, and it was looking good.  I installed a few other apps (exaile, BMP, compiz-switch), and ended up restarting.

On the next boot, I found that the display was not working correctly ( mouse pointer was there, grey desktop and diffrent-shade-of-grey panels, no icons or text), but happily was able to rectify this using compiz-switch.

I also see that the list of proprietary drivers is now empty- so my display isn't working as well as it could, and my wireless card is not doing anything!

So, where to go from here?  Is it a matter of re-scanning the hardware to re-install drivers?  If so, how?

Thanks in advance for your help!
Charlie

---

### Post by FokkerCharlie on 2008-04-30
Another thing- there's something very badly wrong with the sound somewhere.

I only get a 'beep' when evolution notifies me of an arriving email, and Exaile and BMP are crashing when they try to play a tune.

This is most odd!

Cheers
Charlie

---

### Post by Thingymebob on 2008-04-30
Just upgraded to Hardy - No restricted drivers!!! so my ATI Based card is running like a dog and my wireless isn't working. Both processor cores are MAXed all the time (probably because of the video issue) and are now running hot. I've had to disable all desktop effects just to get a window to close in less than 5 minutes and my hard disk is doing some serious thrashing. 

Ouch - Need to get all this working again. Was running sweet under gutsy and have dist upgraded all the way from dapper without problems until now.

---

### Post by FokkerCharlie on 2008-04-30
OK- I think that I've solved this.

Go into synaptic, and search for 'restricted', and have a look through the list for the package(s) that relate to what you need.  Install them, have a look at the restricted drivers manager, and you'll probably need to restart, too.

Good luck.
Charlie

---

### Post by Thingymebob on 2008-04-30
Really very simple
```
sudo apt-get install linux-restricted-modules-generic
```
and they all magically re-appear in System->Administration->Hardware Drivers
Now its all working a treat!

---

