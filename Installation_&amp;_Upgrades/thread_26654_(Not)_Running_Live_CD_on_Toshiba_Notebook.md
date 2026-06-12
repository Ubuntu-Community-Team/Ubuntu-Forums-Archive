---
title: "(Not) Running Live CD on Toshiba Notebook"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by WiFi Net Guy on 2005-04-13
Hi. I have a Toshiba Satellite A75 notebook PC that I am trying to run the Live CD (5.04) on. I boot from the CD, get to the boot screen where I'm supposed to either enter in a boot: command or simply hit <enter> to boot the CD. After I hit <enter> I see some text run by where some commands are being run and then it simply goes blank. No disk activity no screen activity, nothing.

I know this isn't much info but it's all I have. I'm pretty much a newbie on Linux (currently run SuSE on this Toshiba in dual-boot) and don't really know what to do next.

Thanks in advance...
Alvin

---

### Post by nuke on 2005-04-13
I have had some experience with a Toshiba Satelite laptop and found that Toshiba isn't always the easiest to run Linux on.  But that doesn't help you.

Here is some stuff that I used to get the Satelite to run.  Try the following:
1) follow what text goes onto the screen just before it goes blank.  Maybe this will provide us with some more info to help.  Post it back here.
2) try to run Knoppix, Mepis or Libranet as a live CD and see if it boots OK.  If so, check out what hardware options it selected.  Maybe Ubuntu isn't finding the right hardware.
3) check if there is a boot option on Ubuntu to set screen to VESA which might help if the screen driver isn't being recognized.
4) The biggest problem I had with my Toshiba was with the PCMCIA drivers and the IRQ set-ups.  For what ever reason, the Yenta Socket (which was the correct one for my Satelite) was not getting selected and the IRQ that the BIOS indicated was not what Linux was selecting.  The conflict between the two IRQs caused the hang.  So see if the text on the screen shows the PCMCIA prior to hanging.  If there is, do a search on the Knoppix board where I posted a solution to the IRQ/PCMCIA issue.

Hope this helps.
Nuke

---

### Post by catvader on 2005-07-27
Hi, I´m kind of having same problem, can u tell me please where to get those aplications live cds?
Thanks a lot

---

