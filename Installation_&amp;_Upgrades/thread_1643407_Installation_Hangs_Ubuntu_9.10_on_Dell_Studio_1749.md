---
title: "Installation Hangs Ubuntu 9.10 on Dell Studio 1749"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by Theotherguy1 on 2010-12-11
Hello,

I've been attempting to install 32-bit Ubuntu 9.10 on my Dell Studio 1749 with the intention of making a dual-boot system. Attempting to install with a live CD using the default settings, I got as far as pressing ENTER on "Install Ubuntu" before the screen went completely black. The CD drive spun wildly, but nothing ever appeared on the screen. I tried the fix detailed here:

[http://bennybeta.blogspot.com/2009/12/ubuntu-910-on-dell-studio-1555.html](http://bennybeta.blogspot.com/2009/12/ubuntu-910-on-dell-studio-1555.html)

typing "nomodeset" as an option, and using the "apic=off" option. When I did this, I was no longer greeted with a blank black screen, but instead with a blinking cursor, but the installation still hung. The keyboard was unresponsive and I could not open a terminal. I also tried using the alternate installer instead, and got the same results.

After this, I tried installing using wubi, and on boot I get exactly the same results: black screen without "nomodeset" and a blinking cursor otherwise.

I should also mention that the same thing happens for every option on the installation screen, including the option to "try ubuntu" by booting from the CD.

Does anyone know what could be causing this issue, and how I might install ubuntu on my machine?

Thanks.

---

### Post by sikander3786 on 2010-12-12
Welcome to the forums :-)

First of all, if there is no specific reason behing using 9.10, I would suggest to download a newer version of Ubuntu i.e, 10.04 or 10.10 as support for 9.10 is scheduled to end in April 2011 and you'll need to either upgrade to the newer version or do a clean install then.

If you decide to go that way, download a newer version from ubuntu.com and run MD5SUM to make sure the image is not corrupt (that will definitely save you troubles later).

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, you can either burn it to a disc or a USB drive.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

If you decide to install 9.10 anyways,

> typing "nomodeset" as an option, and using the "apic=off" option. 

Try pressing F6 and putting in the boot parameters as mentioned here. I think there is no parameter like apic=off, it is either acpi=off or noapic. (Might be that works with apic=off also, not sure)

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

