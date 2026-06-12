---
title: "Another Ubuntu Nvidia Install Failure"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by Tim_Olaguna on 2006-12-08
I have an HP Pavilion 514n which uses a 82845G/GL[Brookdale-G]/GE Chipset by Intel as its default graphics supplier.  I recently installed an Nvidia GeForce FX 5200 graphics card to get better graphics (yes, I know there are better cards out there but this old PC only has a PCI bus, so an older PCI-based card is required).

The Nvidia card works well when I boot up Windows XP (using an older 77.77 Nvidia driver) or Fedora Core 6.  But Ubuntu or Kubuntu both seem to ignore it.  They only seem to see the 82845G/GL[Brookdale-G]/GE Chipset.  It's the only option offered when I try to configure xserver-xorg.  If I enter anything else I end up with no GUI.  Yes, I have downloaded and installed the various Nvidia drivers.

I believe the problem lies with Ubuntu/Kubuntu not recognizing the Nvidia card at all.  Am I right in assuming the "BusID" setting in xorg.conf should be used to identify the location of the card? 

When using the xserver-xorg configuration script the default entry for BusID is "PCI:0:2:0".  But that entry just results in Ubuntu/Kubuntu using the inferior Intel chipset.  

Windows XP tells me the following about my Nvidia card; "Nvidia GeForce FX 5200, PCI Slot 2 (PCI Bus 2, device 10, function 0 [that's a zero])".  How should I translate that information into a correct BusID setting?

---

### Post by taurus on 2006-12-08
[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by brt on 2006-12-08
use "lspci" on commandline to find out the correct BusID for your graphics adapter in linux and place it to your xorg.conf. you will also have to change the driver to "nv". if it doent work, look out for some "nvidia howto", there are plenty of them...

---

### Post by Tim_Olaguna on 2006-12-08
> **taurus said:**
> [http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

No, I tried following that guidance last night.  It did not work.  I received numerous errors about all kinds of irrelevant things.  I'm running 6.06 because it seems to offer more flexibility with other system things.  Like being able to choose my preferred KDE over Gnome.

I really need to know how to specify and/or use the BusID setting; which that article does not seem to address at all.

---

### Post by Tim_Olaguna on 2006-12-08
> **brt said:**
> use "lspci" on commandline to find out the correct BusID for your graphics adapter in linux and place it to your xorg.conf. you will also have to change the driver to "nv". if it doent work, look out for some "nvidia howto", there are plenty of them...

Thanks, brt.

The report tells me "0000:02:0a.0" then goes on to describe it as a VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1).

Do you have any idea how I should translate that into the requested format setting "PCI:#:#:#"?

Thanks so much for giving me a good technical tip.

---

### Post by Tim_Olaguna on 2006-12-08
I GOT IT FIXED!!

The secret was to do the following:

- Edit xorg.conf.
- Replace 'nv' with 'nvidia'
- Make sure 'BusID' is set to 'PCI:0:2:0'
- Exit the editor after saving the file.
- Type/Enter > aptitude install nvidia-glx (I was running in recovery mode so 'sudo' was unnecessary)
- Type/Enter > nvidia-xconfig --no-composite
- Type/Enter > startx
- If all goes well (as it did for me), celebrate briefly.
- Then logout and reboot.

---

### Post by brt on 2006-12-10
great!

you may also have a look to the following howto's:

[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2)

---

