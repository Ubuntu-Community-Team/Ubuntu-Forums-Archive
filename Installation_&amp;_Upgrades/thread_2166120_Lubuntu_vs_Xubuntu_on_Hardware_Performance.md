---
title: "Lubuntu vs Xubuntu on Hardware Performance"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by Boab1993 on 2013-08-07
Hello all,

I am an avid user of lubuntu on my netbook, however it has always been known to me that the processor on this is terrible at best, and whilst i had free time on my hands yesterday with literally nothing to do i did a long needed benchmark test on my computer.

As it turns out i have 2GB of RAM and im using maybe about 245MB in total and my processor load is about 100% near constantly.

My question is does xubuntu have any advantages over lubuntu on performance by exploiting more RAM?
I use an XFCE install on my desktop, but ive not been keeping up very much over the last year or so as im between homes alot.

If not, any tips on how to lighten the load on my processor in my current install?

Thanks for all advice,

Cheers.

---

### Post by Frogs Hair on 2013-08-07
Below are the minimum system requirements for for both 13.04 flavors. Did the benchmark indicate  why the cpu is working so hard ?  

Lubuntu 13.04

The minimum system requirements for Lubuntu 13.04 are a Pentium II or Celeron CPU with PAE support, 128 MB of RAM and at least 2 GB of hard-drive space. This release also still supports PowerPC architecture, requiring a G4 867 MHz processor and 640 MB of RAM minimum.[78]

Xubuntu 13.04
&#8207;
Processor: Pentium III, 800 Mhz 
RAM memory: 512 MB
Video card: 32 MB
Hard disk space: 6 GB

---

### Post by Boab1993 on 2013-08-08
Hi Frogs Hair, 

I dont think i worded my question clearly enough,

What im wondering is because xubuntu uses more RAM and harddisk space, would that increase the performance of my computer over using Lubuntu?

As for the cpu, its an intel Atom N270, so the reason the load is so high is pretty much just because im running/loading more than one application at a time.

---

### Post by sudodus on 2013-08-08
Xubuntu is more advanced and has more eye-candy than Lubuntu, and therefore it needs more RAM. The harddisk space depends on how many and big packages that are installed.

I think the only really relevant test is the one that you run yourself using your hardware and running the programs you are interested in (and running them the way you want to use them, for example how many tabs to keep open at the same time).

I think one important thing is the general web browsing experience. Another one is playing video of the kind you want to play (kind of video, resolution, codec, bit-rate ..., and video player). My experience is that Lubuntu's desktop environment needs less horsepower than that of Xubuntu, so if video is limiting your performance, you should use Lubuntu. Flashplayer for linux is not well supported, which makes it hard to play flash video with low end computers. It might work better to download video files (if available) and play them locally.

It is also possible to install the other desktop environment and select which one to run from the log in screen. In Lubuntu:

```
 sudo apt-get install xubuntu-desktop
```
or
```
sudo apt-get install xfce4
```

depending on if you want the whole package or only the desktop environment. Then you can select the suitable desktop environment for each working session.

-o-

If you have an advanced graphic chip/card, you might be able to do a lot of video processing in the gpu and relieve the cpu from that work, but since the computer is a netbook, there is probably no such graphic chip or space for a separate card. But to be sure, check for the graphics card and post the result.

You can use for example ***hardinfo*** to get the information.

---

### Post by Boab1993 on 2013-08-08
Thanks for the info sudodus,

That pretty much covers it, to be honest. Its an old netbook(2008 i believe) so your right no such GPU exists.

As for if all xubuntu is over lubuntu is some flash graphics ill stick to lubuntu.

I  dont use graphics dependant software particularly, i mainly use the  likes of eclipse, code::blocks, steam, firefox with firebug etc. 

Just a shame it tends to chug a little if im using multiple applications.

Oh well, might be time for an upgrade, my wallet is sad.

Thanks for the advice.

---

