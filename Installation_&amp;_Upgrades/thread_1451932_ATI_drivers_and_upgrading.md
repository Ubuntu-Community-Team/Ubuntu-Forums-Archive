---
title: "ATI drivers and upgrading"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by a__l__a__n on 2010-04-11
I have an HP nc8430 laptop with ATI X1600 graphics.  I've been running ubuntu 9.04 with downgraded X packages (locked) so I could run the ATI propietary drivers.  Yesterday I upgraded to 9.10 in preparation upgrading again to the 10.04 release.  Now every time I boot I get a message that I'm running in low graphics mode.  When I try to open the System-Preferences-Display tool, it tells me that the video drivers don't support it.  

I knew I would be losing the proprietary ATI drivers by upgrading.  How do I get from this state to the default video drivers?

I've tried unlocking the locked packages and re-installing the xorg packages from Synaptic Package Manager, to no avail...

---

### Post by a__l__a__n on 2010-04-15
I don't know exactly what I did to fix this... But I tried several permutations of editing xorg.conf (including trying several of the other versions of the file in the /etc/X11 directory).   No dice. Then I followed these instructions:

[http://ubuntuforums.org/showpost.php?p=8201026&postcount=23](http://ubuntuforums.org/showpost.php?p=8201026&postcount=23)

which did not fix the problem.  

I unlocked all the locked packages in synaptic package manager, and repeated the above process.  Still no luck.  In fact now I had no video at all, even in single user mode.  

And then I booted with a live cd, mounted my ubuntu drive, and deleted

    /mnt/<mountpoint>/etc/X11/xorg.conf 

and rebooted... and it worked!   Maybe that will help someone else.

---

### Post by Mark Phelps on 2010-04-15
I'm glad it worked ... but my guess is that NOW, you're running the open source drivers. Which is why you're seeing a desktop again.

You might take a look to see if that is the case.

---

