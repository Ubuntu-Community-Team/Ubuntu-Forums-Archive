---
title: "random issues from upgrade"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by oldmanstan on 2005-10-15
I just upgraded from hoary to breezy using synaptic.  The upgrade errored on the first attempt, so I repeated the process and it seemed to get farther along each time, took a total of about 4 times doing "upgrade all" in synaptic before it finally got all the necessary packages installed.

Then the x server wouldn't start, I figured that it was probably because of my nvidia drivers so I switched back to a non-nvidia xorg.conf file, that worked, now gnome comes up, etc.

Only a couple annoying issues that might be signs of bigger issues... lilo sees 2 different linux kernels now, is that right? I mean, I know breezy is different, but shouldn't it have overwritten the old stuff?

Also, my trash can, minimize all windows and some random other icons dont work now, just a page with a red X on it for those, weird.

Any suggestions?  I'm thinking about maybe just backing up /home and doing a fresh install from a breezy iso image, thoughts from someone who knows what they're talking about a little better than me?

---

### Post by Redindian on 2005-10-15
Only a couple annoying issues that might be signs of bigger issues... lilo sees 2 different linux kernels now, is that right? I mean, I know breezy is different, but shouldn't it have overwritten the old stuff?

***For GRUB, delete the old kernel from /boot/grub/menu.lst. i dont know for LILO**.*


Also, my trash can, minimize all windows and some random other icons dont work now, just a page with a red X on it for those, weird.

***Change the theme and reboot. It worked for me.***

---

