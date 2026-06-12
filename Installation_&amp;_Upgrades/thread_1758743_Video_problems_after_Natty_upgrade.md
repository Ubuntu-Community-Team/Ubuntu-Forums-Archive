---
title: "Video problems after Natty upgrade"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2011-05-15
On my desktop computer, I ran into some nasty problems after upgrading from Kubuntu 10.10 to Kubuntu 11.04.  Nasty enough that for a while I thought my motherboard had died, and then thought my hard drive might have died.  Here's the history.

I upgraded my installation (one of several Linuxes in different partitions on the same machine) from Maverick to Natty.  I worked with it for a bit and then didn't use that machine for a couple of weeks.  When I rebooted, I got the usual bios bootup messages and then a message on my monitor "Frequency Out Of Range".  No blinking of the disk light, no Grub choice of images to start.  Looked like a deathly sick motherboard to me.  

But on a hunch I tried booting up from a CD and discovered that I could do that.  Any attempt to boot from the hard drive failed immediately, but gparted was able to look at the hard drive, and everything seemed to be in order.

I finally managed to get access to the hard drive with SuperGrub and was able to boot one of the partitions (not the Natty one).   But attempts to boot the Natty partition still produced the "Frequency Out of Range" message.  However, I discovered that if I waited for a while, the system would actually start up -- but at a resolution of 1024x768, not the 1280x1024 that I normally use.  Once the system was started, I was able to use System Settings to get the proper resolution.  But once I rebooted, I was back to the "Frequency Out of Range" message and the lower resolution.

I think that the Nvidia settings have something to do with this problem, but I don't know how to correct it.   It definitely was brought about by the Natty upgrade. I'm using the onboard video on my motherboard, which is reported as a GeForce something-or-other (I can get more details if it matters).

---

