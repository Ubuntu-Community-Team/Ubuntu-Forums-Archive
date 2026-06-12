---
title: "it hangs at LOADING ACPI devices..."
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by KARLZ on 2008-04-24
Hi! once my laptop was able to get into the live version of Ubuntu 7.04, but not anymore! I wonder what happened?!?! I need some help here!... (sad)  I have an Acer Aspire 5050 with 1GB on RAM and 64 bits processor, I guess is an Athlon... any ideas? there must be something on the preferences at time to run... I have try everything and now I'm desperate! thanks for your help!

---

### Post by KARLZ on 2008-04-24
any help?

---

### Post by cafe con leche on 2008-04-24
Hey,

When the CD initially loads, hit f6, this should show you a string (boot parameters) representation of each menu item. 

Highlight the "Install Ubuntu" option (if it already isn't) using your arrow keys, and then hit space (to add a space) and type in the following (it will be added to the end of the pre-existing line)

pci=noacpi

now hit enter.

If that still hangs, do the following except this time, instead of putting pci=noacpi, put pci=nomsi

If that fails, do the following:

Go through your BIOS (if you know how), and make sure that all your hardware shows up, and that no nonexistent hardware seems to be active, (like your BIOS telling you that you have a floppy drive even though you don't have one). 

If that doesn't work, try re-burning the cd at a slower speed and on a different cd or different drive (whatever is most possible). 

And finally, if that doesn't work, I'd try the alternate CD version of ubuntu, which can be found where you first downloaded ubuntu.

Someone else might have a more specific response to your specific problem, however I'm just telling you what MIGHT fix your problem followed by some general installation troubleshooting methodology. 

hope this helps!

---

### Post by Partyboi2 on 2008-04-24
Have you tried with some boot options like noacpi [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

