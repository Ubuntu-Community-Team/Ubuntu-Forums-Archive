---
title: "Problem installing; seems to be GFX card. &quot;No devices detected&quot;"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by Subterranean on 2007-02-01
I downloaded the Ubuntu 6.10 cd iso, burned it fine, but have problems installing. It goes to the selection menu fine, but if I choose the main option, to run the live CD so I can install from there, it eventually gives me the error:
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"
If I select yes, I get the default log, and at the bottom it says:

"(EE) No devices detected
Fatal server error:
no screens found"

If I view the extended log, theres a lot of stuff there, but just above the No devices detected error, it says:

"(II)NV: driver for NVIDIA chipsets:
[long list of nVidia GFX card models]"

I have a geforce 8800 GTS, which is not listed in the long list, is this the problem? If I select the 'safe graphics mode' from the initial menu, I get to exactly the same point, but with a black screen instead of the error message, which doesnt carry on, and I have to reset.

Is there anyway to set the driver to some sort of default one? I noticed nVidia have a linux driver for the 8800 on their site, is there anyway to use this from the install CD?

Thanks for any help.

---

### Post by Kerry Lange on 2007-02-02
You're going through the same grief I am.  I've got the added benefit of having an Intel p965-based MB.  Not only is the install hanging because of the 8800 card, I can't install from the CD because of problems with the jmicron PATA controller chip.

After I solve my issues with the MB...

Some have told me they've been able to get Edgy running by fooling around with the command line; however, I'm not well versed in using the command line so I'm out of luck until I find some instructions.

I'll let you know if I get my system running & how it happened.

---

### Post by Kerry Lange on 2007-02-04
Well, I got Ubuntu Feisty working on my machine.  If you're interested, you can read about what worked for me near the end of the following thread:

[http://ubuntuforums.org/showthread.php?t=351205](http://ubuntuforums.org/showthread.php?t=351205)

---

