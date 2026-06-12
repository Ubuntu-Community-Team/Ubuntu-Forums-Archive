---
title: "Screen shows trash on setup"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by lcrespom@gmail.com on 2006-03-27
Hello...

I am installing Ubuntu into a Via Mini-ITX machine, the ML600 model.

I can boot from an external DVD-Reader and I get the nice initial screen that says "ubuntu", etc. Then it switches to text mode and starts detecting hardware.

Then, it switches to some other graphic/text mode, apparently white text on blue background, but this graphic mode does not display properly. The screen is totally unreadable and shows everything in zigzag... imagine that you switch on your PC when you are very drunk: that is what you would see.

Of course I cannot proceed from there. I have tried to press some keys and yes I see that the screen changes but can't see what is going on. If I press enter several times I think I get some red progress bar in the middle of the screen.

Is there a way to change the display mode of this setup?
Or should I just try another Linux distribution? If so, which one do you recommend me?

Thank you,

    Luis.

P.S., ehem, I think that I chose a bad user name. It is a good thing that gmail spam filter really works.

---

### Post by stuporglue on 2006-03-27
1) Can you try a different monitor? It could be the video card that isn't supporting the video mode, but last time I had this trouble, it was a goofy monitor. 

2) If that doesn't work, does your board have a PCI slot? Can you throw a PCI video card in there for the duration of the install?

---

### Post by luis31415 on 2006-03-28
(It's me again with a different username that does not show the e-mail)

I have a 17" TFT display, Acer, which I have been using with lots of different resolutions and with more than 3 different video cards, and has always worked fine.

My Via board is a ME6000 model, which, according to the Via website, has a "Integrated VIA Unichrome AGP graphics with MPEG-2 Accelerator" as the video adapter.

Regards,

    Luis.

---

### Post by luis31415 on 2006-03-29
Hello, it's me again with an update.

I started the installation on another PC and there I could read some startup message about the framebuffer just after switching to the problematic screen. So then I started the ubuntu installation again on my new PC, pressed F1 in the initial screen and saw some configuration parameter that allowed me to disable the frame buffer (something like debian-framebuffer=off, only longer).

This way I could go through the whole Ubuntu setup, until it switches to XWindows and graphics mode. Now what I get is a totally black screen... argh!

I can start in text mode but then I don't know how to configure XWindows while still in text mode. Any help will be appreciated.

I am quite sure that the video card or the monitor are not failing, as I have installed Windows and works fine, although when I check on the adapter information it says <unknown>, but I guess it is just a matter of installing the drivers that come with the motherboard CD. And still with the default installation I can get 1024x768 and 32-bit color.

I also tried Knoppix with exactly the same problem: everything works fine until it decides it is time to switch to XWindows, then I get a black screen and there is nothing I can do.

Apparently Windows is still better than Linux at video hardware support and at "playing safe" in order to let the user have some environment to begin working and install the very latest video driver support from there.

(Yes, I admit, the paragraph above is there to provoke you Linux fans and come with some helpful reply that refutes my statement).

I will spend a couple of hours every night to keep trying to install Linux on that computer. I still have Fedora and Suse 10 to try... but if by Sunday I still get a black screen, I will have to reinstall Windows XP (ugh).

Luis.

---

### Post by krolben on 2007-04-11
I'm sorry to bump this thread, but I'm experiencing the exact same problems. Has anyone found a solution to the issue?

I have successfully installed Ubuntu 6.10 Desktop on my Mini-itx system, but the issues happens when trying to install the server version.

---

