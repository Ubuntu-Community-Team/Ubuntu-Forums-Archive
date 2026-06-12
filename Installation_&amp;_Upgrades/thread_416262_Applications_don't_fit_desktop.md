---
title: "Applications don't fit desktop"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by riseringseeker on 2007-04-21
Hi

I am not overly new to linux, been running Mandrake/Mandriva since 9.2 (what's that, 4 years now?)

I have been asked if I can set up an old laptop for a friend that has been threatening to get on the internet for quite some time.  I have been very impressed with what I've seen with Ubuntu, installed without a hitch, even with the ancient Gateway solo 2500, even got the linksys wpc54g wireless card with very little trouble.  I really believe this non-comnputer user will be quite pleased with how this box works (esp. for the price!  $0)

At this point the only problem I am having is that some of the administrative applications (i.e.  System -> Administration -> Login Window) extend beyond the bottom menu, and cannot be resized.  This means the final choices (like "OK") cannot be seen.

I would appreciate any help I can get on this, thanks

---

### Post by heimo on 2007-04-21
Can you change to higher resolution? What is it using now?

---

### Post by riseringseeker on 2007-04-21
> **heimo said:**
> Can you change to higher resolution? What is it using now?

Nope, at the highest resolution now.  The laptop is: [http://support.gateway.com/s/Mobile/Solo_Series/P2500/P2500nv.shtml](http://support.gateway.com/s/Mobile/Solo_Series/P2500/P2500nv.shtml) and has the 12.1 inch screen, which, unless I am misreading the specs, only allows a 800x600 60 Hz resolution.

I have looked through some other posts here and have seen some disagreement over what the max resolution is - though that may only apply to the larger screen, I don't know.  If anyone has an idea that can allow a 1024 X 768 resolution, I am all ears.

---

### Post by TheThirdBardo on 2007-04-21
Have you tried to select a smaller font size?

To also get smaller font size in the administrative settings you may have to run the Control center as root. To do this, run the command *sudo kcontrol*

---

### Post by heimo on 2007-04-21
I think it's a usability bug. There is one way around this - some people may like it, others hate it. You can set your desktop larger than resolution - using a virtual screen. You do it by changing /etc/X11/xorg.conf, something like:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7300 GS]"
        Monitor         "CM752"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "800x600"
[COLOR=Red]                 Virtual         1024   768[/COLOR]
        EndSubSection
EndSection
```Then you restart Xorg, and you should be able to choose this higher resolution. In system->Preferences->Screen resolution. It won't change actual resolution, but will make your screen scroll with your mouse pointer. So you see a 800x600 area of your 1024x768 screen.

---

### Post by riseringseeker on 2007-04-21
> **TheThirdBardo said:**
> Have you tried to select a smaller font size?

To also get smaller font size in the administrative settings you may have to run the Control center as root. To do this, run the command *sudo kcontrol*

Pretty sure kcontrol is a KDE thing, and with this limited hardware, KDE is not really doable.

---

### Post by riseringseeker on 2007-04-21
> **heimo said:**
> I think it's a usability bug. There is one way around this - some people may like it, others hate it. You can set your desktop larger than resolution - using a virtual screen. You do it by changing /etc/X11/xorg.conf, something like:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7300 GS]"
        Monitor         "CM752"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "800x600"
[COLOR=Red]                 Virtual         1024   768[/COLOR]
        EndSubSection
EndSection
```Then you restart Xorg, and you should be able to choose this higher resolution. In system->Preferences->Screen resolution. It won't change actual resolution, but will make your screen scroll with your mouse pointer. So you see a 800x600 area of your 1024x768 screen.

Does not seem to work for me, it just crashes the Xserver on start.  Just wish the app window was scrollable, or resizable.

---

