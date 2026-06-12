---
title: "Live CD will not boot - Video card problem?"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by slockton on 2007-12-13
Hi,

I posted this in the "Absolute Beginner" forum, but it got very quiet very quickly, so I'm summarising the thread in this one post in order to get some more specialised help.

I have an old(ish) HP with a P4 1.8, 1 gig RAM and a 160 Gb PATA hard drive. I recently decided to turn this into a little music server/MythTV box.

I got a old(ish) PNY GeForce4 MX 4000 card (has s-video out) and slapped it in a PCI slot (yes it's PCI, not AGP :)) and attempted a fresh install of Ubuntu 7.10 using the bog-standard live CD. It freezes at exactly the same point each time during the load of the live desktop - the orange block bounces around happily for a bit then it always stops a few pixels past the third checkmark on the progress bar. When I load the liveCD without the splash screen i get the following error:

[IMG]http://grad.bio.uci.edu/ecoevo/slockton/ubuntucrash.gif[/IMG]

the computer is locked-up at this point. The cursor is flashing but no amount of ctrl-alt-del can reboot it...

Later, while poking about the back/insides of the computer, I saw that it had it's own VGA port, so probably on-board video. So I changed the VGA device order in the BIOS from "PCI-VGA" to "Int-VGA", saved, and rebooted with the VGA cable in the on-board VGA port.  It worked just fine, booting to the live desktop.

So, it does seem like some kind of graphics card issue. I browsed this and other forums and people seem to have success with nvidia geforce4 mx 4000 cards, so what is going wrong?  Do I have to use the "driver update CD" option on the liveCD? Help!

Thanks,
Ste

---

### Post by slockton on 2007-12-14
Nothing?  Hm, looks like XP Media Center Edition instead...

Free, open-source software is all great until you can't even install the OS and then not get any help. :(

If anyone has any ideas I'd be willing to give Ubuntu another try.

Ste

---

### Post by slockton on 2008-04-09
*bump* - anyone care to contribute?

S

---

### Post by Jiffyman on 2008-04-09
Can you install the OS and try to use the card after you get it working with the on board vid? 
Have you already tried this?

---

### Post by slockton on 2008-04-09
Update: This post fixed my problem: [http://ubuntuforums.org/showthread.php?p=4640049#post4640049](http://ubuntuforums.org/showthread.php?p=4640049#post4640049)

:)
Ste

---

