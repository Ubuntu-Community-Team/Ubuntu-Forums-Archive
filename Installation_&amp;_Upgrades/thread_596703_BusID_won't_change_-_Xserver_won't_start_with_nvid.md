---
title: "BusID won't change - Xserver won't start with nvidia card on HP"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by dwise75 on 2007-10-29
Hopefully someone can help with this one.

Running 7.04 on an HP XT858

I was attempting to install an Nvidia video card. I used the reconfiguration tool (dpkg-reconfigure xserver-xorg) to enter all the settings for the card, a GeForce FX 5500. Problem is, I entered the wrong BusID. As you can guess, it didn't work. 

When I put the new card in and rebooted my computer (sfter checking BIOS to make sure PCI selected)  I got an error telling me, essentially, that my graphical interface can't start because no card was found on the bus I identified. So I used the tool to change it to the correct bus, rebooted, same error. I then tried it again and again, and attempted to use both the nv driver and the nvidia driver. Still the wrong BusID comes up in the error message, even though the busID is set correctly in the xorg.conf file. 

Oh, I also loaded some nvidi-glx-new or some similar file at some point.  

I believe I know how to do it now, but how can I get that BusID out of the system. Where is it hiding?

Sorry I cant post the error messages because it only happens when I have the new card in and only get command line access then. 

Thanks for any help!

---

