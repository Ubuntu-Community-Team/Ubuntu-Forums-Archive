---
title: "error setting up gfxboot"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by roe46 on 2011-03-31
Hi
everybody is going for ubuntu, so I decided to give it a try. I downloaded ubuntu for desktop and created an usb-stick. I am using an old hp eVectra PC as an "guinea-pig". I configured its bios to use usb as first boot device. It did not boot from there, but went straight on to the debian on the HD.
Ok, let's go for a CD. I burnt the image and tried again. It recognized the CD, but it reported:```
graphics initialisation failed
Error setting up gfxboot
boot:
```
and repeated this endlessly. Any ideas around what I should try next? 
Thanks and regards roe46

---

### Post by franic_watts on 2011-04-08
I am having the same problem.  I have a Toshiba Netbook (NB305) purchased from best buy.  It currently has Windows 7.

I used the "netbook 10.10" iso.  
In setting up the USB I chose the "netbook 10.10 remix"

+++++

graphics initialization failed
Error setting up gfxboot
boot:

+++++

sound familiar?  I was able to use the regular 10.10 to get to a drive on my crashed desktop.  because I like that experience, I wanted to first try it on something smaller.

my thought is maybe I should have chosen the regular "10.10" rather than the "netbook 10.10 remix?"

I don't know.

---

### Post by MAFoElffen on 2011-04-08
> **roe46 said:**
> Hi
everybody is going for ubuntu, so I decided to give it a try. I downloaded ubuntu for desktop and created an usb-stick. I am using an old hp eVectra PC as an "guinea-pig". I configured its bios to use usb as first boot device. It did not boot from there, but went straight on to the debian on the HD.
Ok, let's go for a CD. I burnt the image and tried again. It recognized the CD, but it reported:```
graphics initialisation failed
Error setting up gfxboot
boot:
```and repeated this endlessly. Any ideas around what I should try next? 
Thanks and regards roe46
If at the LveCD boot menu where it asks you if you want to try or install... there is an options tab on the lower right of the screen that will let you boot from different graphics options...  If use this on puters where the graohics doesn't nativley comeup w/ the LiveCD.  

On some I come up un TTY Text console (appending "text" to the end of the kernel boot line) to use "hwinfo --framebuffers" to see what modes the graphics card supports -OR- boot up in GRUB2 and use "vbeinfo" at the Grub2 command line to find graphics modes.

One small change that seems to work is to dynamically edit (e) the grub menu entry-- "GRUB_GFXMODE=640x480" or the any mode you are sure that box supports. The boot (cntrl-x)

Or if you are just "trying" and seeing... Ubuntu Natty 11.04beta1 seems to have gfxmode's worked out a little better on it's LiveCD's from what I see so far.

Hope this was some help.

---

### Post by roe46 on 2011-04-13
Thank you MAFoElffen. Meanwhile I have experimented with the ubuntu 10.10 alternative ISO. I managed to overcome the gfxboot error, but the installation always failed in that sequence where it should download and install many files. It did install a lot, but obviously not all, but simply reported a failure of the installation - without giving any details. I then decided to go back to debian, downloaded the most recent debian 6.0 ISO and with this CD, the installation worked smoothly. What's wrong with ubuntu?

---

