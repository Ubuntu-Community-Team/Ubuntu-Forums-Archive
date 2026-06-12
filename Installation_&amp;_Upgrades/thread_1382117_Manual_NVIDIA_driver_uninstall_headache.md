---
title: "Manual NVIDIA driver uninstall headache"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by TrevorBradley on 2010-01-15
Long ago (Back in the Intrepid Ibex days) I ran a manual upgrade of NVIDIA drivers from NVIDIA's website, in an attempt to get Wine running better on my system.  Now every time I run upgrade manager, this message (or something similar) pops up twice every time I run upgrade manager:

```
The system has detected an obsolete NVIDIA driver in your system.

Please install nvidia-glx-185 at the end of the installation with the following command:

sudo apt-get install nvidia-glx-185

The removal of other NVIDIA drivers will be dealt with automatically. 
```

I actually have nvidia's 190 drivers installed, so the error message is a bit of a misnomer.  This message has been persistent with every upgrade, and appeared many times during the Karmic upgrade.

Now I understand when I did this originally every time I get a kernel upgrade and rebooted I'd need to reinstall NVIDIA's drivers.  But ever since my Karmic upgrade, things seem to be a bigger hassle than normal.. The system almost locks up after reboot.  Compiz now seems crippled and I've disabled it just to get a decent framerate.

What I'd really like to do is go back to Karmic's NVIDIA drivers and not have to deal with update problems anymore.

However, when I attempt to reinstall Karmic's NVIDIA drivers, I just can't seem to make this error message go away or get the drivers to work.  I end up frustrated an hour later, reinstalling NVIDIA's drivers because something is broken and I just can't get jaunty's drivers working at all.

Are there instructions anywhere for expunging NVIDIA's command console drivers and getting back on track with Karmic's drivers?

I have an asus m2npv-vm motherboard with onboard GeForce 6150.  My system was originally an Intrpeid system... the upgrade to Jaunty was great, but this Karmic upgrade hasn't been hassle free.

I know I've not provided enough info here, but I'm not sure what would be relevant.  I'll be happy to post more info as required.

Thanks in advance!

---

### Post by TrevorBradley on 2010-01-15
OK, in an attempt to document this... here's a log of my latest upgrade attempt...

Upgrade kernel. (2.6.31.17 pae)
modify xorg.conf to point to nv instead of nvidia
Tell system to install nvidia glx 185 drivers
rebooted
system comes up to console only
startx results in "no screens found"
nvidia-glx-185 is already installed according to apt-get
modify xorg.conf *again* to change nvidia to nv in the devices section
startx gives a console
Install nvidia glx 185 from Hardware drivers... no, let's remove/install this time... (removing driver takes a *very* long time, perhaps 4 minutes)
That was odd... Hardware Drivers said something about the existing 185 being a "different version".. maybe this is the source of my annoying error.  Perhaps that 4 minute expunge will do my system good.
Install and activate 185
Restart again.
XWindows comes up properly.. Oooo, with a good framerate too.. this is a good sign.
Attempt to turn on Compiz with Extra effects... "Desktop Effects could not be enabled" (likely a glx thing)
Added option "Composite" "Disable" to an "Extensions" section at the end of my xorg.conf...
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

...

Wait a second.. research seems to indicate the Proprietary NVIDIA drivers (from NVIDIA's) site have an --uninstall option.  GLX looks buggered because of a driver conflict.

*will post update briefly*

---

### Post by TrevorBradley on 2010-01-15
OK, there's the command I was looking for!

/etc/init.d/gdm stop (This will stop X!)
sudo sh ./NVIDIA-Linux-x86-190.42-pkg1.run --uninstall
/etc/init.d/gdm start

And now GLX is working with Karmic's glx drivers. (Tested with "glxgears")

Compiz's framerate seems like it's about 3fps, but that's another problem.

---

### Post by TrevorBradley on 2010-01-15
Aha!  And a few more minutes investigation has found the source of all my compiz problems.

The Asus's onboard video has a bios setting for how much memory to dedicate to the framebuffer.  By default it's 32Megs only!  I upped that to 256Megs and the performance is much better.

Compiz looks awesome even on a GeForce 6150 at 1920x1200.. Don't knock onboard video (but know how to use it, apparently).

OK, I'm all fixed!

---

