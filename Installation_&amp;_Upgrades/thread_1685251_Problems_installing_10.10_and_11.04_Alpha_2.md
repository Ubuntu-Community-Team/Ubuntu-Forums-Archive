---
title: "Problems installing 10.10 and 11.04 Alpha 2"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by jamiepgs on 2011-02-10
I wanted to give 11.04 a try so I burned a copy and rebooted, however, when it got to the part Plymouth would usually appear the screen went into sleep mode and stayed that way, after 15 minutes I gave up, thinking "hey, it's an Alpha, what do I expect?" And so I decided to burn a copy of 10.10 instead but lo and behold, the same issue.

I managed to install 11.04 by using the alternative installer but when I rebooted into Ubuntu the screen went into sleep mode and wouldn't budge. 

Now, I have installed 10.10 before, however that was before a motherboard and CPU upgrade, the GPU was the same, so perhaps it's an issue with them.  

10.10 and 11.04 are both the 64-bit versions. I have an old 10.04 CD which is 32-bit that boots fine, however there was a problem with the installer where it just quits when you select 'Install,' which it always had.

I then tried 10.10 32-bit, in case it was an issue with the 64-bit versions, but still no luck.

I've tried all images in a virtual machine and they run and install perfectly, so I'm guessing they're fine. 

EDIT: I've also tried a range of disc brands, speeds and types but still no difference. 

Potentially useful information:

AMD Athlon II 640 X4 3.0GHz
ASUS M4N75TD Motherboard
4GB DDR3 1333MHz RAM
Nvidia 9800GT
320GB HDD with Windows 7 64-bit
1 TB HDD with a 20GB partition for Ubuntu, including Swap, the rest is for data. 

If the worst comes to worst I'll download a new 10.04 and see if I can get that installed, but I'd rather use one of the more recent versions. 

Also, I don't want to use Wubi, I'd rather have a dedicated partition for it. 

Thanks

---

### Post by dino99 on 2011-02-10
as usual, try by:

removing "splash" on boot line
adding either (if needed): nomodeset, noacpi

---

### Post by coffeecat on 2011-02-10
> **jamiepgs said:**
> Nvidia 9800GT

There is major turbulence with the xserver at the moment in Natty which seems to be particularly affecting nvidia. Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1675614](http://ubuntuforums.org/showthread.php?t=1675614)

You'll see that in later posts people are downgrading the xserver just to keep Natty going. I'm still (relatively) OK with Natty on my machines with Intel and ATI graphics but an install on a machine with a nvidia 8400GS card is not a pretty sight.

I suggest giving it at least a week before trying to install Natty alpha on a machine with nvidia graphics and then make sure you download the latest daily.

I don't know why 10.10 is a problem for you though.

---

