---
title: "Unable to boot + unable to save bios changes"
date: 2018-03-14
forum: Installation &amp; Upgrades
---

### Post by peter1985 on 2018-03-14
All,

last October 2017, I installed ubuntu 17.10 on my Lenovo yoga 300.
The installation was fine and working properly.
Two days later, I was unable to boot my laptop. The start screen kept popping up. I tried to boot from usb, but this was not possible.
Later, I found that there is an issue with ubuntu 17.10 on lenovo laptops and usb boot ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147))

Since my laptop was still under warranty, I send it back for repair.
Two months later, I got my laptop back, with the message that my hard drive had crashed and that they were unable to restore my pc because there is a password on my bios (which isn't).

After I got it back, I bought a new hd and installed Zorin OS on it using another laptop.
I did this using a bootable usb and then installing Zorin on the hd (connected through usb).
I was able to boot from this hd using my other laptop.

Then I installed this hd in my lenovo and tried to boot. No result however.
I'm completely stuck now.
I taught about booting from lan, but this option is not available in my boot menu.
Also, I'm still unable to save changes in the bios. So setting the bios to boot from lan, will not work.
I tried resetting the bios using the bios menu and by unplugging the cmos battery (and laptop battery).
However, the result remains the same. Unplugging the cmos battery had reset the time. So it seems the battery is still ok.

Summary:
My hard drive had crashed.
Because of this ubuntu 17.10 issue I cannot boot from usb.
I'm unable to boot my new HD.

Does anybody have any idea how I can get my lenovo working again?

Thanks

Peter

---

### Post by wyliecoyoteuk on 2018-03-14
Sounds like a faulty bios chip.
If you can't save changes and there is no password, then the BIOS NVRAM is faulty.

---

### Post by peter1985 on 2018-03-16
Wylie.. thanks for the tip.
It got me further in finding out what went wrong.
I found this article about how ubuntu 17.10 corrupts the bios [https://www.omgubuntu.co.uk/2017/12/ubuntu-corrupting-lenovo-laptop-bios](https://www.omgubuntu.co.uk/2017/12/ubuntu-corrupting-lenovo-laptop-bios)
I keep digging for a solution..

---

### Post by papiroflex on 2018-07-26
Hi, I have a lenovo yoga on lubuntu 18.4 and it runs ok. to boot from usb you must have legacy usb on and legacy first as boot order, and your usb drive as first boot.

---

