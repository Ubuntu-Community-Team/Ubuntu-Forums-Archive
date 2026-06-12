---
title: "Still can't get Ubuntu to work on my computer"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by jadarite on 2012-04-16
Well, I don't know what to do here.

For the past 2 months I have tried to get Ubuntu on my computer with no luck, but Windows 7 works perfectly fine.

If I just load it from the hard drive the ubuntu logo with the orange animated dots appear and nothing else happens.  I let it sit for 30 minutes, nothing happened.

If I try to reinstall Ubuntu, then after 1.5 hours it stalls at "Restoring previous packages". 

There is no progress meter, so I don't know if that is the final step or if I will have to wait a decade for it to finish.  My guess is that something is not working.

---

### Post by critin on 2012-04-16
> **jadarite said:**
> Well, I don't know what to do here.

For the past 2 months I have tried to get Ubuntu on my computer with no luck, but Windows 7 works perfectly fine.

If I just load it from the hard drive the ubuntu logo with the orange animated dots appear and nothing else happens.  I let it sit for 30 minutes, nothing happened.

If I try to reinstall Ubuntu, then after 1.5 hours it stalls at "Restoring previous packages". 

There is no progress meter, so I don't know if that is the final step or if I will have to wait a decade for it to finish.  My guess is that something is not working.
> 
[COLOR=Red]**If I just load it from the hard drive** [/COLOR]the ubuntu logo with the orange animated dots appear and nothing else happens. Do you mean BOOT, or run it from the cd from Windows?  It must boot the machine.
Usually when this happened to me it was a faulty burn/download.  I would download again and burn at the lowest speed.  I have better luck with unetbootin and flash drives.  Never any issues.> 
[COLOR=Red]
**If I try to reinstall Ubuntu**[/COLOR], then after 1.5 hours it stalls at "Restoring previous packages". Above it seems you couldn't get this far, the cd just sit there.  Reinstall?  You have installed it before?

No, that is not the final step.  If it has installed it will say so and ask you to restart the machine.
Did you get past the area where you choose and prepare the partition?  That comes close to the beginning.

I suggest downloading a new image and try again.

---

### Post by jadarite on 2012-04-16
> Do you mean BOOT, or run it from the cd from Windows?

I am not using anything related to a CD.  I am using a USB stick.  I had no problems with Ubuntu until I tried to upgrade to 11.10 (I was using some version of 10 before), then that is when problems occurred.  Now, I can't get anything to work.

> Above it seems you couldn't get this far, the cd just sit there. Reinstall? You have installed it before?

Well, kind of.  I tried to "upgrade", but in effect it downgraded to a non-usable operating system.  So, I tried to install from scratch 2 months ago and nothing happened.  Now, it seems to be getting further along in the process, but it hangs at "restoring previous packages". 

> Did you get past the area where you choose and prepare the partition? That comes close to the beginning.

I already did that.  So, what I am doing now is using Windows 7 to download the beta 12.04 beta 2.  Again, all of this will be from the USB stick, not a CD. 

After that, I'll just remove the 11.10 and hope that fixes things.  I think the programmers for Ubuntu should put up a status line showing how far the FULL installation is.  They could make a checklist to show the user how much more needs to be downloaded.  The way it is now, the green bar shoots across multiple times.  There is no way to know how many times it will do this before it is finished.

---

### Post by mastablasta on 2012-04-16
you are still not perfectly clear. at least to me. so you booted from some other USB and made a full install to USB key ? Or did you create a liveUSB using unetbootin or similar windows programme? Or did you use a wubi install where you chose to put the Ubuntu to the USB?

---

### Post by More or Less on 2012-04-16
> so you booted from some other USB and made a full install to USB key ?

I don't know what USB key is, but the procedure I have done is to download "Universal-USB-Installer" and then use that to install Ubuntu.  It has worked flawlessly with any version of 10 and earlier (I have done it multiple times over the years). 

Now I have version 1.8.9.1 and I am 75% through with downloading Ubuntu 12.04.  One thing I am not sure about is that there are 2 entries for 1.8.9.1, one is for "Daily" and another is for "Beta".  I think I will try the Beta one first.

> Or did you create a liveUSB using unetbootin or similar windows programme? Or did you use a wubi install where you chose to put the Ubuntu to the USB?

I am sorry, I don't know what liveUSB, unetbootin, or wubi are.  Again, for my next try, I am going to:

1. Download 12.04
2. Using Universal-USB-Installer 1.8.9.1, I will install Ubuntu 12.04 onto a USB
3. I will boot my computer from the USB Drive, select the option to reinstall over any previous Ubuntu versions (keeping Windows 7, I still need it at least until I get one version of Ubuntu working again and I don't want to go back to 10 if 12.04 can work).

If there is any reason why I shouldn't try this, please let me know.  It will save a few hours of downtime if you know it won't work.  Thanks in advance.

[Edit: I was able to install 12.04, the trick is to not have it connect to the internet while installing.  Also, I noticed in my research others have experienced it stopping when it reaches something called "arch".  If you open the install area on the left of the progress window, you can click a "skip" button on the right that appears.  After that it finishes.  I did this 2 or 3 times and it must of completed within 10 minutes or so.  Much faster. :p]

---

