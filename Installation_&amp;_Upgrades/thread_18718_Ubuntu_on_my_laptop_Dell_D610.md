---
title: "Ubuntu on my laptop: Dell D610"
date: 2005-03-08
forum: Installation &amp; Upgrades
---

### Post by Adagyo on 2005-03-08
Hi all, sorry for my bad english (i'm french!)
I have a BIG problem... My previous laptop was the D600 and there was no problem installing and compiling kernels on it.

But on that one, the hard drive isn't detected by the installer... I try a lot of things... But it doesn't work.

I install the Debian Woody with it's 2.4.18 kernel... It work fine but I have no network!!! (drivers for the broadcom bcm57xx isn't provided by this kernel).
I TRY to install the Debian Sarge (testing) with the 2.6.8 kernel... And this is the same problem: No hard drive!!!!!!!

Please.... Help ME!!!!! I get crazy!!!!!  [-o<  [-o<  [-o<  [-o<

---

### Post by Adagyo on 2005-03-09
Nobody has a solution??? Plzzzzzz help me [-o<  [-o<  [-o<  [-o<  [-o<

---

### Post by eternity on 2005-03-09
[QUOTE=Adagyo]Hi all, sorry for my bad english (i'm french!)
I have a BIG problem... My previous laptop was the D600 and there was no problem installing and compiling kernels on it.

But on that one, the hard drive isn't detected by the installer... I try a lot of things... But it doesn't work.

I install the Debian Woody with it's 2.4.18 kernel... It work fine but I have no network!!! (drivers for the broadcom bcm57xx isn't provided by this kernel).
I TRY to install the Debian Sarge (testing) with the 2.6.8 kernel... And this is the same problem: No hard drive!!!!!!!
[/QUOTE]

This is a known problem. D610 uses SATA and Warty don't include drivers for SATA (atleast not by default) and therefor it doesn't work. You can either download Hoary preview release or wait for the final release (a month).

I have th D610 myself and use Hoary array 6 and it worked right out of the box.

---

### Post by evisboy on 2005-03-11
I am trying to use the Hoary preview live cd, and the cd will not detect my Dell Lat. D610's DVD/CD Burner Combo drive. 

I want to make sure that everything will work before I attempt an install with the Hoary preview. 

Did you have any expereience like this?

---

### Post by lyly on 2005-03-11
Hoary array 5 does not support the D610 CDROM detection. I had the same problem with a D610. Try array 6 live CD or daily build installation, both worked for me  :grin: 

Lynda

---

