---
title: "Edgy install results in X failure"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by robmoore on 2006-10-30
I'm trying to install Edgy on a Dell Optiplex GX620 with a Radeon X600 and am running into a X startup failure after the inital splash screen (which displays fine). The X log has the error "no screens". I was initially using the DVI interface to my monitor but suspected it might be the problem, so I used the analog interface instead but the results were the same. I don't see any other mention of this in the forums so I thought I'd ask.

Thanks,

Rob

---

### Post by robmoore on 2006-10-30
Some additional detail from the logs (I've transcribed this so it's not exact):

Primary Device is PCI 01:00:0
Candidate "Device" section "ATI Technologies, Inc RV370 5B62 {Radeon X600 (PCIE)]"
ATI: PCI Mach64 in slot 1:0:0 could not be detected!
ATI: PCI Mach64 in slot 1:0:1 could not be detected!

Above I noticed there was a long list of supported devices. My card was listed but it had RV380 instead of RV370 -- not sure if that's significant.

---

### Post by wongk on 2006-11-21
X is attempting to load the wrong video driver.  Once you exit out of the error screen and are returned to the command prompt, enter the following "sudo vim /etc/X11/xorg.conf" (I am assuming you know how to use vim).  Change the "ati" driver to "radeon".  Exit and enter "startx".

See reference:
[http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/674910/an/0/page/0](http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/674910/an/0/page/0)

---

