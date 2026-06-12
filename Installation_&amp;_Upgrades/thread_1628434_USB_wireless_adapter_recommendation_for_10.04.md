---
title: "USB wireless adapter recommendation for 10.04"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by hodad on 2010-11-22
Has anyone installed a wireless USB adapter right out of the box with 10.04?   I've just spent 5 days trying to get a D-Link  DWA-125 to work, and I ^&(*&%^&(*& )(* 

Thanks!   (and don't buy a DWA-125!)

---

### Post by cybergnome on 2010-11-22
There's a recent thread here where I posted a link for using ndiswrapper with a Sitecom USB wireless adapter.  You might be able to follow the scheme there, but development for USB wireless devices is lagging.  :confused:

---

### Post by hodad on 2010-11-22
Thanks for the reply, but I'd rather get something that I can just plug in - and -Voila, it WORKS!    (Oh well, it's nice to dream, isn't it?).   I LOVE Ubuntu, but every time I get ANY new hardware, I don't care what it is,  I go thru several days of beating my head against the wall to get it to work.  

Has anyone thought of building a hardware installation decision tree as a general guide for installing new devices?  I typically go thru hundreds of pages of suggestions. God bless em, the volunteers do a great job and are very helpful, but it's maddening trying to get anything to work.  I'd love to contribute to such a guide myself, but am not good enough with pc's.  

Oh well, didn't mean to rant, but I've just been thru 5 days trying to get a simple usb wireless device to work... (I still love Ubuntu, however!)

Still looking for that magical wireless adapter that works out of the box, if anyone has any suggestions.

Thanks

---

### Post by Cpierce on 2010-11-22
I feel your pain. I went thru this same journey, but hopefully can point you in the right direction. The first "plug in and play" USB adapter that worked was a linksys WUSB54g ver4.0. It had to be version 4.0 However, the connection speed seemed inconsistent and only worked on G band. 

The two newer "N" adapters are the Netgear WNA1000 and Belkin F5D8053 ver 1.0. Again, the Belkin has to be ver 1.0. Both of these worked right away as soon as I plugged them in. I found the WNA1000 refurbished by Netgear on ebay for $15. Look here:

[http://cgi.ebay.com/NETGEAR-Wireless-N-150-USB-Adapter-WNA1000-802-11n-WiFi-/110576097563?pt=LH_DefaultDomain_0&hash=item19bed9591b#ht_1980wt_907](http://cgi.ebay.com/NETGEAR-Wireless-N-150-USB-Adapter-WNA1000-802-11n-WiFi-/110576097563?pt=LH_DefaultDomain_0&hash=item19bed9591b#ht_1980wt_907)


Hope it works for you !

MODS, hopefully it is okay to post the ebay link, if not, please remove the link. Someone can just type WNA1000 in a ebay search.

---

### Post by wightghost on 2010-11-22
Hi there,

I use an ASUS WL-167g wireless adapter that worked perfectly "out of the box" for me on 10.04 (even worked the same in 9.04).  I'm using it with 10.10 and no dramas either.  Note that it's a "G" adapter not an "N".  Got it on ebay.

Hope this helps

---

### Post by jives11 on 2010-11-23
I'm in the same boat. A friend gave up on windows on her old Packard Bell Easynote R1004. I suggested she try Ubuntu and 10.10 installs fine, but I cannot get the ath5k internal wifi to work. Tried most methods. Was wondering if using an external wifi usb device would work. Ideally a samll one like the LM Technologies. The ones identified here are all full usb memory stick size, which is a bit obtrusive if it becomes permanent

---

### Post by hodad on 2010-11-23
Thanks for the recommendations!

I agree that the ones that hang off of the back are cumbersome.  THat was one thing I liked about the D-Link DWA-125; it had a cradle that allowed the unit to sit on top of the pc; but if it doesn't work, that feature becomes less attractive(!).

If we end up getting the DWA-125 to work, I'll post a link as to what we did.

---

### Post by jives11 on 2010-11-25
Well looks like I don't need an external adaptor after all. I have been trying to get wireless working on a Packard Bell R1004 Easynote. It uses the ath5k driver but I couldn't get it to work.

This long thread culminates in a solution which immediately worked for me. I had to set these grub boot options:


acpi=force irqpoll noapictimer

[http://www.linuxforums.org/forum/wireless-internet/159283-atheros-ar5001x-8.html](http://www.linuxforums.org/forum/wireless-internet/159283-atheros-ar5001x-8.html)

Respect to sanne for swooping in at the end with the silver bullet, but also to waterhead for a very long debug thread with the OP.

Sorry - slightly off topic, but it might help people who , like me, were considering external  if they couldn't get internal to work.

---

### Post by hodad on 2010-11-28
I decided to try the Netgear WNA1000.  I will report on how it went, and what I had to go thru to make it work, once I get the item.

---

### Post by ibod on 2011-01-25
> **wightghost said:**
> Hi there,

I use an ASUS WL-167g wireless adapter that worked perfectly "out of the box" for me on 10.04 (even worked the same in 9.04).  I'm using it with 10.10 and no dramas either.  Note that it's a "G" adapter not an "N".  Got it on ebay.

Hope this helps


Hi 
I have a friend with a Packard bell easynote r1004 and the same wifi problem 

He is running 9.10 

I tried the boot options but they messed up the mouse and usb, despite using the last suggestion that was supposed to correct those problems.

I don't know what version of ubuntu this fix was for, so maybe not for 9.10 ?

If you still have the ASUS WL-167g can you tell me what version it is so I can get the right one 

Thanks

---

