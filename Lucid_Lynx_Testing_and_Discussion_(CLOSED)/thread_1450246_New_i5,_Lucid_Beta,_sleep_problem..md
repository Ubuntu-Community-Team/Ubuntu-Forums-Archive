---
title: "New i5, Lucid Beta, sleep problem."
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wadam on 2010-04-08
Hi everybody --

I just installed Lucid Beta 2 on my newly built core i5 system.  I've found that everything works very well, except that it doesn't seem to want to sleep or hibernate.  When I tell the system to sleep, it locks the screen like it should, then the display blanks for a minute, then it goes back to the locked screen.  When I tell it to hibernate, I get an error message about it not being able to shut down a USB device, the screen blanks for a minute, then it goes back to the locked screen. My relevant system details are:

i5 750 CPU
Gigabyte H55M-USB3 motherboard
Geforce 250 (running the proprietary drivers)

And connected to the computer's USB ports are an Apple keyboard and a set of logitech USB speakers.

Any help would be greatly appreciated.

Also, on a related note, if anybody knows how to blank the screen when the nvidia driver is active, I would appreciate some advice on that as well.

Thanks ahead of time!

---

### Post by emanuel.b on 2010-04-08
I'd unplug the Apple keyboard and the speakers, and then try sleeping it. If your computer dosen't have a sleep button, then plug in a different keyboard / mouse, and try to sleep it.

---

### Post by wadam on 2010-04-10
Emanuel --

I unplugged all of my usb devices and still have the same problem.  I do have an exact error message to share now, though:  "device USB9 failed to freeze."  Does that help at all?

Meanwhile, I kind of have the suspicion that it might be a problem in my BIOS.  I have no substantial reason to think that.  But if I can ever figure out how to unarchive an updated BIOS image from one of these accursed self-extracting .exe files, I intend to install it and see if that solves the problem.

---

### Post by emanuel.b on 2010-04-10
Did your computer have the same problem running 9.10? (Assuming that you ran 9.10 before upgrading.) It may be just normal beta issues, and should be worked out in future updates. You could also try deactivating the proprietary drivers.

Here's an app that extracts files from .exe and .msi installers. I'm not sure if it runs on linux, but you can go ahead and try...

[http://legroom.net/software/uniextract]("http://legroom.net/software/uniextract")

---

### Post by wadam on 2010-04-10
I never ran Karmic on this computer, so I couldn't say.  But this being a bug in the beta is a definite possibility.  I suppose I'll just have to wait it out and see if it goes away in the final release.

Thanks for the link.  I suppose that I'll upgrade my BIOS and see if that ends up helping the situation.

---

### Post by emanuel.b on 2010-04-10
You're Welcome!

Still it wouldn't hurt to download 9.10, boot from the cd, and see if it has the same problem.

---

### Post by wadam on 2010-04-12
So.  I upgraded my BIOS, and perhaps unsurprisingly, it did not solve the problem.  I did some looking through suspend.log, however, and here is what I discovered:  my system seems to think that it's going to sleep, then immediately waking up and restarting all services.  I'm not sure what to make of that.

---

### Post by aofc on 2010-04-22
I have the same problem on my Dell Studio 15: Sleep and Hibernate used to work perfectly in Karmic, but in Lucid Beta1 it caused a kernel error that prevented my CPU fan to work on wake up (thus causing overheating). On Beta2, sleep just locks the screen.

Will this be solved before launch of the new version??

---

### Post by teh603 on 2010-04-22
My i3 seems to have similar problems. I read something on the board somewhere about i-series systems not being able to suspend/resume until the .33 kernel. Lucid is going to be using the .32 kernel unless we get some kind of miracle.

Now, you can supposedly install the .33 kernel since it does have a stable release. I just don't know how to do it.

---

