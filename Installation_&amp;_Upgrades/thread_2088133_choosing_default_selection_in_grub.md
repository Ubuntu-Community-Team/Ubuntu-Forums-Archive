---
title: "choosing default selection in grub"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by ray field on 2012-11-25
Just installed Quantal a couple of days ago. Now on bootup, its grub entry is at the very bottom -- below 10.04 and 12.04, although at this point I would rather it boot by default.

I tried Grub Customizer but for my purposes it doesn't seem to work -- it's rather unwieldy, which I understand is the nature of the way grub2 works these days -- but it also didn't seem to render the menu as it looks, in fact I got so confused, I set grub-repair loose. Which is why I think 12.10 is last, since it's last in partition order. 

I'm less interested in changing the order of the menu as making sure, if I've stepped away from the PC upon reboot, that 12.10 is the one that is started.

---

### Post by darkod on 2012-11-25
If you have the grub2 from 12.10 booting the computer, it should be first on the list (unless you have changed the default settings). The OS which grub you are using to boot is always first in the default setup.

Now, regardless which grub you are running, you can control the default OS. But you need to know which grub you are running because you need to know where to edit it.

Here is what you can do for example:
1. Count the position of 12.10 in the grub boot menu.
2. Open the /etc/default/grub in the OS which grub you are using, and change the GRUB_DEFAULT value so that 12.10 is default. Note that it counts from 0, not from 1. So, for example, if 12.10 is 6th in the list, you need to make GRUB_DEFAULT=5.

After that run sudo update-grub to recreate the rub.cfg file and that should be it.

If 12.10 changes the position after a kernel update or similar, you will need to make changes too. But in the latest grub config, older kernels go under Previous Versions so that it doesn't move the entries below. If you are still using grub2 from 10.04 it might still work in the older way.

---

### Post by ray field on 2013-01-04
It's late for a reply, but first off, let me thank you for the help.

I am very uncomfortable messing with grub -- even Grub Customizer frightens me -- so although I have no doubt your advice was spot on, I decided to put up with the mild inconvenience.

However... just this morning I rebooted 12.04 on my netbook for the first time in several months, and applied 126MB of updates; on reboot, grub presented me with a bewildering array of choices, and grub-update didn't change anything. Having had a good experience with boot-repair in the past, I decided to see how it would cope: sure enough, it restored the netbook's grub to its previous 

My desktop was a different story -- I guess I had a residual old version of grub on my first HD -- incredibly (to me at any rate), boot-repair used popups to guide me through the process of deleting the old grub stuff from sda1 and once that was complete, reinstalling grub on BOTH my internal drives. The result is a beautiful, dhiny, and nicely simplified grub menu which now selects 12.10 by default.

Can't say enough great things about boot-repair.

---

