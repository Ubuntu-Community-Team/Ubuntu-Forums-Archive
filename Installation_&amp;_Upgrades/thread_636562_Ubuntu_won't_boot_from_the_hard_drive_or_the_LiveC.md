---
title: "Ubuntu won't boot from the hard drive or the LiveCD"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by Hobo Joe on 2007-12-09
Ok, I had quit Linux for a while, due to some shortcomings that had bugged me. But now, I'm sick and tired of Windows and I want to come back to Linux.

But rather than try to use my old install and download a ton of updates, I decided to start with a clean slate. So I downloaded the disk and burned it, and I booted up. 

It got to the selection menu, and I picked the normal 'start or install Ubuntu' option. And then the screen goes black. However, with my graphics card, that is normal. It's always been that way, with multiple installs, for some reason the loading screen never showed up, but I never made much of an issue of it. So I waited, expecting a long boot time, as it was booting from a CD. Long story short, I waited 20 minutes and nothing happened. 

A little confused, I restarted and tried to boot from my old install. Same thing, black screen for 20 minutes. So I rebooted AGAIN in recovery mode. It loaded right up as it should in 30~ seconds. No errors or anything. So I tried a few things to make sure it wasn't my graphics card. 

Using 'startx' I was able to get the GUI perfectly, and set up the monitor I've gotten since the last time I've used Linux via the nVidia control panel. Then I logged out of the Xserver and ran 'sudo dpkg-reconfigure xserver-xorg' to see if my boot problems were caused by the drivers. I tried booting again: Same problem. Just a blank screen.

I'm not sure what's causing this, the most likely thing seems to be the graphics card/drivers, although I'm not sure, because I was able to get the GUI perfectly via recovery mode.

So I'm stumped. Any help would be greatly appreciated.

---

### Post by Hobo Joe on 2007-12-10
Nobody?

Also, I forgot to mention, my graphics card is a 8800GTS 640MB.

---

### Post by rsambuca on 2007-12-10
With the 8800 you should be using the new beta driver from nvidia.  The nvidia-glx-new driver from the repos doesn't really work with these newer cards.

[For the 32bit version]("http://www.nvidia.com/object/linux_display_ia32_169.04.html")

[For the 64bit version]("http://www.nvidia.com/object/linux_display_amd64_169.04.html")

---

### Post by Hobo Joe on 2007-12-10
> **rsambuca said:**
> With the 8800 you should be using the new beta driver from nvidia.  The nvidia-glx-new driver from the repos doesn't really work with these newer cards.

[For the 32bit version]("http://www.nvidia.com/object/linux_display_ia32_169.04.html")

[For the 64bit version]("http://www.nvidia.com/object/linux_display_amd64_169.04.html")

Alright, I'll give that a shot.

But that still wouldn't fix my problems with the LiveCD. Any idea's on that?

---

### Post by rsambuca on 2007-12-10
You need the alternate CD

---

