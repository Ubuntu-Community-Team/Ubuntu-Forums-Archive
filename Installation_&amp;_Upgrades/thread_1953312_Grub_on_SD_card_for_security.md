---
title: "Grub on SD card for security"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by Sinderan on 2012-04-06
I am interested in using a small (512MB) SD card that I had wasting away in a drawer to install Grub (or preferably Burg) to act as almost a key to my laptop. Literally have no bootloader on the laptop at all so it cannot boot. Then have Grub on the SD card so when I plug it in it boots to the SD card install of Grub and lets you boot into Win7 or Ubuntu, etc. installed on the Hard drive. I have issues with people getting on my laptop and messing with things and I was interested in this, if only as a proof of concept.
Sorry if this has already been discussed I couldn't find anything with search. Thanks

---

### Post by Paddy Landau on 2012-04-06
Moving the bootloader to a USB key would stop only the most lazy person. It will not stop people from accessing your hard drive, say with a Live USB.

I would suggest instead that you ensure you have a good password so people cannot sign on, having booted. If your BIOS supports it (and it should), also add a boot password, so people cannot boot without the password. That way you are not dependent on a USB stick.

To really protect your data against messing around, have an encrypted home folder, as even a BIOS password can be easily bypassed. You can go to the extreme of encrypting your entire hard drive with something like TrueCrypt, but that is probably overboard in your case.

---

