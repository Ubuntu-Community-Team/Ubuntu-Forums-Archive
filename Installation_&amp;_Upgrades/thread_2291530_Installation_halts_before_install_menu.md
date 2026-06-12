---
title: "Installation halts before install menu"
date: 2015-08-20
forum: Installation &amp; Upgrades
---

### Post by Chrille_Hedberg on 2015-08-20
Hi there!

I recently was given a computer by my father-in-law. It's an "a little bit of this and that"-desktop computer.
It has a fairly recent version of Windows installed. The installation of Windows was, surprisingly, without pain and loss of hair. Windows isn't really what I'm looking for though, so I thought I'd install Ubuntu 14.04.3 LTS desktop.

I downloaded 64-bit version. Booted from the DVD, got the purple screen, the "five dots"-countdown - and then it thappens, from left to right: vertical lines starting with a black background with alot of small green dots, continuing with black background with not so many small green dots, going to a white background with pink dots and a white background with alot of pink dots. This times 2,5. Also, the computer seems to halt. Num lock/caps lock won't react, pressing any keys won't change anything/do anything.

"Well... Odd. Windows could install, and if Windows have graphics drivers Ubuntu should have it too." I am thinking graphics driver because the screen looks a lot like the "I'm about to receive a signal from E.T. and it will pop up any second"-thing that always are on computer monitors in bad Hollywood-movies.

Then I downloaded 15.04, burned a new DVD and verified it - just to be on the safe side. It felt like it could load longer, but end result is the same.

Cursing starts.

"Is it something about using 64-bit version? Can't be. Gotta try!"

Downloaded 14.04.3 32-bit version. Result more similar the 15.04-try than 14.04.3 64-bit try.

I've been at this for too long now. I've googled my behind off and, to be honest, I'm getting too many hits. "Problems installing Ubuntu", "vertical lines during ubuntu install" and a lot of other key words have given me a lot to read, but nothing that is substatial to solving my problem.

I did read somewhere someone pressing the shift-key when the boot from DVD started, continuing with pressing E-key to get a prompt and entering nomodeset.
Also read something about > Windows 8.x has some feature for not "accidentally" installing another OS. UEFI? Can't find any such settings in my BIOS that the FAQ referred to.

I would really appreciate any pointers on solving this.

Kind regards

Chris

---

### Post by oldfred on 2015-08-20
What video card/chip does system have?
If nVidia or AMD you often need the nomodeset boot parameter to get into lower quality graphics until you can install inside your working install the vendor driver from System Settings, Software & Updates, driver tab.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Chrille_Hedberg on 2015-08-22
Thank you so much, oldfred!

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

This was what I needed! Found the boot menu, pressed F6 and selected NOMODESET and it worked at first try.

---

