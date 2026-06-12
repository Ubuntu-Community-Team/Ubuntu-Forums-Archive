---
title: "Infamous &quot;Checking battery state...&quot;"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by linuxuser21 on 2011-10-28
I'm getting the (apparently common) problem where after a new install or upgrade (mythbuntu 11.10), the system hangs after "checking battery state" on my HTPC.

Specs:
*mobo: kalmet2 (A7V8X-LA)
*GPU:  9500 GT (SP95GT512D2L-HP)
--DVI > HDMI adapter
*AMD Athlon XP 3200+
*2GB Ram
*Audigy 2
*hauppauge 1600

I've tried:
*About 5 fresh installs.  Each one trying something different than the last.
*Regular Ubuntu (11.10) install.  Same thing happens.
*sudo startx
*Purging lightdm
--a. reinstall lightdm
--b. install GDM
*remove /etc/X11/xorg.conf 
--a. rebuild
--b. completely purging xorg & reinstall & rebuilding
*uninstall nvidia drivers & reinstall with wget

If you need the exact commands I used, I can get those for you as well.  I've searched about 5 pages deep in Google, trying each different thing.  I am more than willing to reinstall for a "clean" install.
I'm about ready pull my hair out with this.  I decided to get rid of Windows 7 and my WMC setup for something more cooperative.  We use this box A LOT so i really need to get it back up.

Thank you for your time!

---

### Post by linuxuser21 on 2011-10-30
So, I got a little further.  I managed to pull up the GUI but I'm back to start now.

Here's what I did:

*Took out the graphics card (nVIDIA 9500 GT)
*Hooked up VGA monitor to the onboard video
*Reinstalled

At this point the regular desktop came up like it was supposed to.  As expected, it was slow and incapable (as far as graphics go) seeing how old it is.

So I then put the graphics card back in and rebooted.  The desktop appeared like normal even from the right port (DVI).  I installed the latest drivers from nVIDIA's website and had it automatically configure X after it was done installing.  This is where I believe it is screwing up at.

Does anyone know how to get around or fix this?  Or really even tell me what is happening? :confused:

---

### Post by MAFoElffen on 2011-10-30
> **linuxuser21 said:**
> So, I got a little further.  I managed to pull up the GUI but I'm back to start now.

Here's what I did:

*Took out the graphics card (nVIDIA 9500 GT)
*Hooked up VGA monitor to the onboard video
*Reinstalled

At this point the regular desktop came up like it was supposed to.  As expected, it was slow and incapable (graphics wise) seeing how old it is.

So I then put the graphics card back in and rebooted.  The desktop appeared like normal even from the right port (DVI).  I installed the latest drivers from nVIDIA's website and had it automatically configure X after it was done installing.  This is where I believe it is screwing up at.

Does anyone know how to get around or fix this?  Or really even tell me what is happening? :confused:
Use my sticky for reference if needed, but I'll take care of you here...
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

-What binary driver version number from NVidia? 280.13, 285.05 or 290.03?  
- Before you installed the binary did you do the following? 
```

sudo nividia-install --uninstall
sudo apt-get remove --purge nvidia-*

```Please send the last generated /ect/X11/xorg.conf and an /var/log.Xorg.x.log (where x= 1 thru 5) where it was trying to boot on the NVidia card and failed. 0 is current and the number goes up for each previous boot. Also post your/var/log/nvidia-installer.log.  Remember to post those within CODE tags.

EDIT-- When it hangs at the "Checking Battery State" through the "Checking For System 5 Compatibility" it is usually a graphics problem where there are no drivers, drivers are not loading or there is something conflicting with the driver modules.

---

### Post by BobW on 2011-10-31
I'm having the same problem.

What makes me mad is that I did a test with booting the CD to the desktop before installing.

Now that I really installed it I can't boot. This is my main computer - I'm so screwed.

---

### Post by BobW on 2011-11-01
Update - I did get it working by using a differnt version of the nvidia driver.

I still don't understand why the live CD worked but an install didn't.

---

### Post by linuxuser21 on 2012-04-23
After attempting to completely remove anything nVidia and install it from fresh as suggested without any luck, I finally just gave in and got the graphics card I had my eye on for this computer.  The 9500 GT was just supposed to be a temporary card until I got this one (Radeon HD 4650).  Ubuntu acted completely different to this card and just worked without any issue.
In my experiences I have learned that there are just to many setups and a lot of different hardware out there for everything to just cooperate.  This is one of them.

Thank you MAFoElffen for the replies.  I will be returning to your sticky in the future as I am not done with this card ;).

---

