---
title: "Upgrade 10.04-&gt;10.10 - No display...not sure where to go from here"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by Chutler on 2010-10-27
Last night and this morning I attempted to update from 10.4 to 10.10 using the alternate CD.  Only step I took that was not default was not replacing GRUB.  I dual boot between Win7 and Ubuntu and didn't want to go through the GRUB modification again if I didn't have to.  The upgrade seemed to go without a hitch and I attempted a restart.  

I restarted from the 10.4 GUI and the machine rebooted to [an eggplant background with Ubuntu 10.10 in a system font]("http://launchpadlibrarian.net/57435662/PA100007.JPG") (skipped GRUB), "[end]" appeared on the page nad then my display went blank.  This isn't a black screen.  The display isn't getting any signal at all but the machine is still on and running.  I powered down, restart the box and arrived at the GRUB.  I chose the first Ubuntu entry, got the eggplant loading screen described above and again - no signal to the display.

Where to go from here?
[INDENT]**System Specs:**
Processor: AMD Phenom II X3 720
MB: Gigabyte MA770T-UD3P
RAM: 4GB DDR3-1333 Ripjaws
Video: Radeon HD4670
Optical: Samsung DVD Burner
HDD: SAMSUNG Spinpoint F3 HD103SJ 1TB 7200 RPM 32MB Cache SATA 3.0Gb
[/INDENT]

---

### Post by Fafler on 2010-10-27
Sound like a problem with your X server/ATI driver.
Can you boot in safe mode or whatever it's called? Then try reinstalling the ATI driver.
You can also do it through the console, but it's a bit more hassle. Ask if you need help with thet.

---

### Post by Chutler on 2010-10-27
> **Fafler said:**
> Sound like a problem with your X server/ATI driver.
Can you boot in safe mode or whatever it's called? Then try reinstalling the ATI driver.
You can also do it through the console, but it's a bit more hassle. Ask if you need help with thet.

I assume that 'recovery mode' is essentially Ubuntu safe mode, correct?

---

### Post by Fafler on 2010-10-28
Exactly ;-)

---

### Post by Chutler on 2010-10-28
Ta-Da.  Thank you that totally worked.  I thought I was battling a much bigger issue.

I logged in recovery mode, using the simple graphical interface and then searched for drivers.  The thrid-party ATI drivers were found and installed.  A restart later and I was in tip-top shape.  Thanks very much.

---

