---
title: "Xbuntu install - cmd prompt only"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by Zerksis on 2006-10-05
I have downloaded Xbuntu alternate-iso.  MD5 check OK.
Have tried to install on 2 mch's one with Nvidia one with ATI 
graphics cards.  Both of these mch's run Ubuntu 6.06-1 fine.

Neither run Xbuntu.  It will install (oem used) and on 
restarting opens at a cmd prompt login.  Can log-in OK.

Tried to reconfig Xserver - (tseliot thread "Dealing with...")
am told gdm is not installed - if I apt-get it the Xserver then
cannot find fonts ... 

So, which Xbuntu iso might install like Ubuntu 6.06-1
because the 6.06.1 LTS "Dapper Drake" final release of Xubuntu 
does not.

Any suggestions ? 

Z

Forgot to mention - full clean install in every case.

---

### Post by K.Mandla on 2006-10-05
Download the ISO that matches your hardware here: [http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/)

Check the md5sum, then burn the CD and start you computer with the CD in the drive.

If you want, you can check the integrity of the CD.

Then choose "Install in text mode" ... don't use OEM mode.

That should do the trick.

---

### Post by Zerksis on 2006-10-06
Thanks for the reply KM, appreciated.

1.) Download the ISO that matches your hardware here: [http://cdimage.ubuntu.com/xubuntu/re...6.1/release.1/](http://cdimage.ubuntu.com/xubuntu/re...6.1/release.1/)
That's where the iso I used came from - matches HW.

2.) Check the md5sum, then burn the CD and start you computer with the CD in the drive.
3.) If you want, you can check the integrity of the CD.
Did both 2 & 3 before the oem install.

I wanted to use 'oem' because I was setting up for someone else who wants to try Linux.

As Ubuntu installs OK in 'oem' mode on same mch. it seems that you are telling me that
the Xbuntu iso has a bug in 'oem' install?

Don't want to waste more time if the Xbuntu bug is elsewhere.

---

### Post by darkteckno on 2006-10-06
Or there is the beta: [http://cdimage.ubuntu.com/xubuntu/releases/edgy/beta/](http://cdimage.ubuntu.com/xubuntu/releases/edgy/beta/)

---

### Post by Zerksis on 2006-10-08
"Then choose "Install in text mode" ... don't use OEM mode."

OK that works - using the same disk ! and on both mch's

Thanks KM

So - for some mch's the Xubuntu alternate iso has a bug in OEM install.

I'll post a new thread aimed at saving others some time and irritation.

---

