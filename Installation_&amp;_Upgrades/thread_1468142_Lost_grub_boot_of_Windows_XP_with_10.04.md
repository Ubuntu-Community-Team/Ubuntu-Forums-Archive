---
title: "Lost grub boot of Windows XP with 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Morganman on 2010-05-01
Hi
I have just updated to 10.04 on my Dell Insperon 8200 laptop, and all seems well with Linux.
My problem is that although it shows in Grub Windows XP will not load. I just get a blank screen with a flashing cursor.
I have tried to grub-mkconfig and grub-update, both of which reported successful results.
However on reboot I still get a blank screen for windows.
This was not an issue with 9.04 and 9.10.so I don't think it is the machine.
As I am still very much a learner can anybody suggest a solution?

Many Thanks

---

### Post by Ethangar on 2010-05-01
That makes two of us... Tried the same things that you did to. I can browse the drive so its all intact... Just seems like grub isn't handing off properly to whatever loads XP

---

### Post by gungrog on 2010-05-01
I had the same problem, this fixed things for me: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Ethangar on 2010-05-01
That fixed it for me. Thanks gungrog!

---

### Post by Morganman on 2010-05-01
Right on the button.
All faith (and system) restored.

Many Thanks Gungrog

---

### Post by Ethangar on 2010-05-01
And I'm betting that I know when it happened. To me anyway. When the GRUB2 install screen came up on updating.. I likely mangled something there.

Nice to have both options up and working again though. Man.. you don't realise just how slow XP boots until you have to go back to it from Ubuntu.

---

