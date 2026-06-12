---
title: "GPU/APU Support on Precise"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by SteveHillier on 2012-07-31
Hi guys
I am looking to upgrade my hardware.
I am considering ASUS F1A75-M motherboard and AMD A6 3670K processor.
I want to run 2 graphics cards and four screens of this configuration.

Does anyone know any reason why this set up would not run 12.04?

Cheers
Steve

---

### Post by SteveHillier on 2012-08-13
Hi guys,
No body screemed 'Steve, Don't do it' So I did it.
I am still having some difficulty with the multi graphics cards.
I tried 2 x MSI R5450 cards which come with 1 x DVI-D and 1 x VGA port and no matter how I tried I could not get any output when I connected more than one monitor.  I did download and install the fglrx drivers and the Catalyst Centre (Thanks to QIII and [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) and at one time I could see both adapters but I simply could never see more than one monitor.

I have now used 2 x Sapphire HD5450 cards. which come with 1 x DVI-I and 1 x VGA port.  I have now been able to get more then one monitor working.

So far I have only used two monitors and have two monitors on one card and two monitors across two cards so I am looking hopeful.

When spread across the two cards the Cataylst Centre did not make a good job of picking up the second monitor but manually changing xorg.conf I was able to fix this.

I am now ready to attach more monitors and see how it goes.

I will report on progress.

---

