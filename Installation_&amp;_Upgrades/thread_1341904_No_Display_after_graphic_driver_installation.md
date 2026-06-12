---
title: "No Display after graphic driver installation"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by orihon on 2009-11-30
I've recently decided to start using Ubuntu. 

I get it installed fine and running, however when I install the display drivers from either Unbuntu's Restricted drivers process or manually download Nvidia Linux drivers and install them I get no output from my graphics card.
I'm assuming its not working with my graphics card somehow. The screen has no output and the monitor switches to stand by.

So far I've tried to find every available source of information for a cure but to no avail (I've tried both Google searches and searches of this forum). I've tried many suggestions I've found but none have worked.

I'm runnning Ubuntu 9.10.14, have tried Nvidia linux drivers 185 and 190 (newest).
I've followed Nvidia's instruction to manually install 190 and allowed Ubuntu to do it own thing for 185 on two different installs of 9.10.

I'm runnning a Nvidia 7900GS with Ubuntu 9.10-14 64bit.

I'm a beginner (aka - first time user but understand Windows well) at Linux so clear instructions would be greatly appreciated.

Thanks!

EDIT:
To provide some additional infos, I am able to run the restricted drivers install and everything is fine - its says to reboots, after I reboot I heard the Ubuntu 'OS loaded' sound but my display has no input.

I just tried it without rebooting and have found that the new drivers are running fine (i.e. I can load the Nvidia control center) however it prompts me to load Nvidia into X config. Having tried just rebooting on previous installs with no results so I figured I'd go in Terminal and manually add the nvidia x-config. After doing this the screen immediately stopped display (i.e. no graphic card output).

---

### Post by RochJer on 2009-11-30
There is the thread that previous user had the no display issue - it was solved. Perhaps you should try the same thread and see if it works out on your end:

[http://ubuntuforums.org/showthread.php?t=1341106&highlight=NVIDIA+restricted+drivers](http://ubuntuforums.org/showthread.php?t=1341106&highlight=NVIDIA+restricted+drivers)

---

### Post by orihon on 2009-11-30
This tells me how to get back to default graphics. If I needed to do that I could simply reinstall Ubuntu (which I've already done several times).

I need a work around or help to get the Nvidia graphics drivers to work on my install of Ubuntu.

What could be causing the issue and how to solve with Nvidia drivers it is essentially my question.

Thanks for trying though.

---

### Post by RochJer on 2009-11-30
> **orihon said:**
> This tells me how to get back to default graphics. If I needed to do that I could simply reinstall Ubuntu (which I've already done several times).

I need a work around or help to get the Nvidia graphics drivers to work on my install of Ubuntu.

What could be causing the issue and how to solve with Nvidia drivers it is essentially my question.

Thanks for trying though.

There is another software that can configure nVidia drivers - Envy. Try going to the Synaptic Package Manager and then look for Envy, install this and configure drivers for nVidia. There is the link that may help out: 

[https://wiki.ubuntu.com/EnvyNG](https://wiki.ubuntu.com/EnvyNG)

---

### Post by jaylsi on 2009-11-30
I once had same problem with my GeForce FX5200 card. The fix to me is to add this line into Section "Device" of /etc/X11/xorg.conf:
Option "NvAGP"  "1"

You may want to try that.

---

### Post by orihon on 2009-12-01
> **jaylsi said:**
> I once had same problem with my GeForce FX5200 card. The fix to me is to add this line into Section "Device" of /etc/X11/xorg.conf:
Option "NvAGP"  "1"

You may want to try that.

I tried this however it won't allow me to edit it from within command terminal.
I was using the following code to attemp an edit:
```
sudo gedit /etc/X11/xorg.conf
```


> **RochJer said:**
> There is another software that can configure nVidia drivers - Envy. Try going to the Synaptic Package Manager and then look for Envy, install this and configure drivers for nVidia. There is the link that may help out: 

[https://wiki.ubuntu.com/EnvyNG](https://wiki.ubuntu.com/EnvyNG)

I just tried EnvyNG and got the same results unfortunately.

---

### Post by jaylsi on 2009-12-01
I am not sure why you can't run "sudo gedit /ect/X11/xorg.conf". You can always try "sudo vi /etc/X11/xorg.conf" but you have to know vi editor commands.

From your posting, I can see your system works fine with default video driver. The problem only occurs when you tried to use nVidia restricted driver. I imagine some cards would have issues like that for Ubuntu 9.10. To go back to default video driver though, do this:

1) Reboot
2) On boot selection screen, select "Recovery mode" (should be the second in the list)
3) Select "Drop to root shell"
4) sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
5) sudo reboot

---

