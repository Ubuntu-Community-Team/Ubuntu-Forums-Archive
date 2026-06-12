---
title: "Failed to start the X server"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Relztrah on 2007-04-30
Well, I successfully downloaded and burned a CD of Ubuntu 7.04 so I'm making progress. But when I booted with the CD in my machine I get the following error messages:

**Failed to start the X server (your graphical interface). It is likely...**

When given the option to **Diagnose** I select **Yes**

I will only list the apparent errors which I believe are designated with (EE):

[B](EE) Unable to locate/open config file
(EE) open /dev/fb0: No such file or directory
(EE) I810(0) Given bpp (32) is not supported by i810 driver
(EE) Screen(s) found, but none have a usable configuration

Fatal server error: no screens found[/B]

The same thing happens if I boot to safe graphics mode. I am running an old Dell Optiplex with an Intel Celeron processor, 256MB of RAM. The video is on the mobo; there is no separate video card. I can stick a video card in there--an old one with only 4 or 8 MB of video RAM--if that will make a difference.

Any help will be greatly appreciated. I'll browse through the threads to see if another newbie has encountered this same problem.

I am committed to learning Linux and Ubuntu was the only distro I successfully burned a CD of, so I guess that makes me a Ubuntu user. I hope to learn the ropes here and hopefully help other novices in the future.

Relztrah

---

### Post by veloce on 2007-04-30
At the initial screen that gives boot options, hit the "vga" key ("F4"?) and select a video mode that will work with your hardware.  It appears to be trying to use 32 bit which may be beyond the capabilities of your machine.

---

