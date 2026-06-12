---
title: "Installer freezes after selecting time zone"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by discostoo on 2010-05-08
Attempting to install 10.04... I can get to the "Where are you?" screen, then the little circular "please wait" cursor spins forever and ever.

Here are a few things I've tried, with no success:
[LIST]
[*]Leaving it alone for hours, hoping it was just taking a really long time. No Dice.
[*]Unplugging any hardware that might be causing a problem, including the network card. No dice.
[*]Burning it to CD, DVD, and booting from a USB key. No dice.
[*]Trying every combination of kernel options I could find in the forums, and setting most combinations found in the "more options" menu in the boot screen. No dice.
[*]Booting into the live environment, then installing from there (instead of just choosing "install" directly). No Dice.
[*]Booting both from the 32-bit and 64-bit ISOs (my machine is 64-bit)
[/LIST]

Does anybody have any idea what could possibly be causing this?

Note: I have not tried just upgrading from my 9.10 install, and I will not try this. If I can't get a live CD to boot, there's no way I would voluntarily hose my current system by upgrading.

Also note: I checked the MD5 of the ISO, and did the "check the disk for defects" menu option as well. Everything checks out fine.

---

### Post by mörgæs on 2010-05-08
Good to see that you are trying several different attempts. If only everybody in here would do that...

Maybe best is to stick to 9.10, plain and simple. There are still some combinations of hardware which are not liked by 10.04.

---

### Post by discostoo on 2010-05-08
I just tried Kubuntu, by the way, and had the same result. I'm tempted to try the text-based installer. Seems totally weird to me that my basic, simple, totally common PC that works with every other distro and OS would just not work with 10.04.

---

### Post by mörgæs on 2010-05-09
Yes, a text-based install will be a good idea. Let us hear if it fixes the problem.

---

### Post by discostoo on 2010-05-31
I just thought I'd bump this now that it's been a month or so since the release. Does anybody have any idea how I might be able to get around this? Or even what the problem might be?

---

### Post by volka_lynx on 2010-06-29
For me it worked to switch the SATA Mode to IDE Mode (was AHCI Mode) in my BIOS settings
You can try to run the installation with acpi=off either. To do that 
hit Shift during boot, and select via F6 (further options)

---

