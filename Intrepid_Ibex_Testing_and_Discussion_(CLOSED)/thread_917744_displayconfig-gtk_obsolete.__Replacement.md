---
title: "displayconfig-gtk obsolete.  Replacement?"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dawynn on 2008-09-12
Prior to Gutsy, there was dpkg-reconfigure xserver-xorg.  This would allow one to change Monitors, indicate video driver, indicate keyboard, mouse, video resolution, etc.  Anything that had anything to do with the Xorg.conf file was updatable there.  Now, this command only updates keyboard and mouse.

In Intrepid, if your choice of video card did not work (perhaps you've installed the latest legacy nvidia drivers, or tried drivers incompatible with your hardware), you would be presented at X startup with a tool where you could experiment with the drivers available on your system and could indicate what make and model your monitor was.  This tool was displayconfig-gtk.

I see now that displayconfig-gtk is being taken away.  And after trying a new recompile of the nouveau drivers, I was again confronted with the "low-resolution" screen at start of X.  Only this time, there was no GUI frontend to configure my monitor or video card.  I was allowed the option to either use my backup xorg.conf (which I could not do, for reasons irrelevant to this post), use the default setting (which chooses the vesa drivers) or manually update my xorg config file. Personally -- I haven't memorized the xorg.conf syntax well enough to feel comfortable with hand-editing, and I doubt most other common users will feel comfortable with such a daunting task.

So, what tool replaces these options?  I don't care if its console-based, like the old dpkg-reconfigure option was, or GUI-based like displayconfig-gtk, but I would like some tool that allows me to pick my monitor make and model, and my video driver, without the need to hand-edit xorg.conf.

---

### Post by wgrant on 2008-09-12
Monitors and their supported resolutions are autodetected - there's very little reason to specify them in xorg.conf. Input devices are also autodetected and configurable through XI properties and FDI files.

The set of display drivers for any video card is rather limited, and I believe one is meant to switch between nvidia and nv (for example) using jockey, the Restricted Drivers Manager. If you're using nouveau, you should probably know how to specify it in your xorg.conf yourself.

---

### Post by ShirishAg75 on 2008-09-13
Hi all, 
 Although dunno much but I think lot of things are now taken care of by X.org 

I would also be interested though to know what displayconfig-gtk is replaced with or obsoleted by.

---

### Post by lewmnik on 2008-09-13
> **fujitsu said:**
> Monitors and their supported resolutions are autodetected - there's very little reason to specify them in xorg.conf. Input devices are also autodetected and configurable through XI properties and FDI files.

But at least in Intrepid **this** (automagic) does not work. If I can't configure it myself I'll end up staring 800x600 display without compiz what used to be 1680x1050.... well done...

---

### Post by wgrant on 2008-09-13
> **lewmnik said:**
> But at least in Intrepid **this** (automagic) does not work. If I can't configure it myself I'll end up staring 800x600 display without compiz what used to be 1680x1050.... well done...

Have you filed a bug?

---

### Post by lewmnik on 2008-09-13
Indeed I have.

---

