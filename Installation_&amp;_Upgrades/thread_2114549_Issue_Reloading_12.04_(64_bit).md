---
title: "Issue Reloading 12.04 (64 bit)"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by farlander762 on 2013-02-10
I am having trouble reloading 12.04 on my computer.  I am trying to do this because of some of the things left over from the previous 11.(whatever) I was using.  There is nothing really wrong just some left over annoyances.  I tried to do a complete wipe/reinstall when I migrated to 12.04 but was forced to do the Update Manager version because of this same problem.  I just gave up that time.

Using either a USB stick or a burned CD the result is the same.  I reloaded my daughter's computer yesterday from this same USB stick without incident.  I formatted the stick in Ubuntu on this machine.  I installed ubuntu on this machine when I bought it almost 2 years ago and don't recall having any issues.  I try to stick to the LTS versions now, some of the others have given me isues and 6 months is far too frequent to upgrade the OS for my taste.

I have tried some of the selectable menu modes and the result is the same.  During startup, it goes to a purple screen with an icon of what appears to be a keyboard next to an icon of a man in a circle.  Next it goes to a black screen and appears to be loading services to memory addresses.  When it gets to the bottom of a screen worth of these it stops and sits there until I turn the machine off.  

Machine Specs:
HP Pavilion Elite HPE-590t
Intel X58 Express Chipset
Intel Core i7-970
9GB DDR3-1066MHz SDRAM
nVidia GeForce GT 420

Any ideas?  Ubuntu is our primary OS.

---

### Post by U202E on 2013-02-10
when you see that man+keyboard scary screen just press enter...
it worked for me :), then it will continue to load the things you need.

---

### Post by darkod on 2013-02-10
With nvidia you might need to use nomodeset parameter to boot into live mode and start the install, and then on first boot also until you can boot once and activate the driver.
[www.ubuntuforums.org/showpost.php?p=10069997&postcount=1](www.ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

