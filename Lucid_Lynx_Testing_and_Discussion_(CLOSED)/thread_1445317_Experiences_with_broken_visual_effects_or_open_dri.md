---
title: "Experiences with broken visual effects or open driver for ATI Radeon?"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mortti on 2010-04-02
I've hand plenty of small problems with my ATI Radeon Xpress 200M with several Ubuntu versions. Now there's a new a bit irritating problem, which actually doesn't necessarily have to have something to do with the actual drivers or the ATI card but is merely a by-product:

When GUI starts, the visual effects are set to "none" causing that the topbars of every single windows are missing.

This problems is solved by changing value of the visual effects in layout settings to normal or even to full effects. When the new settings take place does also the topbars apper where they should.

Not only I have to do this manually every time after reboot as the layout settings cannot remember the setting (propably because they're set to safe mode in wait for new drivers for Lucid?) but the layout window have began to crash every time after the new settings have been selected.

I experienced quite similar problem in developement version of 9.04 or 9.10 but the bug with topbars came only when I tried to switch from no visual effects at all to normal ones. I would guess that this time, the bug has somethind to do with the new feature in Gnome, that shows the bars somewhat transparent when they're not active.

Similar experiences with ATI Radeon or some other closed or badly supported driver? Anyone?

---

### Post by clhsharky on 2010-04-02
HI mortti

I would report a bug with your hardware.

I do not have that chip, but do have 3 legacy ATI cards. 9800pro, X550, X1650 and have 8.04.3, 9.10, 10.04 with different combinations for testing and use. I have not experienced any of your problems on Radeon/Mesa drivers. Sorry no help here, there are newer drivers, kernels, patches out if your adventures.

Sharky

---

### Post by tophill on 2010-04-05
I started having the same problem, at about the same time, with Intel driver.  Visual effects setting boots to "none" each time, I can then change it manually, and that window freezes.  Machine runs fine, but I must repeat the process at each boot.

---

### Post by praveenmarkandu on 2010-04-05
i never had huge problems with my ATI HD4330 gpu on my laptop. there were some slightly annoying things on karmic such as 2D video tearing i both metacity (with compositing enabled) and also with compiz using ATIs catalyst driver

with lucid i have less problems. I am now using the open source Radeon driver. im happy to report compiz is smooth as hell which really surprised me. there is no video tearing anymore. however when i use metacity (compositing enabled) i get video tearing which is weird. might be a bug related to metacity.

---

### Post by Jasev on 2010-04-14
Hi all,

I'm experiencing exactly the same problem with a MacBookPro 5,5 and lucid with an NVidia card.

When I reset my computer, visual effects revert to 'none' and there are no titlebars on any window.

Have tried reinstalling video drivers to no avail (currently using the 'current-recommended' driver which is 195.xx I think).

Anyone managed to solve this? Not a deal breaker but certainly annoying.

J

---

### Post by krige on 2010-04-15
I am experiencing similar problems but not with ATI cards.

Further details are here:
[https://bugs.launchpad.net/ubuntu/+bug/563023](https://bugs.launchpad.net/ubuntu/+bug/563023)

---

### Post by Ric_NYC on 2010-04-15
Remove "fglrx".

It solved some issues I had with my ATI Radeon Xpress 1200.



Before I removed it:


Suspend or hibernate didn't work. 

Some games didn't start.

Etc.

---

### Post by JCoster on 2010-04-15
> **praveenmarkandu said:**
> i never had huge problems with my ATI HD4330 gpu on my laptop. there were some slightly annoying things on karmic such as 2D video tearing i both metacity (with compositing enabled) and also with compiz using ATIs catalyst driver

with lucid i have less problems. I am now using the open source Radeon driver. im happy to report compiz is smooth as hell which really surprised me. there is no video tearing anymore. however when i use metacity (compositing enabled) i get video tearing which is weird. might be a bug related to metacity.

+1 for all of that with an HD3650 running the radeon driver.  

For now I'm avoiding the fglrx driver until ATI get their act together.

---

### Post by krige on 2010-04-15
I fixed it by running "sudo apt-get install compiz".

Extra packages installed:
  compiz-gnome
Suggested packages:
  gnome-themes
NEW packages installed:
  compiz compiz-gnome

---

### Post by Killigrew on 2010-04-15
no titlebar = no windows manger -> open a terminal and type "compiz --replace" or "metacity --replace"
you can make a script on your desktop or an autostart entry till the bug is fixed :)

greetings

---

