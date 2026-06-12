---
title: "Install Ubuntu the weird way"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by telovoyagarcar on 2007-03-06
I have a problem with a Laptop. The cdrom does not work, and i need to install Ubuntu no matter how. 

Im thinking of this:

Plug the laptop hard drive in an old desktop machine i have, install ubuntu in there, and then move the hard drive back to the laptop.
I tried to do this with windows but then i got the blue screen of death.
May be Ubuntu is going to start and reinstall the hardware?... 
is there any other way?.. any ideas? 
Im going to buy the cdrom for the laptop on ebay, but in the mid time i need to have something installed in the laptop at least to be able to have internet access...
Thanks a lot.

any ideas are very welcome

---

### Post by bernied on 2007-03-06
Can you boot to a usb device? (This would be a setting in BIOS.) There are ways of getting the ubuntu install cd to work from a usb flash memory stick.

Or, can you borrow a usb cd drive? (Would also need to be able to boot from usb device)

These two options sound easier to me than what you propose - how do the power and data connections look on a laptop?

---

### Post by mac.ryan on 2007-03-06
> **telovoyagarcar said:**
> any ideas are very welcome

I don't have first hand experience, but this page seems to have plenty of ideas on how to install ubuntu "the weird way" :)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by FuturePilot on 2007-03-06
There's a How To around here somewhere about how to install without a CD. It's basically mounting the .iso file.
[http://www.ubuntuforums.org/showthread.php?t=28948]("http://www.ubuntuforums.org/showthread.php?t=28948")

---

### Post by telovoyagarcar on 2007-03-07
Thank you for the replies.

I did install Ubuntu the way i asked first and works great.

This could be useful if you need to install Ubuntu in an older computer using a faster one to save some time.


Here is the receipt:

1. Remove the hard drive from the pentium3 Toshiba laptop.

2. Use an ide adapter and plug the HD in another faster computer.. in my case this was a 2ghz pentium 4 desktop.

3. Install Ubuntu 

4. Move back the HD to the laptop.

5. xserver is going to protest because now is using a different video card. So just reconfigure it.

6. Voila!


I dont know how the hardware detection and installation works in linux, but i see it is very friendly and flexible, because besides the xserver thing, i saw no other complaints at the time Ubuntu booted into a different machine. Everything works nice now.

So do you know how linux manages the hardware and drivers when you install it? I mean, is it only keeping some configuration for the video card and thats all? And every time it boots, reloads all the necessary stuff and drivers needed for THAT machine?
Seeing that there is a lot of Live CDs makes me think of that.

Who wants to educate some of us about this matter?

Thanks a lot guys. :)

---

### Post by bernied on 2007-03-07
> **telovoyagarcar said:**
> So do you know how linux manages the hardware and drivers when you install it? I mean, is it only keeping some configuration for the video card and thats all? And every time it boots, reloads all the necessary stuff and drivers needed for THAT machine?
Seeing that there is a lot of Live CDs makes me think of that.
I believe very vaguely that this is handled by udev, and maybe coldplug and hotplug. I think udev remembers your system, but looks for changes at startup. Drivers are generally kernel modules, which are loaded into the kernel when they are needed. 

Some people choose to build their own kernels, and some build-from-source distributions, like gentoo, insist that you build your own kernel. When you do this you have the choice of whether to build drivers into the kernel, or build them as modules.

To see what kernel modules are running, use lsmod - you might need sudo to get permissions.
```
sudo lsmod
```
To see what the kernel is doing at startup, use dmesg (maybe with sudo again). Other log files are at /var/log - messages or syslog is the main one.

Google everything else.

If you're interested in how linux works, you would enjoy gentoo.

---

