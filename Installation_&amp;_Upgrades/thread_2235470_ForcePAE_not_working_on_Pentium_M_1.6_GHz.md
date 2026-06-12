---
title: "ForcePAE not working on Pentium M 1.6 GHz"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by Ralf_Hutter on 2014-07-21
Hello everybody, i guess i've read everything regarding installing lubuntu 14.04 on my pentium m 725 with 1.6 GHz which doesn't show its (supposed) PAE capability. I applied "ForcePAE" when booting, but then after some time i get the message "Installation failure" and the computer boots from the CD so that I can "fix the problem". I've tried twice. Actually this pentium m should have PAE capability, as the Lubuntu documentation indicates. Does anybody have an idea what the problem is? I know there are other ways to get it installed, with non-PAE-kernels. But that seems to be more complicated and maybe there's a way to do it this way.

---

### Post by plucky on 2014-07-21
> **Ralf_Hutter said:**
> Hello everybody, i guess i've read everything regarding installing lubuntu 14.04 on my pentium m 725 with 1.6 GHz which doesn't show its (supposed) PAE capability. I applied "ForcePAE" when booting, but then after some time i get the message "Installation failure" and the computer boots from the CD so that I can "fix the problem". I've tried twice. Actually this pentium m should have PAE capability, as the Lubuntu documentation indicates. Does anybody have an idea what the problem is? I know there are other ways to get it installed, with non-PAE-kernels. But that seems to be more complicated and maybe there's a way to do it this way.

What happens if you don't use Forcepae as a boot parameter?

Can you boot the Lived CD/USB?

If it starts the installation and then fails,it is not a PAE problem,it sound more like a problem with the burn of the CD.

Have you tested the integrity of the CD?

---

### Post by sudodus on 2014-07-22
I think your CPU has PAE capability, but we cannot be sure until you have tested it, because it is not officially stated. See this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

 and test according to it with ***cpuid***

```
cpuid|grep ^00000001
```

There might also be a problem with your motherboard. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

But I agree with *plucky *that there is probably some other problem, for example with your installation media (CD drive) or too low RAM.

It makes it easier to help you, if you also describe what is happening in detail.

- Which iso file did you use, the ***desktop iso file*** or the ***alternate iso file***?
- Can you check that the CD disk is good (do it early after booting from it)?
- Can you run a live session?
- Can you run in text mode or graphics mode?

---

### Post by Ralf_Hutter on 2014-07-22
The hash of the downloaded desktop iso file is ok and the cd test right before installing was ok, too. What happens is i boot with forcepae, then i get the black screen with the lubuntu logo for about a minute, cpu and disk drive are working. Then i get the lubuntu desktop background, disk drive still working loudly. I even get notified whether or not i am connected to the internet. But after another minute or so i get a big message: Installation failed. Then the live session starts, which works: i can use the internet and the terminal and do things (only shutting down and rebooting are not working fine, i get a black screen with some lines, the last being "stopping early crypto disks", and in the end i have to turn it off by hand). This is a Acer TravelMate 4502LCi, Pentium M 725 with 1.6GHz and 512 MB RAM. Graphics card is Intel 82852/855GM Integrated Graphics Device (rev 02). Wifi is switched off. As to the PAE capability - the cpuid commad that you gave me is not giving me any result (on another computer, though, because the one in question is not online at the moment and doesn't have cpuid installed), but i already did a cpu check and it showed me 36 bits physical address size, which should be the proof of PAE capability, right?

---

### Post by Ralf_Hutter on 2014-07-22
By the way, this computer has been running xubuntu for years.

---

### Post by sudodus on 2014-07-22
When the live session works, your computer can use forcepae and run. So it is *not* a PAE problem. The 36 bits physical address size is another proof of PAE capability.

512 MB is a bit low, but it should not stop the installation from working. I think you have problems with the graphics card. In order to run the installation without graphics you can 

- boot from the ***alternate installer*** (which installs the same Lubuntu) or
- use some of the other installers
. the ***One Button Installer*** or
. the ***OBI-9w*** installer

according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

After the installation (in text mode) you can try to use UXA acceleration for your Intel graphics. It is described in the same link.

---

### Post by Ralf_Hutter on 2014-07-22
Thanx, i'll try something else. Maybe even another linux distribution, as my cpu is already at the edge of what makes sense with lubuntu. I don't want to support those ever growing power requirements for a desktop pc, anyway.

---

### Post by sudodus on 2014-07-22
A friend of mine has a computer with the same or very similar CPU (IBM Thinkpad T41 with 1.6 GHz Pentium M and 1 GB RAM). I have the next version, (IBM Thinkpad T42 with 1.7 GHz Pentium M and 1.25 GB RAM). Both work well for us with Lubuntu and Xubuntu. We have another graphics chip, but I really think it is worthwhile trying ***UXA acceleration*** with your Intel graphics, because the CPU is definitely good enough.

But if you are looking for ultra light distros, I can recommend Wary ***Puppy, Tiny Core*** and ***DSL. Knoppix*** is very light, not ultra light and is very good at recognizing hardware, so it is also a good alternative.

You find more tips for old computers at these links
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=1582027"]Light Linux Distributions - Hardware Testing (RAM)
[/URL]

---

### Post by Ralf_Hutter on 2014-07-22
Both of you have at least twice as much RAM as i do - you really consider that "very similar"? I'm doing a new install cause xubuntu has become way too slow on this cpu. I know it's not only about the DE, but also about the hardware, but i've just checked [http://en.wikipedia.org/wiki/Lightweight_Linux_distribution](http://en.wikipedia.org/wiki/Lightweight_Linux_distribution)  I've read a lot about AntiX, Bodhi and Trisquel Mini now (Puppy, Tiny Core and DSL seemed to include less features or/and to stem from software i am less familiar with). Bodhi and Trisquel received some good reviews even when it comes to their usability for non-expert users like me. AntiX claims it is suitable for newcomers, too. Trisquel is one of the very few distributions that really run only free software. I might give it a politically motivated try... Its community seems working, too.

---

### Post by sudodus on 2014-07-22
The computers are similar, they were delivered with 512 MB RAM, but it is straight-forward to add RAM. You might even find used RAM of the right kind for a very limited cost.

It is worthwhile testing several distros. Let us hope that you find one, that works well with 512 MB, so that you can continue using the computer without adding RAM. Whatever results you get, please share your results with the Ubuntu community :-)

---

