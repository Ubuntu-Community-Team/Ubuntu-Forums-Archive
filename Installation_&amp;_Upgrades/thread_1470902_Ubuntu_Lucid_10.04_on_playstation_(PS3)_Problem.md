---
title: "Ubuntu Lucid 10.04 on playstation (PS3) Problem"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Danimoth on 2010-05-03
I downloaded the appropriate iso for the ps3 from here:

 [http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/)

(specifically: ubuntu-10.04-desktop-powerpc+ps3.iso via torrent)

Installation runs smoothly up until 100% and then i am prompted to reboot.
When i click reboot, i get info on some daemons(?) shutting down(i think) and then the cd is automatically ejected and i am prompted to press enter.

So far, so good. After i hit enter though, i get a large amount of various read errors and finally a segmentation fault. The system just hangs there :/. 

I forcibly reboot the PS3, and then i am greeted with the pack of errors that are shown in the screenshot.

---

### Post by P!X3L on 2010-05-04
I can get into the install, however after the first couple installation screens my ps3 just hangs... :frown:

---

### Post by phanboi on 2010-05-05
I was searching for a turoial to install lucid lynx on my ps3 when i stumbled upon this thread.. 

dont really wanna install anymore lol

hmm can you get into the ps3 xmb? or anything else at all?
or is it like semibricked or something..

---

### Post by P!X3L on 2010-05-05
Well I've picked up a couple pieces of knowledge between the last post and this. 
I got ubuntu 10.04 running on my ps3 by installing the petitboot bootloader. (the version for ubuntu 9.x as I was having the mount error)
then download the ALTERNATE install disc.
[http://cdimage.ubuntu.com/ports/releases/10.04/release/ubuntu-10.04-alternate-powerpc+ps3.iso](http://cdimage.ubuntu.com/ports/releases/10.04/release/ubuntu-10.04-alternate-powerpc+ps3.iso)

use that to install and click through the steps. 
took a while but it finished up eventually and I can boot into ubuntu no problem. :p

---

### Post by scc4fun on 2010-05-20
I just tried installing Ubuntu on my 60GB FAT PS3 running 3.15 last night. I installed the latest petitboot from the installation instructions at psubuntu. When I restarted into Other OS with the Ubuntu 10.04 (Lucid) Desktop CD in the drive I was not able to see anything while connective via HDMI. I can't find the original composite cables and I don't have component cables for it (HDMI's so much easier and supports full resolution Blu-rays). It didn't seem like the PS3 was outputting anything when I restarted. I have also tried using the bootloader from the Ubuntu CD, but could not get any video output then either.

Any suggestions?

---

### Post by andibuntu on 2010-06-05
> **P!X3L said:**
> 
took a while but it finished up eventually and I can boot into ubuntu no problem. :p
How is it working for you?
I am having a hard time installing most packages because dependencies are missing.
Can you check if you see "zlib1g-dev" for example? It seems to be needed by quite some packages.

---

