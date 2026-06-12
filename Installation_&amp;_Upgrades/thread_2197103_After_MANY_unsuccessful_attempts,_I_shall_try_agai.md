---
title: "After MANY unsuccessful attempts, I shall try again.."
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by DRatJr on 2014-01-02
So I would like to install and use Ubuntu, well try to at least. I have tried and failed many times. I am on a Samsung Series 7 Chronos Laptop (NP780Z5E) with UEFI installed. My main problems came from it not booting and then being stuck on my boot menu in Windows, forcing me to reinstall my BIOS.

So now.. I would like to just run it on a USB drive, as fully as possible. I'd like to start programming on Linux. So here are the questions:

1. What is the recommended size for a USB that I want to install Linux on?
2. Anyone know a thorough guide explaining this?
3. Addon for 2, what is the best distro of linux to install on a USB drive?
4. Will I be able to install and have it working (almost / as close as possible to) fully like a desktop version?
5. Will I be able to program on this USB version?

Thanks to all!

---

### Post by Bucky Ball on 2014-01-02
*Thread moved to **Installation & Upgrades**.*

1. Depends if you are keeping your personal data on there as well as the OS.

2. There are a heap online. [https://duckduckgo.com/?q=install+ubuntu+usb+persistence](https://duckduckgo.com/?q=install+ubuntu+usb+persistence).

3. Completely down to personal taste and what suits the way you work. Subjective.

4. Yes. You install it with persistence to the USB dongle just as you would to a hard drive. It will never be as fast running from USB, though.

5. Yes, but again, the USB install will be slower than hard drive. 

You might be better to post here about your issues with installing to the hard drive rather than going the USB route. You'll probably learn more about Ubuntu and programming by working with the community and trying to figure out what the problem is. I'm guessing it is to do with UEFI (particularly if Win was preinstalled).

---

### Post by DRatJr on 2014-01-02
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*

1. Depends if you are keeping your personal data on there as well as the OS.

2. There are a heap online. [https://duckduckgo.com/?q=install+ubuntu+usb+persistence](https://duckduckgo.com/?q=install+ubuntu+usb+persistence).

3. Completely down to personal taste and what suits the way you work. Subjective.

4. Yes. You install it with persistence to the USB dongle just as you would to a hard drive. It will never be as fast running from USB, though.

5. Yes, but again, the USB install will be slower than hard drive. 

You might be better to post here about your issues with installing to the hard drive rather than going the USB route. You'll probably learn more about Ubuntu and programming by working with the community and trying to figure out what the problem is. I'm guessing it is to do with UEFI (particularly if Win was preinstalled).

Yes the problem has to do with UEFI. The thing is, I've came here numerous times. I can never get sufficient help to get a successful install. And then, when I uninstall, I have so many more problems trying to get it fully off of my computer.

---

### Post by chkneater on 2014-01-02
I sounds like when you install the grub is not showing at startup like it should, then it times out and attempts to start windows...  using terminal do 'sudo Gparted', it should show you're installed Ubu and windows systems.  There is a section to the right side that says 'flags'.  Click on the ubuntu partition, (needs to be unmounted) and mark that flag as 'boot'.  

That should redirect the BIOS to start the Grub and allow you to choose between systems.  If windows is flagged as boot, it would probably jam it up.

---

### Post by sudodus on 2014-01-02
> **DRatJr said:**
> So I would like to install and use Ubuntu, well try to at least. I have tried and failed many times. I am on a Samsung Series 7 Chronos Laptop (NP780Z5E) with UEFI installed. My main problems came from it not booting and then being stuck on my boot menu in Windows, forcing me to reinstall my BIOS.

So now.. I would like to just run it on a USB drive, as fully as possible. I'd like to start programming on Linux. So here are the questions:

1. What is the recommended size for a USB that I want to install Linux on?
2. Anyone know a thorough guide explaining this?
3. Addon for 2, what is the best distro of linux to install on a USB drive?
4. Will I be able to install and have it working (almost / as close as possible to) fully like a desktop version?
5. Will I be able to program on this USB version?

Thanks to all!

First of all, I wish you good luck. Maybe we can help you get over some hurdles. We have a lot of patience, so if you don't give up, you will get a nice system in the end. I agree with the previous replies, I would only like to add a few points.

1. If a pendrive, Sandisk Extreme USB3 32GB. But you can also connect a HDD or SSD via USB 2 or USB 3 (USB 3 is much faster), and it will be faster than the pendrive, particularly reading and writing many small files. HDD and SSD will also last longer.

2. There are several guides here at the Ubuntu Forums and wiki pages, for example

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I would also suggest that you make a normal installation to the USB drive, not only a persistent live system. A normal installed system will be more stable and can be completely updated/upgraded, while a persistent live system can not upgrade the kernel. If you have eSATA, it is a good alternative, that gives you a fast connection to an external drive, about the same speed as USB 3.

3. I say the same as Bucky Ball, it depends ... But a slower connection than with an internal drive makes it interesting to have a system with a light foot-print, for example Lubuntu or Xubuntu rather than standard Ubuntu or Kubuntu.

4. Yes, almost (with USB 3 or eSATA)

5. Yes

Anyway, it might be worthwhile to try to install a dual boot system into the internal drive.

And whichever method you choose, make a ***complete backup of the current system before*** you start with the installation, because things can go wrong!

---

