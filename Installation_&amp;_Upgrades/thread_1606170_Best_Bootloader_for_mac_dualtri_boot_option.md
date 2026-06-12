---
title: "Best Bootloader for mac dual/tri boot option?"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by rashhashan on 2010-10-26
Just looking for advice...I've been doing some homework myself and i found this ([http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)) but i wanted to hear what you guys think. I have also had experience with rEFIt...but i didn't like how grub would force to install as well so if i wanted to boot into linux i would have to go through rEFIt(which btw has a very pleasing, simple interface) to  grub..which is bland on a shiny mac.

So tell me what you guys think or have done and why! Thanks!

~Rash


**Also, I wanted to mention that i have a 13.3" Macbook with 2gigs of ram and a 2.4GHz Core2Duo...should i install full blown ubuntu or the netbook version? I've kind of been itching to try it out

---

### Post by rashhashan on 2010-10-26
bump...this is sort of a pressing matter..sorry to annoyingly bump

---

### Post by srs5694 on 2010-10-26
Yaboot and rEFIt are used on entirely different systems; Yaboot is for older PowerPC-based Macs, whereas rEFIt is used on newer Intel EFI-based systems. AFAIK, you'll never have a choice of which one to use; at most one will be suitable.

I'm not positive, but I believe that rEFIt isn't enough to boot Linux; you'll need a secondary boot loader, such as GRUB 2 or eLILO, to finish the job.

---

