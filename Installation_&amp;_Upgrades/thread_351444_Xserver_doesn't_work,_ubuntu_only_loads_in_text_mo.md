---
title: "Xserver doesn't work, ubuntu only loads in text mode"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by doublementh on 2007-02-01
I tried ubuntu in LiveCD mode, and OEM mode, and regular mode, and Xserver, the GUI, always fails to load, so everything is all text. There is no graphical anything.

I don't think I can install it again, as right now I have Windows Vista Home Premium, but why did it do that? It's not a bad burn, as I have one of those official Ubuntu DVD's of 6.10.

My specs, if needed:

Video Card: ATI Radeon X600
RAM: 1GB of DDR2 memory Dual-channel
Motherboard: Intel 945G (not sure, I need to know how to check for sure)
143 of 160 GB free on my HDD
Processor: Intel Pentium 4 Processor 3.0 GHz

Thanks in adavance.

---

### Post by doublementh on 2007-02-02
Bump. I've asked this question before, and I see that I'm pestering you guys.

---

### Post by riven0 on 2007-02-02
Have you tried a reconfiguration yet? 
If that doesn't work, how about [installing the ATI drivers]("http://ubuntuforums.org/showthread.php?t=204910&highlight=fglrx+install")? One or the other usually works for most.

---

### Post by doublementh on 2007-02-02
Thanks. Do I just put them in, or do I have to boot them?

EDIT: Also, can I delete Windows Vista and re-install it again if this doesn't work?

---

### Post by doublementh on 2007-02-05
The driver installer doesn't open in Windows, that's the problem.

I really want to make the move to Ubuntu.

---

### Post by Moulton on 2007-02-06
> **doublementh said:**
> Video Card: ATI Radeon X600
RAM: 1GB of DDR2 memory Dual-channel
Motherboard: Intel 945G (not sure, I need to know how to check for sure)
143 of 160 GB free on my HDD
Processor: Intel Pentium 4 Processor 3.0 GHz

I'm currently building a dual-boot/virtualization demo machine that is similar to what you have.  The one I'm working on has a new Intel D946GZIS motherboard, with onboard video, ethernet, and audio.

I had to use kernel boot options "acpi=off noapic" to boot at all.  The gNewSense distro had new enough video drivers to bring up the GUI.  The Ubuntu distros lacked the proper video drivers.  Neither of them had drivers that worked with the onboard ethernet, even though it's a PRO 10/100, which has been around a long time.  

Intel has a download site with driver kits.  You can navigate to your precise board model from this point, where I started...

[http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?](http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?) ProductID=2482&lang=eng

The kit did not include any drivers for the 10/100 ethernet chip, so that's still broken for me.

---

### Post by regard on 2007-02-18
hi I have got the sme motherboard, intel d946gzis everything is working fine. but I cant start the xserver then the whole xserver resets by itself

any ideas?

---

