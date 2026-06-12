---
title: "Booting Ubuntu from a USB (and keeping your data past a restart)"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by russellchamp on 2008-02-08
Hey y'all!  I recently (earlier today) got a Ubuntu live USB to work (yai!) using a nifty guide someone actually wrote of Knoppix (through the process of using this program in Win to prep the USB drive, copying the live CD to the USB and then moving the isolinux files to the top partition and changing some other file).  It works fine and all (I'm actually using it right now to post this) but I have one li'l issue.

Is there any possible way that I can mount the usb as read/write and add programs that I install to the USB instead of just loading it into RAM?  I ask because I'd really like these things to stick around past each reboot... :-(

If I could get this to work it'd be so totally AMAZING!  I know this *should* be able to be done (we're talking about **LINUX**, after all!) but I'm not sure how'd I'd go around it.  Any help, congratulations, or comments would be appreciated! :-P

---

### Post by clinton137 on 2008-02-08
Hi,

I have ubuntu running read write on a 4 gb USB stick, take a look at pendrivelinux.com, follow the instructions.

good luck

clint

---

### Post by russellchamp on 2008-02-08
Sweet!  I assume you're talking about this guide.
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
I'll try it out later today and see if it works.

---

### Post by russellchamp on 2008-02-08
Sweet!  I followed all of those steps and got it working!  The only difference I had was the fact that I already had Ubuntu installed on my computer so I just extracted the iso into a folder instead of burning it to a CD and got the files out directly.  Cool times!
The only... disapointment I have now is the fact that I can't get compiz to work due to the fact that I have a nVidia card and need to enable the restricted drivers which requires a reboot.  The only problem is that when I boot again the restricted drivers are NOT enabled.  Anybody know anything on this? :-P

---

