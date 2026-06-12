---
title: "Will not boot from Dvd or USB in 12.04"
date: 2012-08-03
forum: Installation &amp; Upgrades
---

### Post by Candlehawk on 2012-08-03
Quick back story on the issue: Before all this, I dual booted windows 7 and Arch Linux, but then with some of the recent changes made, and with Steam (eventually, but now definitely) coming to Linux, (specifically being supported for primarily Ubuntu as of now.) I decided to install Ubuntu. Naturally, the first thing I did was take my USB and put a nice, freshly installed iso of Ubuntu 12.04 on it (which has worked in the past on booting to BackTrack, same USB same computer) and try to install. The familiar purple screen flashed up for a second before being replaced with an empty shell (i.e. a black screen with only a blinking white underscore in the top left corner) I let it sit that way for a little bit. Not a thing happened. I then reboot, and burn myself the iso onto a dvd at  the slowest speed and pop it in the drive and attempt to boot. Same thing happened. Keep in mind, I kept doing what I needed to boot from the USB and DVD (i.e. hitting delete to get to the bios menu (have you ever heard of that? Delete as the bios menu key? I sure never have before, before I got this computer!) F8 to get to the menu and selecting my USB stick or DVD drive, depending of course on what I was booting). At any rate, I take out a dvd I had with Ubuntu 11.10 on it, booted like a charm and installed just as it should have. Now, the problem I have is that I don't want 11.10, I want 12.04. I have had this problem with Mint 13 as well on this system. I believe Debian still boots, fine, so this must be a change that was made on the Ubuntu and downstream side. On my other computer the disk boots fine, so this must be an issue with my hardware, which I shall now list: 
CPU: Intel core i7-2700K CPU @ 3.50GHz 3501 Mhz
Motherboard: Can't remember exact model, it's Asus though.

I will try to find more system information if necessary once I reboot into Ubuntu 11.10

---

### Post by 2F4U on 2012-08-03
You should provide more information about your hardware. Anyways, you can try to set some kernel options such as nomodeset which may or may not prevent the black screen. For more information see here:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Candlehawk on 2012-08-06
Thank you, choosing 'nomodeset' has appeared to have worked.

---

