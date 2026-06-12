---
title: "Installing Ubuntu on Laptop without Batteries fails"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by mupi_foerster on 2012-10-09
I recently received an old laptop from a friend which I want to use for my kids. The battery was thrown away because it did not work anymore. However, I plan to use it connected to power all the times.

Problem: When installing Precise (FYI it is a 64bit alternate CD I am using), at some point during software installation, the laptop switches itself off. Needless to say the installation is not runnable afterwards.

My theory is that at some point the installer is doing a battery test or something similar. Without a battery being there, the laptop just turns off. This happens as well in expert mode, I couldn't find an option to change that behavior.

So here my questions:
- Is there really a battery test happening and causes my problem?
- If Yes, it there a way to avoid that test e.g. by telling the installer this is kind of a PC and not a laptop?

Thanks for your help

---

### Post by mupi_foerster on 2012-11-04
No ideas? :(

---

### Post by spideryada on 2012-11-04
You say that it is an old laptop. Are you sure it is 64 bit?

---

### Post by mupi_foerster on 2012-11-05
> **spideryada said:**
> You say that it is an old laptop. Are you sure it is 64 bit?

A valid point - although it is not that old, its a Lenovo N500 bought in 2008.

Anyway I just tested again with Ubuntu 12.04.1 i386 Live CD. The Live System starts without problem, then installation prompts for all the details, but later on, during "installing the system", like with the alternate installer, it switches itself off.

Really annoying, as the hardware seems great to run Ubuntu on it.

How can I tell the installer there is no battery? :confused:

---

### Post by coldraven on 2012-11-05
You will probably save a lot of time if you just buy a battery for it. I've just checked on ebay, you can get one for £15, deduct it from the kid's pocket money :)

---

### Post by Linux_junkie on 2012-11-05
How secure is the power cable?  As the laptop has no battery it is relying on an AC supply being present all the time, should the power cable become loose there will be no power and the laptop will switch off.

Also just because the laptop was made in 2008 does not mean that it uses 64 bit architecture.  It is possible to install software compiled for 64 bit pc's on a 32 bit pc but you will probably get issues sometime.

But it could also be the type of hardware installed that is causing the problem.  I have a Dell Inspiron 6400 that I have never had a problem installing any of the *buntu's on but others have had issues installing on other makes of laptop.  Not all laptops are created equal.

First of all I would check that the power cable is seated securely and also buy another (cheaper model) battery for that laptop.

---

### Post by mupi_foerster on 2012-11-05
> **Linux_junkie said:**
> How secure is the power cable?  As the laptop has no battery it is relying on an AC supply being present all the time, should the power cable become loose there will be no power and the laptop will switch off.

Also just because the laptop was made in 2008 does not mean that it uses 64 bit architecture.  It is possible to install software compiled for 64 bit pc's on a 32 bit pc but you will probably get issues sometime.

But it could also be the type of hardware installed that is causing the problem.  I have a Dell Inspiron 6400 that I have never had a problem installing any of the *buntu's on but others have had issues installing on other makes of laptop.  Not all laptops are created equal.

First of all I would check that the power cable is seated securely and also buy another (cheaper model) battery for that laptop.

Thanks for the input. As I have mentioned above, prompted by spideryada, I tried now as well with an **i386** Precise CD - same result.
Naturally, the laptop is dependent on (uninterrupted) AC Power - just like a Desktop PC is as well. The cable is well, and I'm sure it is not a problem with the power supply - the installation reproducibly powers off the system at the same point.
As to the hardware, the live system is  running without any problems.
I tried to find a BIOS setting regarding the battery (something must tell the installer that this is a system with a battery, after all), but failed to find one.

Buying a new battery seems a sensible idea, but I won't be able to do that for months as I am sitting in a developing country, sending parcels overseas is difficult and I'm not sure i can find one locally...and anyway, I would only use it for installation.

I hoped I could find some switch to tell the installer to ignore all battery-related installation steps.

---

### Post by coldraven on 2012-11-06
>  I am sitting in a developing country, 
Could it be spikes or fluctuations in the AC power that causes this?
Without the battery even a brief loss of power will switch off the laptop.
Can you try doing the install somewhere where there is a UPS?

---

### Post by varunendra on 2012-11-07
Since Ubuntu (and Linux in general) can adapt itself to hardware change, you may try clonezilla to restore a preinstalled system image on a pre-allocated partition of the laptop. No hardware probing (beyond running clonezilla live) = no problems ! (at least not during 'restoration').

You may create this image on a different system or on a virtual machine. Just make sure the source partition, which you are creating the image of, is either equal or smaller than the target partition on the laptop, else the restoration will fail (limitation of clonezilla).

A bit lengthy, but easy and more promising way to go, especially when we are not sure if the problem is indeed the battery or something else.

---

### Post by mupi_foerster on 2012-11-12
> **varunendra said:**
> Since Ubuntu (and Linux in general) can adapt itself to hardware change, you may try clonezilla to restore a preinstalled system image on a pre-allocated partition of the laptop. No hardware probing (beyond running clonezilla live) = no problems ! (at least not during 'restoration').

You may create this image on a different system or on a virtual machine. Just make sure the source partition, which you are creating the image of, is either equal or smaller than the target partition on the laptop, else the restoration will fail (limitation of clonezilla).

A bit lengthy, but easy and more promising way to go, especially when we are not sure if the problem is indeed the battery or something else.

Thanks, a great idea! will test that soon and write about the result.

---

### Post by mupi_foerster on 2012-11-12
Problem solved!

- Installed precise amd64 in a virtual machine with almost the same HD size as my old Laptop.
- used cloneZilla iso and a memory stick to get an image from the virtual machine
- used cloneZilla CD and memory stick to put the image onto the laptop

=> Laptop is fully functional. After startup, the battery symbol is shown only for a short time, when I hover the mouse over it, it says: battery not present. Otherwise no problem whatsoever.

I still think it would be good to have an option to override the battery check in the installer, at least in expert mode.

Thanks, **varunendra,**that worked like a charme!

---

### Post by varunendra on 2012-11-12
Great job ! And you are most welcome :)

Portability was the "first" reason (and perhaps availability of tools like remastersys the final..) why I embraced linux. So flexible, so many ways to solve or at least get around a problem..

> **mupi_foerster said:**
> I still think it would be good to have an option to override the battery check in the installer, at least in expert mode.
No doubt ^. No matter how promising, it's just a 'workaround' nonetheless..

But who knows if such an option is already available, just obscured from our non-expert eyes (for good, maybe?). A solution gets highlighted only if the pertaining problems become common.. While I say this, I have the 'acpi' related boot options in mind..
More at Community Documentation page : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Some great explanations by P4man : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Now that you know a definite workaround to your problem, you may safely try them and enlighten us with your valuable feedback, if you wish and have the 'extra' time. After all, this is how this wonderful thing has evolved and developed to its current form !

Hope you'd enjoy your first 'hard-earned' installation :)
Regards.

---

