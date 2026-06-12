---
title: "Upgrading to 9.10 killed my Wifi!"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by Skyline969 on 2010-03-30
Ok, I installed Ubuntu 9.04 on my laptop, and all was fine, except the sound was very low. Oh well, I decided to upgrade to 9.10, and the sound issue was fixed... but now my Wifi is dead! I checked the drivers, and the restricted Broadcom driver is "installed but not being used." I have a Dell Inspiron 1525. What can I do to get my Wifi to work again? Perhaps a hardware rescan or something else that I have no idea how to do? I noticed that when I unplug my Ethernet cable, the icon on the top changes to a Wifi signal icon, but with no bars, but when I right click there is no option to enable Wifi. I hope that helps a little.

Sorry, total Ubuntu idiot here. I'm surprised I even installed Ubuntu with the setup I had to do (all manually setting partitions to dual-boot with Ubuntu all on my extended partition).

If anyone could shed some light on this, I'd appreciate it.

Thanks in advance!

---

### Post by Slim Odds on 2010-03-30
I'm curious why so many people seem to be updating to 9.10 with 10.04 so close to be released.

You might want to try 10.04 because I believe that there has been a lot of work done on the wireless.

---

### Post by Skyline969 on 2010-03-30
> **Slim Odds said:**
> I'm curious why so many people seem to be updating to 9.10 with 10.04 so close to be released.

You might want to try 10.04 because I believe that there has been a lot of work done on the wireless.

I'll be upgrading once it comes out completely. Something about an Ubuntu beta makes me kinda iffy about installing it, so once it's completely ready for release I'll upgrade.

However, do you have any idea why my wireless wouldn't be working now?

---

### Post by Slim Odds on 2010-03-30
> **Skyline969 said:**
> I'll be upgrading once it comes out completely. Something about an Ubuntu beta makes me kinda iffy about installing it, so once it's completely ready for release I'll upgrade.

However, do you have any idea why my wireless wouldn't be working now?

Sorry, no. When I bought a laptop recently I made sure that it had an Intel 5100 chipset. Those work great.

But, then again, I'm also using 10.04.

The beta is actually pretty darn good. The only issue is the numerous daily updates at this point.

Did you do some forums searches? That is a pretty common problem.

---

### Post by coffeecat on 2010-04-01
> **Skyline969 said:**
> I checked the drivers, and the restricted Broadcom driver is "installed but not being used."

I've no direct experience of broadcom, but I know they can be a pain because of the Broadcom licensing issues. Just a guess, but I should imagine the driver didn't get automatically updated because of said licensing issues, and the Jaunty version of the driver doesn't work with the Karmic kernel. That's a supposition - not necessarily a fact. :)

Anyway... try reinstalling the STA driver (bcmwl-kernel-source) or the b43-fwcutter package, whichever you installed in Jaunty. Useful link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Skyline969 on 2010-04-01
> **coffeecat said:**
> I've no direct experience of broadcom, but I know they can be a pain because of the Broadcom licensing issues. Just a guess, but I should imagine the driver didn't get automatically updated because of said licensing issues, and the Jaunty version of the driver doesn't work with the Karmic kernel. That's a supposition - not necessarily a fact. :)

Anyway... try reinstalling the STA driver (bcmwl-kernel-source) or the b43-fwcutter package, whichever you installed in Jaunty. Useful link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Alright, get this. I turned off my laptop for the night, and the next day when I turned it on my wifi worked. Just magically. I don't even think I did any updates (don't remember). Ah, gotta love Ubuntu for that. :P

---

### Post by coffeecat on 2010-04-01
> **Skyline969 said:**
>  Just magically. 

That's Linux for you. :wink: It's the other way around in Windows. You turn off your laptop for the night and next morning when you boot up something is **not** working. Just magically. :lol:

---

### Post by Skyline969 on 2010-04-01
> **coffeecat said:**
> That's Linux for you. :wink: It's the other way around in Windows. You turn off your laptop for the night and next morning when you boot up something is **not** working. Just magically. :lol:

Still haven't turned on my laptop again today. It might have been a fluke in Ubuntu, and now nothing will work. ;)
I'll find out as soon as class is over, I guess.

---

