---
title: "Swap file management or downgrade ???"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by WinRiddance on 2010-06-28
Alright, I just wanted to see if this would even work, so I installed Ubuntu Lucid Linx 10.04 on a 2001 Sony Vaio with 1.7 Ghz. Intel P4 processor and, yes you're reading this correctly, only 256 MB of PC2100 Ram. I dumped in my own PCI wlan card and 64 MB Radeon 9000 Pro AGP card, then I did the installation.

Although I already ordered 2 mem chips (512 MB each) for this system which will max it out, I also created a 5 GB swap partition since I figured that this would greatly enhance the installation and consequent usage thereafter. Now mind you, the installation of 32bit Lucid worked like a charm. Slower than normal, but like a charm. Wifi is working and even the 3D desktop settings are working in advanced mode. **BUT ....**

... the system is just way too slow to react to the mouse and keyboard. I'm certain that the lack of memory has a lot to do with that although I was secretly hoping that the huge swap file would help to make a big perfomance difference. So here now my questions:

1. The swap file doesn't really appear to have made any difference at all. How come?
2. If I wanted to "downgrade" to Xubuntu, how would I accomplish this?
3. Would it be a better idea to just start over with an installation of Crunchbang instead?

I'm trying to get this system working **for a relative who's never had a computer before**. Whatever I end up with on this machine has to be _as simple as possible to use_ while maintaining some semblence of decent perfomance. I'm sure before too long they'll want to enhance their desktop looks/theme as well so consideration needs to be given to that too. Your suggestions and comments would be appreciated. Again, Ubuntu Lucid runs just fine, although really really slow. Internet is no problem. Thanks.

---

### Post by WinRiddance on 2010-06-29
**Bump** ... alright people, no experts here who can advise on Swap management and less streamlined Linuxes ???

---

### Post by snowpine on 2010-06-29
Your system is slow because it does not meet the [minimum hardware recommendations for Ubuntu]("https://help.ubuntu.com/community/Installation/SystemRequirements"):

> Ubuntu Desktop Edition

    * 1 GHz x86 processor
    * 1 Gb of system memory (RAM)
    * 15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily)
    * Graphics card and monitor capable of 1024 by 768
    * Either a Cd/Dvd-drive or a Usb socket (or both)
    * Internet access is helpful 

Increasing your RAM to 1gb should make a big difference (you currently have only 25% of the recommendation!)

Your assumptions about swap and performance are a little bit backward. Swap doesn't speed up your computer; in fact, swap is terribly slow and using it should be avoided if you're looking for performance. The reason for this is that a hard drive is much slower than RAM. It is better to have enough RAM for the task so that swap is not used. 

The main benefit of swap is that you can run applications that require more RAM than you physically have, for example Ubuntu on 256mb. :)

---

### Post by Malta paul on 2010-06-29
If you made 5Gb of swap file it far to large for you system spec. In your case I would only use 256Mb. Unless you are using a very work intensive program the only time the swap file will be used is if you use hibernate or suspend. :wink:

---

### Post by dino99 on 2010-06-29
Lubuntu should run better on your system

swap is only used when free mem =0 or so and for suspend/hibernate, as linux consider ram faster than swap

---

### Post by WinRiddance on 2010-06-29
Thanks dino99

I found this link here to be incredibly helpful, especially with all of the user comments below which helped to provide an even better insight:
[http://www.tuxradar.com/content/whats-best-lightweight-linux-distro](http://www.tuxradar.com/content/whats-best-lightweight-linux-distro)

Based on everything there, trying to combine ease of use, looks, and stability I went ahead and tried Mint first. Ended up with problems though, nothing major, but then decided to give **Lubuntu** a shot anyway. Yeah, you're right, Lubuntu is incredibly easy to use and I think that our relative will have no problem at all with it.

I'll be tweaking it just a little bit, adding Tomboy with a bunch of Tomboy help files that I wrote in the past 12 months, and I'll change it visually just a bit more to the user personality. All in all I'm certain that Lubuntu will work out just right. I'm already impressed with the performance even though I'm still running with 256 MB of Ram. Can't wait to see what it'll be like when I have 1 GB of Ram on it.

:lolflag:

---

