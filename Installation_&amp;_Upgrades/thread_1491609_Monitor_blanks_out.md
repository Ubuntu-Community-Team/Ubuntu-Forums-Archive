---
title: "Monitor blanks out"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by detoam on 2010-05-23
I am trying to install 64 bit 10.04
My system is:
Athlon X2 64Bit 5200+
3 GB RAM
Video is XFX Radeon HD5670

Problem is that when I try either the preview before install or install the screen goes blank shortly after the loading screen appears. I have tried using the options to nomodeset, noapic, nolapic and still it does the same. 
My video card only has the DVI output so I can't use the VGA inputs on my monitor.
I've been at this for the last hour and a half, trying various combinations of the boot options. All to no avail.
Please help.

---

### Post by elohssa on 2010-05-23
Mine is doing the exact same thing.  I have the same video card but different other specs..

---

### Post by detoam on 2010-05-23
Frustrating as hell

---

### Post by detoam on 2010-05-24
I finally installed it.
I found an adaptor to switch from DVI to VGA for my monitor. Changed boot options to nomodeset, noapic, noalpic (removed the silent and splash options).
Can't go back to digital video mode as I can't figure out how to install new video drivers. I found them and figured out that I have to run the *.run as an application, but it keeps telling me that I have to be super user. Can't figure out how to do that.

---

### Post by wojox on 2010-05-24
Try logging out and when you get to the GDM screen press Ctrl+Alt+F1 

Then:

```
sudo /etc/init.d/gdm stop
```

```
sudo killall Xorg
```

Then go to the directory your .run file is in and 

```
sudo sh *.run
``` 

Use the whole name of the file.

---

### Post by detoam on 2010-05-24
Thank You wojox.

---

### Post by elohssa on 2010-05-25
YAY got mine working too... I actually took out my Vid Card and installed 10.04 through my onboard video card.  Then I replaced my graphics card to my computer.  Then I booted into recovery mode with low graphics mode.  Ran updates, then tried to install the ati driver through the hardware drivers.  This was unsuccessful for me, so I then downloaded the driver directly from [www.amd.com](www.amd.com), then ran sudo chmod +x file.run.   Then sudo file.run.  Came up and installed the driver, rebooted, and is working ok now.

---

### Post by detoam on 2010-05-25
I got it to work as well. I couldn't remove the card, but I finally figured out that leaving the downloaded driver in the Download folder does the trick. Before, I tried moving the file to the Desktop. Now I just need to get a better power supply. Mine works great, but it's underpowered for the card.

---

