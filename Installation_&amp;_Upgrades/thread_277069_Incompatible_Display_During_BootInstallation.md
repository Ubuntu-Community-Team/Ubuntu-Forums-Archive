---
title: "Incompatible Display During Boot/Installation"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by davidwsica on 2006-10-13
I'm trying to install Ubuntu onto a new system I have with the Intel 945GZ Express Chipset onboard video hooked up to a Dell 2405FPW monitor via VGA.  I've tried with both 6.06.1 and 6.10 beta with the same result that I can see it booting up but it gets to a certain point during startup and my monitor complains that is is unable to support the current display mode.  I have tried the safe graphics mode as well as changing the F4-VGA option to no avail.  Interestingly, I am able to boot a Knoppix 5.0 Live CD with no problems.  I'm new to Ubuntu, any ideas what I can do to resolve this issue?

Thanks,
David

---

### Post by meng on 2006-10-14
If you're sure you want to install Ubuntu, then download, burn and use the Alternate CD rather than the Desktop CD. This will go straight to a text-based installer without booting to a graphical desktop first. After installation, if further video tweaking is required, this should be relatively straightforward.

---

### Post by davidwsica on 2006-10-14
> **meng said:**
> If you're sure you want to install Ubuntu, then download, burn and use the Alternate CD rather than the Desktop CD. This will go straight to a text-based installer without booting to a graphical desktop first. After installation, if further video tweaking is required, this should be relatively straightforward.

Thanks for the advice.  I'll give the Alternate CD a shot for installation.  I'm not sure I'd agree at this point that the video tweaking will be straightforward but we'll see.  As a side note it still troubles me that I can't run a Ubuntu Live CD with this system.  This surprises me.

---

### Post by meng on 2006-10-14
It may be as simple as the system not recognizing your LCD monitor, and trying to pass a vertical refresh rate above the capacity of your monitor; indeed I saw this very problem described by someone else recently, and even the safe graphics mode didn't work. If this IS the case, a simple edit of your /etc/X11/xorg.conf file should fix it once the system is installed. Is there a way to do it without installing first, so that you can evaluate the Live Desktop? Perhaps there is, but I'm not certain.

---

### Post by davidwsica on 2006-10-14
> **meng said:**
> It may be as simple as the system not recognizing your LCD monitor, and trying to pass a vertical refresh rate above the capacity of your monitor; indeed I saw this very problem described by someone else recently, and even the safe graphics mode didn't work. If this IS the case, a simple edit of your /etc/X11/xorg.conf file should fix it once the system is installed. Is there a way to do it without installing first, so that you can evaluate the Live Desktop? Perhaps there is, but I'm not certain.

As I thought, this is easier said than done.  I've installed via command line but cannot for the life of me determine the proper settings in my /etc/X11/xorg.conf to get this thing working.

---

### Post by cbalmforth on 2006-11-02
Try examining the /etc/X11/xorg.conf file that Knoppix 5.0 uses, or even using this one instead of the Ubuntu one (after backing up the original of course!)

---

### Post by davidwsica on 2006-11-04
> **cbalmforth said:**
> Try examining the /etc/X11/xorg.conf file that Knoppix 5.0 uses, or even using this one instead of the Ubuntu one (after backing up the original of course!)

Thanks for the suggestion, I didn't think of that.  However, as a result, I've moved on to trying SuSe and NexentaOS.  Maybe I'll give Ubuntu another shot in the future.

---

