---
title: "Asus EN8500GT Silent on gutsy? As useless as a rock!"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by tag on 2008-01-28
I bought an Asus EN8500GT Silent 512MB today and tried to make it work on my Asus  M2N32 WS Professional Motherboard. My old card (A 7300) refused cooperation on all systems, so I thought this one might work.

Well it works on the open source "nv" driver. However it doesn't on nvidia-glx-new, the envy driver or anything else I have found on the forum. I tried the dpkg-reconfigure xserver-xorg dance, I tried to install the drivers via synaptic and over commandline - it just won't work.Whenever I reboot i get sent to the "Ubuntu is running in low graphics mode" screen, where I have to select all the right settings, only to be sent there again on next reboot. (And by the way, yes - I did remove the old drivers before I installed the new ones)

The only thing that works is the nv driver which, obviously, is not a solution.

Now, if any of you guys know what is wrong with my conf, your help would be greatly appreciated, otherwise I might end up with a pile of gfx cards and be broke as hell by the time I find a working solution ;)

---

### Post by overdrank on 2008-01-28
HI and do either of the graphics cards need additional power? When you receive the low graphics error can you and have you tried to switch to a terminal and use the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by tag on 2008-01-28
Hy overdrank,
additional power? You mean like an external power cord or something? No, none of that. The only connector is the PCI-Express slot.

Apparently the command line you mentioned doesn't work either. It just messed up my keyboard settings (set the layout to default english). Thanks for the suggestion though.

---

### Post by overdrank on 2008-01-28
> **tag said:**
> Hy overdrank,
additional power? You mean like an external power cord or something? No, none of that. The only connector is the PCI-Express slot.

Apparently the command line you mentioned doesn't work either. It just messed up my keyboard settings (set the layout to default english). Thanks for the suggestion though.

Ok I see that board has SLI  could there be something in the bios pertaining to the graphics SLI that might be interfering?

---

### Post by tag on 2008-01-28
Hmm - I went through all settings in my bios and switched the SLI related features off. Actually it was only one option: There was a setting called "SLI ready memory" which I disabled.

But it didn't change anything for me. :confused:

I kept playing with some BIOS settings, but I have to say that though I'm a developer myself, I am quite low-level illiterate and have little clue on these things. Any suggestions on what other settings might need some tweaking?

---

### Post by tag on 2008-01-29
I just played with a few settings:
Chipset/NVIDIA GPU Extension: was: Disabled set to: Auto
PCIPnP/Plug&Play OS: was: No set to: Yes
PCIPnP/Ressources: was: Manual set to: Auto

Again, this didn't change anything. *sigh*
I'm getting the feeling this might be entirely unrelated to the BIOS.

---

### Post by Pumalite on 2008-01-29
Take a look at this thread, it might be helpful:
[http://ubuntuforums.org/showthread.php?t=679266](http://ubuntuforums.org/showthread.php?t=679266)

---

### Post by tag on 2008-01-30
@Pumalite
Thank you for the suggestion. After I tried the manual install, which compiled some kernel interfaces to go, I already thought I'd make it, but unfortunately this didn't work either.

However, I found this error message in /var/log/Xorg.9.log after trying to start up X:

> (II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


I don't know what to make of it. Ideas? Anyone? Ferris? ;)

I'm attaching the whole logfile to this post, maybe that helps?

---

