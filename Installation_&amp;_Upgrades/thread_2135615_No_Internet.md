---
title: "No Internet"
date: 2013-04-14
forum: Installation &amp; Upgrades
---

### Post by sgmdmz on 2013-04-14
I had Ubuntu 11.10 on my Dell Inspirion laptop top and everything worked GREAT (Note: I did a complete install getting rid of everything else on the hard drive)!  I then upgraded to 12.04 and I would have to occasionally reboot after the initial start-up to have access to the internet.  I have now installed Ubuntu 12.10 and I have NO access at all to the internet.

I have tried to look at everything and am at a loss.  If someone could please help me I would be very, very appreciative.

Thank you,
          Dave Zehner:o

---

### Post by darkod on 2013-04-15
You didn't provide much detail, but i guess you are talking about wi-fi access. Sometimes you will need a driver (or the correct driver) to make wi-fi work.

You can find out the chipset (which might be different from the manufacturer) by executing in terminal:
[code[lspci[/code]

That will list all PCI devices and usually the wi-fi card is one of them. Note the model down, also the codes for the manufacturer and model which are in format xxxx : xxxx and google how to make it work in ubuntu 12.10.

You can also post a new thread in the Networking subforum stating the exact model of the card, someone might have an idea.

---

