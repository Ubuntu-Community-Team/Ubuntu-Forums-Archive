---
title: "How to get higher resolution on flat screen monitor"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by dkuhlman on 2007-10-26
I have a flat screen moditor.  The resolution recommended by the manufacturer is 1440x900.  But, I am unable to use that resolution.

I found this clue:

"Fortunately, both ATI and nVidia offer custom Linux device drivers for their products. These drivers are proprietary software, which means Ubuntu will not install them by default. If your PC includes hardware from one of these vendors, you can enable the accelerated driver from the System > Administration > Restricted Drivers Manager control panel."

[see [http://www.infoworld.com/article/07/10/22/43FE-linuxswitch_graphics_1.html]](http://www.infoworld.com/article/07/10/22/43FE-linuxswitch_graphics_1.html])

I'm guessing that the "System > Administration > ..." thing is for Gnome.  How do I do that in Kubuntu/KDE?  I've looked in both "System Settings" and "Control Center", but can't find anything that seems related.

Is there a doc on this somewhere?

I'm using Kubuntu feisty fawn.

My video card is MSI NX7300LE-TD128EH GeForce 7300LE 128MB 64-bit GDDR2 PCI Express x16 Video Card.  Chipset is NVIDIA.

The monitor is: Hanns·G HW-194DJB.

Thanks for help.

Dave

---

### Post by billrad1 on 2007-10-26
You could try envy, the invidia installer. 

that works pretty well.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by DaveLG on 2007-10-26
[I]I second the use of the Alberto Milone  Envy driver setup program. I just used it on a new Kbuntu 7.1 install and was able to load the Nvidia drivers and the Nvidia setup program where I was able to set my Samsung 24 inch monitor to 1920 x 1200 resolution.

I did have to set the 50Hz mode but after that it worked fine.


It is a mighty fine piece of software that I have used also for a Ubuntu 7.04


Dave

[/I]

---

### Post by dkuhlman on 2007-10-27
Just reporting back on my progress.

Thanks for the suggestions to use Envy.  That worked great.  I'm now viewing my screen at 1440x900.  Super.

On my system, which is still very new, I had to install about 10 or so dependencies.  That was a small chore, because Debian makes installation easy.

I have no idea what Envy did.  But watching the output to the transcript window gave me the idea that it did lots.  Is there a log anywhere that I could look at?

Oops.  I found it.  Never mind.  If anyone who uses Envy wants to look at the log, it's at:

```
/var/log/envy-installer.log
```

Thanks again.  This kind of help is what makes Ubuntu so great.

Dave

---

### Post by dkuhlman on 2007-10-31
> **dkuhlman said:**
> Just reporting back on my progress.

(snip)

Thanks again.  This kind of help is what makes Ubuntu so great.

Dave

One more report ...

My machine has an AMD 64 X2.  And, I decided that I needed Gutsy Gibbon.

When I re-installed Ubuntu Gutsy Gibbon, the monitor resolution was taken care of for me.  The default resolution on my system is now is 1440x900.

That this happened automatically might have something to do with the fact that the restricted repositories are enabled in my /etc/apt/sources.list.  I don't understand that too well.

Dave


Dave

---

