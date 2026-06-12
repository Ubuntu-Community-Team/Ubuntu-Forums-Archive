---
title: "nvidia Fx5200 Cant boot?"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by dbelkie on 2007-09-18
hey all! I hope this is a acceptable question..... so here it goes..

I am trying to install MythTV (myth ubuntu) I have a nvidia FX 5200 video card. (DVI out)

Here is a point form of what I have done:
I try to use it, but it hangs during the install.
I switch to the onboard VGA, and do the install (thinking I can correct the problem after its installed)

I have followed the instructions on the howto's such as [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)
and
[http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php)

I think I am VERY close, but yet so far :)

Once I have done everything int he above docs, I reboot (but still use VGA) However my X server then fails to start a quick look at the /etc/X11/xorg.conf shows this:

(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:02:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:4:0) found
(EE) No devices detected.

Does anyone have any ideas or howto's to get this going? I am using 7.04

Thanks to all in advance!
-dan

---

### Post by dabl on 2007-09-18
Yep.

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

And then download and run the Envy script installer from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

:guitar:

---

### Post by dbelkie on 2007-09-18
Thanks for the details! I thought for sure it was going to work!

I have a few other questions that might help me get this fixed.

I run through your first instructions, and I got my x server working (however this is on my on board video, not my fx5200)

NO problem, I figure as soon as Envy is run through I will be able to disable my on board, and then use the FX5200 to boot, and possibly reconfigure X. However....

When I try to run Envy, it tells me that my operating system is not supported? I thought for use it was 7.04 I was using? Can someone tell me the ubunto command to find my release version? (I am used to Redhat / Fedora)

I look at my mythbuntu iso, and the file is: mythbuntu-7.10~070830-i386.iso. So it looks like 7.10?

Is there a tool like Envy for 7.10?

Thanks for all the help.
-dan

---

