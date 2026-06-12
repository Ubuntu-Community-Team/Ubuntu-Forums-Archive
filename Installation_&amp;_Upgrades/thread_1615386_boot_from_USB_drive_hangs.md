---
title: "boot from USB drive hangs"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by rclocher3 on 2010-11-06
Hi all,

I would like to try Ubuntu 10.10 Netbook Edition on a Lenovo S10-3 netbook.  So I followed the directions on the website: I downloaded the ISO, downloaded the "Universal USB Installer" from pendrivelinux.com, and used the Universal Installer to format the USB drive and install the ISO onto it.

When I boot to the USB drive, a bunch of text flies by, and then it hangs, still in text mode.  Pressing Ctrl+C doesn't do anything, nor does Ctrl+Alt+Del; I have to hold the power button for five seconds to shut the computer off.  The last text on the screen says this:

[drm] Initialized drm 1.1.0 20060810

I checked the MD5 hash of the ISO, and it is correct.  I repeated the step of using the Universal Installer to format the USB drive and install the ISO onto it, and I booted to the USB drive again.  I got the same error.

Would someone please give me a hint on how to proceed?  I'm pretty stuck.

- Rob

---

### Post by sikander3786 on 2010-11-07
Hi and Welcome to the forums :popcorn:

> [drm] Initialized drm 1.1.0 20060810

Can't guess much from that error message. I think you need to try with some boot parameters like **nomodeset** and **acpi=off** etc.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

If that doesn't help, It would be the best practice here to try with some other USB creation tool like unetbootin or maybe some other thumb drive as well.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by rclocher3 on 2010-11-07
Thanks very much for taking the time to look at my problem!  I'm sorry to say that I tried every one of your suggestions, but I still can't boot from the USB drive.  To be specific, here are the things I tried:

1) I got into the Boot Options menu and pressed F6 for "Other Options".  I tried turning on each option, one at a time, and then rebooting.  One of the options got me slightly further along in the boot process before hanging, but the boot process still hung every time with text on the screen.

2) Next I reformatted the USB drive and used unetbootin to load the ISO file onto the USB drive, and booted again.  This time the boot process appeared to hang on the unetbootin boot menu.  I was a bit surprised there, because I had tried unetbootin with a different Linux distro before, and it worked with the other distro.

3) Finally I got my other USB drive (that formerly had the other Linux distro on it), reformatted it, and used the "Universal USB Installer" from pendrivelinux.com again to load the ISO onto the new USB drive.  When I rebooted I got the original problem again.

So I'm stuck even worse than before now.  I don't understand why Maverick Meerkat Netbook Remix won't work with my computer.  Does anybody have any more suggestions for me, or should I report this as a bug?

Here's a photo:
[IMG]http://www.idiompress.com/eBay/ubuntu_usb_boot_hang.jpg[/IMG]

---

### Post by rclocher3 on 2010-11-08
I did a Google search, and I found a link somewhere saying that my model of netbook worked fine with Ubuntu 10.04.  So I tried it: I downloaded the Lucid Lynx (10.04) Netbook Remix ISO, installed it on one of my USB drives, and booted it.  It works!

So there must be something wrong with Maverick Meerkat (10.10) Netbook Remix and my Lenovo S10-3.  Does anyone know where I should report this problem?  And if I want to install the latest version of Ubuntu on my netbook, how do I figure out which driver or module doesn't work so I can get around the problem?

---

### Post by sikander3786 on 2010-11-08
If you want to report it to the developers, report a bug at launchpad.

[https://launchpad.net](https://launchpad.net)

They will guide you in searching for the offensive/missing driver/module.

Happy Ubuntu-ing!

---

### Post by rclocher3 on 2010-11-08
Thanks again for your help.  This issue turns out to be a known kernel bug. [https://bugs.launchpad.net/linux/+bug/634702]("https://bugs.launchpad.net/linux/+bug/634702")

If anyone else has this problem with a Lenovo S10-3 IdeaPad, here's the work-around: quickly press any key when the blank screen with the small human figure is showing.  That takes you to the boot options menu.  From the screen that offers many languages, either pick a language or hit the Esc key if English is good enough.  Then press F6 for Other Options.  Press Esc again to dismiss the popup dialog.  There will be a new line at the bottom of the screen.  On my computer it says this:

Boot Options ed/ubuntu-netbook.seed boot=casper initrd=/casper/initrd.lz splash --

You will want to edit this line.  The cursor should already be at the end of the line.  Add "intel_idle.max_cstate=0" to the end of the line, without the quotation marks.  Then hit Enter, and the computer should boot properly this time.

---

### Post by watzing on 2010-11-08
Cheers for the solution. Same issue here.

---

