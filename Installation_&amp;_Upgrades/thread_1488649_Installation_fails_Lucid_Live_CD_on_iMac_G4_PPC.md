---
title: "Installation fails: Lucid Live CD on iMac G4 PPC"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Stanver on 2010-05-20
I can't get the Ubuntu 10.4 Live CD for PPC to work on my old 800 MHz flat screen iMac G4. I believe it's supposed to work, but the installation dies with a magenta screen about a minute after selection of any boot option in the yaboot dialog.

I tried all the sensible boot choices and options, all with the same result: some trundling of the CD reader, display of the messages related to the ramdisk, more trundling, then a blank magenta screen and no more trundling. The iMac becomes totally unresponsive: no more messages, can't enter any command shell. I get the impression (complicated story) that it begins to install the X server and then aborts.

This iMac has a PPC G4, 512 MB of working memory, and a GeForce2 MX video card with an nVIDIA chipset and 32 MB of video memory. There seems to be no hardware problem: OS-X 10.3 and OS-9 run just fine including wireless networking.

Any suggestions to get this working?

---

### Post by CharlesA on 2010-05-20
Could try hitting any key as the cd is booting and selecting "Check Disks for Defects"

---

### Post by Stanver on 2010-05-20
Now I end up with a black screen...

---

### Post by roym4 on 2010-05-20
We've had the same problem on an iLamp (G4 LCD) and a similar problem on a PowerMac G4 MDD. Install goes just fine, after reboot we get blank screen, no alt terminals available. Have tried nosplash video=ofonly, etc with no change. Any ideas??

---

### Post by Rabendoktor on 2010-05-26
Hi there,

same macs (iLamp and G4 MDD), same Lucid (cdimage for PPC), same prob (black or magenta screens...)

Any solutions found by now?

Thanks a lot!

Rabendoktor

PS: Whereas installation on my VERY old PowerBook G3 succeeded without any probs...

---

### Post by Stanver on 2010-05-27
[Debian 5.04]("http://www.debian.org/CD/http-ftp/index.en.html#stable") works, after some doing. You get the same magenta screen on first startup but Debian has a trapdoor on the X server: if X doesn't start in time then init drops you into a command shell.

Which is very convenient, since you can then log in as root, run "Xorg -configure" and follow instructions. Move the new xorg.conf in place, restart, et voilà: a working albeit somewhat slow desktop.

On Ubuntu this doesn't work, apparently because Xorg can't find the nVidia drivers (you can get into a simple CLI shell via the installation disk).

---

### Post by Rabendoktor on 2010-05-30
Hi, there,

at least for my G4 MDD (PowerMac3,6, with Radeon 9000 Pro) a firmware-update fixed my probs - although I had 4.4.8f2 installed, running the update ([http://docs.info.apple.com/article.html?artnum=120171](http://docs.info.apple.com/article.html?artnum=120171)) enabled me to install Ubuntu 10.0.4 from the alternate-cd without any probs now...

Have a wonderfus sunday!

---

### Post by Stanver on 2010-05-30
I think this bug exists only for this specific iMac model and video card, and only in Debian-type distros. I've tried a few more out of curiosity. Yellow Dog Linux works (but seems years behind, and thus of little use); Fedora produces a useless scrambled screen but doesn't crash.
Now I've gotten hold of a second-hand copy of Tiger. Which, of course, works flawlessly.

> Have a wonderful sunday!

Thanks, and to you! This sunday is past now, but I'll save it for the next...

---

### Post by kgarbutt on 2010-05-31
Hey Stanver,

I just installed 10.04 on my work G4 Mac. This is what you have to do. 10.04 won't work from the beginning because the old G4 Macs aren't supported. Start with an alternate 8.04 download for the old macs. When 8.04 is installed then upgrade to 10.04 with the update manager. There is a direct upgrade from 8.04 to 10.04. Do a search to find it. I just did it so I know it works. I should say though that my sound doesn't work on my G4 after all this. There is some sound issues with 10.04.

Good luck man.

---

### Post by Stanver on 2010-05-31
kgarbutt,

Perhaps I'll try this later, when I have more time. My intention originally was to try out the 10.04 live CD to see if it could replace Panther, and then I got carried away... 

If I remember well, the PPC was still officially supported on 8.04 Hardy. This is an excellent tip for anyone trying to install Ubuntu on an iLamp (i.e. the 2002 800 MHz 15" flat screen iMac with the GeForce2 MX). Another option is installing Debian.

> ... my sound doesn't work on my G4 after all this.

Exactly. Judging from my experience with Debian, there are many functions that don't work out of the box (for playing music, ditch ALSA and switch to OSS only). Note that support for the PPC doesn't necessarily mean support for the Mac. Nice for the kids to play with, or for Dad hacking away rainy afternoons. I'm typing this on a home-built system which works quite well with Kubuntu 10.04 as it has generic PC hardware, an Intel processor and no wireless, but still, it can't mount Samba shares.

For now however my little old iMac is functioning crisply with this ancient copy of Tiger, although I had to replace the hard disk after all these Linux experiments ;-) .

> Good luck man.

Thank you!

---

### Post by soldersplash on 2010-07-18
> **kgarbutt said:**
> Hey Stanver,

I just installed 10.04 on my work G4 Mac. This is what you have to do. 10.04 won't work from the beginning because the old G4 Macs aren't supported. Start with an alternate 8.04 download for the old macs. When 8.04 is installed then upgrade to 10.04 with the update manager. There is a direct upgrade from 8.04 to 10.04. Do a search to find it. I just did it so I know it works. I should say though that my sound doesn't work on my G4 after all this. There is some sound issues with 10.04.

Good luck man.

I'm trying this on an iMac G4 (iLamp). 8.04 is installed OK :D
Update manager doesn't show 10.04 available for dist upgrade though.
I have checked in software sources dialogue that dist upgrade is set to LTS.

What else might I be missing on this subject?

Thanks,

---

### Post by twizler on 2010-09-02
I am in the same boat... 10.04 ppc "iLamp" mac .. no work ... i get a yellow screen and nothing else. 

BUMP ](*,) ](*,)

---

### Post by jimwg on 2011-04-04
I've a 700mHz G4 iMac with a dead hard drive so I'm tinkering for a Live-CD replacement for Panther. Booting Ubuntu 10.04 or 9.10 leaves me stalled with a yellow screen. Ubuntu 8.04 seems to work well outside of Airport networking issues in refusing passwords. Wish there were a way to "install" other fonts for OpenOffice on it, but otherwise it's nice. I am going to take a whack at using a "alternate install" to see whether I can pre-burn prune the 10.04/10 iso of unneccessary files to bring down its infamous crippling over 700mb CD burn size. Would really like to know whether this is the max Ubuntu version this machine can handle, so if you're in the know please chime in.

JimWG

---

