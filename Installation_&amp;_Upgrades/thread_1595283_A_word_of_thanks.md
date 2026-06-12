---
title: "A word of thanks"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by dargaud on 2010-10-13
Hello all,
well, yesterday I decided to replace the system dusk of my main PC and do clean install of 10.10 in the process as my system had gone through 6 Ubuntu upgrades, one mobo change, two video-card changes and two monitor changes since I originally installed it and it was beginner to show some problems.

So I sat down with lots of beer, pen and paper to write down potential problems and a wristwatch to time out the operation. For the system drive I decided to replace my old IDE drive with an SSD. From the first boot to the end of the install, it took 12 minutes, which was pretty fast. Then the reboot left me flabbergasted: between the blink at the end of the BIOS and the KDE password prompt, it took less than ONE second !!!

And I didn't have to mess with anything. Everything worked out of the box: webcam, USB3 card, graphics, fancy mouse, scanner... My expected night of hackery turned out to be boring backup restorations.

So kudos to the (K)ubuntu team.

---

### Post by leopoldb on 2010-10-13
Me too!
Older Gateway.  Invidia video card,2 monitors.  A clean install.
I had backed up all user files and simply copied them back.

A couple of hiccups
Changing ownership and perms.  Relatively easy
Scanner still doesn't work, a known problem (epson V500)
Latest Virtualbox doesn't work with USB, backing down a version fixed it.
New interface was lovely until the first automatic update and it changed and it doesn't look as nice - I need to resolve that.

But that's all small turds, the result is great and I add my thanks to Canonical and the Ubuntu community.

Paul N.

---

### Post by dargaud on 2010-10-13
> **leopoldb said:**
> Me too!
Older Gateway.  Invidia video card,2 monitors.  A clean install.
I had backed up all user files and simply copied them back.
A couple of hiccups
Changing ownership and perms.  Relatively easy

It's easier to make sure you've kept the same username and UID number in the /etc/passwd file. But sending a well crafted "find -uid 1234 -exec chmod newuser {} \;" works as well
> 
Scanner still doesn't work, a known problem (epson V500)

I have the same scanner, and although I haven't reinstalled it on this PC yet, I installed it on my parents' last WE (Ubuntu as well) and it was much faster than first time. Just 2 files to download off some japanese website (not Epson) and some instructions. I/they use Vuescan but I briefly tested in in xsane as well. Worked great.
> 
Latest Virtualbox doesn't work with USB, backing down a version fixed it.

Make sure you haven't installed the OSE version, it doesn't have USB.
> 
New interface was lovely until the first automatic update and it changed and it doesn't look as nice - I need to resolve that.

I you copied your old /home over the new one, it reverted some defaults. I had the same happen. Not sure how to solve that but that's not important in my book.
> 
But that's all small turds, the result is great and I add my thanks to Canonical and the Ubuntu community.

Yeah, I spent the day telling everyone about my boot time under one second, and they looked at me funny. It's not often that a computer amazes me after 30 years of using them daily.

---

