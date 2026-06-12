---
title: "Ubuntu 11.04 On A Thinkpad W500"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by crokett on 2011-08-13
I am trying to get a test drive running on a W500 laptop.  I had issues with modprobe at boot but found a fix by turning off ACPI.  The boot gets further but still hangs. I see messages about USB devices that couldn't be inserted at a particular device ID. Any suggestions?  Since this is a test drive I don't think I can log anything.

---

### Post by steve11911 on 2011-08-15
Live cd's offer the chance to test compatibility before taking the full install plunge.Assuming the install media your using is good I'd recommend switching to 10.04. A successful Lucid install on your hardware is detailed on the page linked below:

[http://www.dehora.net/journal/2010/06/19/ubuntu-lucid-1004-on-thinkpad-w500/](http://www.dehora.net/journal/2010/06/19/ubuntu-lucid-1004-on-thinkpad-w500/)

A resource page worth having specific to your hardware:

[http://www.thinkwiki.org/wiki/Category:W500](http://www.thinkwiki.org/wiki/Category:W500)

---

### Post by crokett on 2011-08-15
Thanks, that is pretty much the conclusion I came to.  The live CD works on another system I have.  Fedora 14 works on the W500 but it uses a different kernel. I thought about trying Fedora 15 or 16 that use the same kernel as 11.04 just to see what happens.

---

### Post by crokett on 2011-08-16
Ok after some searching I found this.  I tried it and it fixed both the modprobe and the USB issues with 11.04  As far as I can tell this is only an issue with the Thinkpads with ATI Radeon chipsets.  The W510 has an nVidia and does not have this issue.

```


Hit F1 once you see the Thinkpad screen come up, to bring you into the Bios

From the main BIOS Setup Utility screen, the cursor should default to "Config", hit enter

Use the down arrows to select "Display*, then hit Enter

Move down to "Graphics Device" by pressing the down arrow twice

Hit enter to change the default " Switchable Graphics". 
The other options are "Integrated Graphics" (INTEL) and "Discrete Graphics" (ATI). 
We suggest you change to "Integrated Graphics" by pressing the up arrow twice, 
and enter,so the system uses Intel for all power modes. You must move away from
 switchable graphics due to lack of driver support on Linux.

The default factory setting had it on "Switchable Graphics", which uses Discrete for maximum 
performance and Integrated for battery-savings - only if you have Vista and Lenovo's PowerManager utility and video drivers

Move down to "OS Detection for Switchable Graphics" by using the down arrow once.
 Then press enter to change the default setting of "Enabled", then the up arrow to "Disabled", 
and enter to save that setting.  If you do not do this the BIOS will revert to "Switchable" every time you reboot.

Select PF10 to "Save and Exit", and enter on Yes to "save configuration changes and exit now?"

```

---

