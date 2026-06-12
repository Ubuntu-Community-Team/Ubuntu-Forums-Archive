---
title: "nVidia 96"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2012-05-28
Attempts to install nVidia-96 drivers in 12.04 LTS results in all sorts of broken package and other error messages only understandable to Ubuntu gurus.

What is solution?

John

---

### Post by wildmanne39 on 2012-05-28
Hi, I believe it is best to uninstall the nvidia driver and use the nouveau in 12.04 that is what I had to do with my older card.

Also install nouveau-firmware.
Thanks

---

### Post by cigtoxdoc on 2012-05-28
Thank you for your assitance, but the real problems is here:

E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the list directory

above is result of attempting to install nVidia 96 driver 

John

---

### Post by critin on 2012-05-28
> **cigtoxdoc said:**
> 

[QUOTE]E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the list directory

Attempts to install nVidia-96 drivers in 12.04 LTS results in all sorts  of broken package and other error messages only understandable to Ubuntu  gurus.

What is solution?

John



You might go to Synaptic Package Manager and click on Status.  Look at the bottom of the page and see if there are broken packages, etc.  Click on Edit at the top and choose Fix Broken Packages, dependencies, etc.

If you don't have Synaptic, you can install it with Software Manager.

---

### Post by wildmanne39 on 2012-05-28
Hi, I had the same problem with the 173 driver the issue is it does not work with the new xserver version, I still recommend the nouveau driver instead.
Thanks

---

### Post by critin on 2012-05-28
> **wildmanne39 said:**
> Hi, I had the same problem with the 173 driver the issue is it does not work with the new xserver version,[COLOR=Red]** I still recommend the nouveau driver **[/COLOR]instead.
Thanks

I agree--they always work for me.

---

### Post by cigtoxdoc on 2012-05-28
What should the xorg-conf file look like when the nouveau driver is correctly installed?  I am using a ViewSonic VA926g monitor with a native resolution of 1280 x 1024.  Should I be able to set refresh rate?

Thank you,

John

---

### Post by cigtoxdoc on 2012-05-28
I have attached a copy of my xorg.conf file.

If I change "nv" to "nouveau" in the Device section,
my PC will not boot correctly.  The only way out is to go to a login and change "nouveau" to "nv" using VI editor.

What do I need to do to make to nouveau driver work?

John

---

### Post by wildmanne39 on 2012-05-28
Hi, I checked and I do not have that file it is only created if you create it and it is not needed for nouveau.
Thanks

---

### Post by cigtoxdoc on 2012-05-28
Thank you for your post.  You are correct.  I deleted it and PC still runs.  However, the xorg web site mentions it.  Is there a correct way of writing it to give better control over monitor.  Monitor has correct resolution, but no idea of color depth or refresh rate.  Nouveau driver thinks my ViewSonic VA926g monitor is a laptop.

John

---

### Post by wildmanne39 on 2012-05-29
Hi, I do not know about color depth or refresh rate all I know is if the resolution is correct and it looks good I leave it alone more damage can be done by trying to fix something that is not broke then leaving it alone.
Thanks

---

### Post by TREESofRIGHTEOUSNESS on 2013-01-20
Hi, I use those same drivers.  Did you enable the proposed repos?  That is the only way to install the drivers correctly.  Otherwise there is some serious unmet dependencies.
The well known bug of dependency on a non-existent xorg-abi-somethingorother was fixed in the proposed for BOTH 96 and 173... however it seems 96 is not yet in Raring....

---

