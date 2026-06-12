---
title: "Booting from live USB freezes when menu item clicked"
date: 2015-04-29
forum: Installation &amp; Upgrades
---

### Post by ParthianShotgun on 2015-04-29
So I was trying to reinvigorate my much older brothers laptop (a dell latitude d600) and it freezes when I run the usb. This is what pops up, as expected ([http://i.imgur.com/5CbreP5.jpg](http://i.imgur.com/5CbreP5.jpg)). But when I clicked any of the options, it froze and then showed a weird corrupted line on the top edge (seen here, [http://i.imgur.com/FpspNyF.jpg](http://i.imgur.com/FpspNyF.jpg)). I tried it on 2 different usb's and even tried Elementary OS, but the result was the exact same. My boot settings were fine, but the laptop completely freezes. I was wondering how I would be able to fix this. The laptop is in stock condition.

---

### Post by RobGoss on 2015-04-29
What are the specs for the machine in question. Sounds like it may not have enough ram to Handel the distribution you're trying to install.

---

### Post by ParthianShotgun on 2015-04-29
It is running Windows XP 2002 Service Pack 3 with Intel Pentium M [1600 mHz] clocked at 1.59 gHz. And it is fitted with 1.25 GB of ram (which is ideal, I would imagine, for Lubuntu). Thank you for the prompt reply, I really am at a loss as to why it would not work.

---

### Post by RobGoss on 2015-04-29
Yes you're correct Lubuntu is a lighter version and should perform much better being your machine does not have a lot or ram. Creating a bootable usb is also important. Do you have another computer on hand that you can see if that usb will boot from?

When I create a Ubuntu usb If for any reason it does not boot up on the machine I'm working on I will then see if it boots up from another machine to help me determine what might me causing the problem.

---

### Post by sammiev on 2015-04-29
Hi,

You can try F6 from the main menu and select nomodset.

If I recall correctly that model may have a ATI Mobility Radeon 9000 graphic card.

---

### Post by kerry_s on 2015-04-29
use the "nomodeset" option, you have a graphics glitch.

---

