---
title: "Simply cannot get past the end of the install (locks up, video driver issue?)"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Zyzzyva100 on 2006-06-01
This is my second attempt at installing ubuntu on my fiancee's computer.  I previously tried with breezy, but had similar problems to what has been happening to me today, and had to scrap it.

To begin with, it took a few tries to get the live cd to even boot, for some reason it would get to the point at which the graphical login manager would come up, and then just lock.  So I tried the safe video mode, and was able to get through the entire install.

Upon the first login attempt, the screen again locks (mouse no longer respond, and keyboard is gone, can't turn numlock etc lights on or off).  So I tried again to reboot and go to the terminal at boot via ctrl-alt-f1, and got there only to have the computer again immeadiately lock. 

I am pretty sure that the problem lies in the nvidia 6600 video card, since there are some weird video distortions when this happens (some of the time at least)  I think maybe I just need to enable vesa, but I can't even seem to get far enough to configure xorg.

Previously when this happened I though it had something to do with the keyboard or mouse, but have tried every combination or wired and wireless keyboards on ps/2 and usb with no luck.

Does anybody have any ideas for how to go about fixing this?  I can't believe that even before the official beta release I was able to install on my laptop with no issues at all, but can't get the install to take on this desktop.  Any help here would be appreciated.  My finacee really likes using ubuntu on my laptop, and its frustrating that I can't get it setup for her on her desktop.

---

### Post by Jason_25 on 2006-06-01
1.Have you verified that nothing is overheating?
2.Have you checked the cd integrity?
3.Have you run memtest86?

---

### Post by Zyzzyva100 on 2006-06-01
Yes to all the questions, its not a hardware issue.  The computer runs windows fine, the md5 sum checked as did the cd integrity check at the boot menu, memtest86 shows no errors, and the processor is running at about 35 degrees C.

Whatever is wrong is deffinitely a software issue.

---

### Post by Zyzzyva100 on 2006-06-01
Ok, so now I kinda have this working.  I am able to login via recovery mode and then startx, but some things (like dbus) aren't started.  Having never had to use recovery mode before, am I to assume this is on purpose?

I also noticed that during boot, a message quickly flashes saying:
"Cannot allocate resource region 3 of device 000:05:00.0" which is the address of the PCIe video card.  I have a feeling this is all connected, I just can't quite figure it out.

---

### Post by Zyzzyva100 on 2006-06-01
I am still able to only login via recovery mode.  I installed the nvidia binary driver, and installed the K7 restricted module, but I even when I do manage to get to the desktop, I get an error saying that dbus has not been started, and now I get an error saying that HAL has failed to initialize.

I have seen other reports of problems with HAL, but it was related to samba shares being mounted through fstab.  I just can't figure out what is going on, and its driving me nuts.  It comes so close to working, and then conks out at the last minute.  At this point it has to be something with HAL or dbus, I wonder if this motherboard just won't work with linux.

EDIT:
Ok, so now I deffinitely have the problem narrowed down.  If I start via the recovery mode for the k7 kernel, and start gdm I can now login as a user.  Every time I login I get the error that HAL and dbus have not started. 

However, if I manually start dbus through terminal (which starts HAL), then it will start without problem.  At that point everything works as it should, and I can plug in usb drives and they automount and everything.

So, now the question is, how do I go about figuring out how to make sure that HAL and dbus start.  If I start the regular kernel, I still have the problem wherein as soon as the gdm login box comes up, the computer freezes, so there is nothing I can do there.  Anybody have any ideas?

---

