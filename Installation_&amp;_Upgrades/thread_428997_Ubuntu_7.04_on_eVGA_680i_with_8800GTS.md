---
title: "Ubuntu 7.04 on eVGA 680i with 8800GTS"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by codezer0 on 2007-04-30
Hi all,

I'm currently at my wit's end with my new computer.

Short and simple:

- intel e6300
- eVGA 680i motherboard
- 2x1GB G.Skill DDR2-800 RAM
- eVGA 8800GTS
- Gateway FPD2185W monitor

At the moment I can't even get the liveCD to work properly on this machine. I can start up in either regular or safe grpahics mode, but it doesn't progress beyond the initial "loading linux kernel' part.

In safe graphics mode, it floods the screen with a bunch of repeating errors...

sb_bread failed reading block (some hex address)
 unable to read page [ some hex number ], size [ some other hex number ]
 zlib_inflate returned unexpected result [ some hex address ]
 and 
 d, srclength [some number], d_in 0, d_out [ random number ]
 
 those four just kept repeating on the screen.

So what can I do here to get this thing working?

---

### Post by Syke on 2007-05-01
Have you tried a Memory Test, and Check CD for Defects?

---

### Post by DJMatty on 2007-05-01
Hi

I have successfully got ubuntu 7.04 running on my Asus 680i mobo with 8800gtx gfx card, it took me a while to work everything out (being a linux n00b as well didn't help :) )

I had to use the safe graphics mode for the Live CD every time, as the normal mode won't work, and I did have trouble sometimes with safe mode not working, but I put that down to dodgy burns.

Once you have live mode running you need to modify /etc/modprobe.d/options and add a line to configure forcedeth, this will get the network cards working. (Add this line to it: 'options forcedeth msi=0 msix=0', then run these lines 'modprobe -d forcedeth', then 'modprobe forcedeth', then '/etc/init.d/networking -restart')

I then used the installer to install the o/s onto my HD, and then before rebooting made sure I had modified the modprobe options in the installed files.

I still needed to use safe graphics mode until I had installed the nvidia drivers, there is a tutorial for doing this by hand on Alberto Milone's web site, however I found that alt-f2 would not work to get to a terminal that is not in gnome, so I had to install rcconf and change the settings to prevent gdm from running, reboot, log in, install the drivers, then use rcconf to enable auto starting of gdm again.

Once this was done I could boot normally and use the nvidia card to it's full potential.

One thing to remember is that you will need to install the nvidia drivers each time you update the kernel, this caught me out a couple of times after doing a system update...

Hope this helps, and if you need any more info let me know.

Matt

---

### Post by SvenM on 2007-05-04
I hope I'm not hi-jacking by giving a reply here, but this has answered my question why the live CD wouldn't boot on my new system. I'm new to the whole linux thing, but willing to experiment (and want to get rid of my WinXP - WinVista dual boot, keeping Vista and replacing WinXP with Ubuntu)

My hardware:

Asus P5B motherboard
Intel 6600 Core 2 Duo
8800GTS 640mb grafics card
2 GB ram

Like the starter of this thread I couldn't get past an "error screen" (? hope I'm right as I'm new...) and had to reboot my system, tried different drive, but never tried the "safe mode". Will be testing it tonight!

---

### Post by DJMatty on 2007-05-04
Yeah, I could never get the normal graphics mode to work with my 8800gtx, I always had to use safe graphics mode (vesa) until I had the drivers installed. And the ones that come with ubuntu for nvidia just wouldn't work, so it was the 9755 version of the nvidia drivers that I ended up installing, following the steps in this article for a manual install:

[http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)

I think the alt-f2 issue I had was also due to the drivers as well, as now I can use alt-f2 to get a terminal window, rather than a black screen.

Matt

---

