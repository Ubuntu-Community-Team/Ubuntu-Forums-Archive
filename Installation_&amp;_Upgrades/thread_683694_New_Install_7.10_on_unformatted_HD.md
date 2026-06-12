---
title: "New Install 7.10 on unformatted HD"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by theRevMom on 2008-01-31
My HD died and I'm trying to install Ubuntu onto the new one.  I'm working from  Dell Optiplex MFF with 1 gig RAM.  

From my windows machine I downloaded 7.10 ISO and burned the CD.  When I put it in the DVD/CD drive and booted to it and chose INSTALL, the machine spent over 15 hours just making CD noise.  

So I quit and rebooted to a 7.04 CD I had ((a Canonical CD from a collection I use to "evangelize").  The same thing happens with this one.

So, this feels like a CD/DVD drive issue.  So here's my question:

Can I put this HD in an external drive case and start the install from another machine up to the point of installing drivers then switch over to the optiplex?  Or, should I start searching E-bay for another CD drive for the Optiplex?

Suggestions?

Oh one more detail, the only system I have to work from for the next week is another Linux box since my Windows box is 4 hours away in my place of employment.

---

### Post by MikeyXX on 2008-01-31
I'd go with a new CD, or snag a USB CD drive. You'll want to do this as pure as possible, especially if you are rather new to Linux.

You could try cleaning that CD drive. Also confirm that you can boot to those CD's using another machine (just incase your burner was bad).

---

### Post by dgray_from_dc on 2008-01-31
Here's the problem I see.  You can boot off of the CD and get to the menu for installing.  (I'm assuming this is the alt CD)  This means your CD drive IS working.  However, when the install tries to start, it hangs.  Check the CD for defects, it may be corrupt.

---

### Post by theRevMom on 2008-01-31
Thank you for your speedy replies.  

I checked the CD for errors on the other Ubuntu box.  It is not bad.  

Yes, I can indeed boot from the CD and get to the install screen.  However, it also takes for ever.

So, I'm on my way to the local electronics store to have them check the RAM.  If it's okay, I'll buy a CD writer (the other ubuntu box needs one) that I'm going to use in the Optiplex without actually installing it (that box takes a micro form CD like in a laptop) by using longer power cable and ribbon cable and sit it on the desk beside.  We'll see if that helps.

I'll be back if it continues to be bothersome.  who knows, maybe I have an excuse to replace the Optiplex!

Thanks!

---

### Post by dabl on 2008-01-31
If that brand new hard drive is not partitioned or formatted, I wonder if that could be a problem?  You might try burning a GParted Live CD and boot that, and then partition the new hard drive the way you want it, and then reboot with the Ubuntu Live CD.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

:)

---

### Post by theRevMom on 2008-02-01
Thank you for the gparted link.  I downloaded on another computer and it was most helpful in getting the HD formatted.  

The CD reader is bad.  The CD does boot from another machine.  I tried the CD-R/DVD reader that I bought for another machine, and the Dell could not recognize it. 

In the meantime, the other computer's HD was about to go, so I put the new HD into it, formatted it using Gparted and installed 7.10 without incident.  

So the Optiplex is still sitting without a HD and not to be used any time soon.

Again, thanks everyone for all your help.  This type of assistance is why I LOVE Ubuntu.

:)

---

