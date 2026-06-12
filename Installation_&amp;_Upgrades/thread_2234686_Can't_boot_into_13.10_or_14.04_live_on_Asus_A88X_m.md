---
title: "Can't boot into 13.10 or 14.04 live on Asus A88X motherboard! Total graphics fail!"
date: 2014-07-16
forum: Installation &amp; Upgrades
---

### Post by Steve_Kelly on 2014-07-16
Hi guys,

Let me just say I am a big fan of everything the Linux and Ubuntu community have done throughout the last few years but I've hit a bit of a wall after upgrading an old pc to relatively more modern hardware. I have tried every modern version of Ubuntu and almost every main distro of Linux but none of them and I mean none of them will boot into a graphical user interface thus allowing me to go ahead and install. All I get is the logo and then a few seconds later either a completely white, black or pixelated screen and then the disc stops spinning and the system hangs. I have searched through Google a tonne of times for an answer to this but the only thing I found was either the "--xforcevesa" fix (Tried this and it doesn't make any difference) or people claiming that I'd just have to install then install the proprietary graphics drivers once more. This is clearly not an option as I can't even boot into the interface and can't even connect to a network until this has completed.  I have tried the Mac AMD64 version too in case it was my UEFI Bios causing the issue and that just did the same thing. The only thing that has been successful was installing 12.04 32-bit but this is so outdated I really don't want to have to resort to it. Anyway I'd just like to know if there is any work around for this because at the moment I've been frustrated for a month with this and it's really beginning to make me lose faith in the whole open OS movement.

Here are my exact specs:

**Motherboard:** ASUS A88X
**CPU:** AMD Dual-core A6-5400K Black edition APU
**RAM:** Corsair 4GB DDR3 single channel

**Preferred version of ubuntu:** 14.04 64BIT

[B][I]Here are links to videos of the issue:
[/I][/B](Apologies for terrible focusing issues; I'm no cameraman. Also yellow line is caused by monitor which is currently borked at times! ;))

[https://www.youtube.com/watch?v=K5GFlZ7NbCM&index=2&list=UUUL7y-JaA6cnOhrNeRN2jCw](https://www.youtube.com/watch?v=K5GFlZ7NbCM&index=2&list=UUUL7y-JaA6cnOhrNeRN2jCw)

[https://www.youtube.com/watch?v=mAcewZss3Ls&list=UUUL7y-JaA6cnOhrNeRN2jCw&index=1](https://www.youtube.com/watch?v=mAcewZss3Ls&list=UUUL7y-JaA6cnOhrNeRN2jCw&index=1)


Your help will be very much appreciated,

Thank you! :D

---

### Post by kc1di on 2014-07-16
The problem is usually found in the Graphics card.  Do you know what the video card is?

My guess is that the modesetting feature of mordern linux kernels can not set you card.  You can try booting with nomodeset.
In ubuntu just as the live disc starts to boot hit the tab key, this should take you to a screen with a list F key options at the bottom of the page.
select F6 and from the list click on nomodeset  hit Esc and then enter see if it boots.

---

### Post by Steve_Kelly on 2014-07-16
Thank you so much kc1di,

I did exactly what you said and went ahead and it booted beautifully. I was a little concerned that when it rebooted the issue may remain but it booted up perfectly and I am now good to go with Linux again:

[http://s1375.photobucket.com/user/OCCY418/media/Screenshotfrom2014-07-16123032_zps884fa0be.png.html?sort=3&o=0](http://s1375.photobucket.com/user/OCCY418/media/Screenshotfrom2014-07-16123032_zps884fa0be.png.html?sort=3&o=0)


I was kind of expecting to wait a month at least for a response if any on here but your fast and concise reply has seriously restored my faith in the open source movement once more! I owe you a coffee dude for that.

Thank you so much. O:)

---

### Post by kc1di on 2014-07-16
Glad it's working , Enjoy ;)

---

