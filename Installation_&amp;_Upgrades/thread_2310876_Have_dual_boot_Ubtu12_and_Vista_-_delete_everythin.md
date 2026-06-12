---
title: "Have dual boot Ubtu12 and Vista - delete everything and install new Ubuntu OS"
date: 2016-01-22
forum: Installation &amp; Upgrades
---

### Post by mitchan on 2016-01-22
Hello! I've been weeks trying to figure out what to do. I would appreciate any help you can give! 

I have an Acer Extensa 5230 from 2009. It came with Windows Vista pre-installed. A friend helped me install Ubuntu in a partition, in dual boot, and a few years later helped me update to Ubuntu 12 LTS. 

My computer is old but still functional and I'd like to keep using it for as long as I can. A month ago I tried to fix something in Ubuntu and crashed the system, now I can only access through Grub, selecting the oldest version. Windows Vista never worked very well and it's slower than ever. 

I want to completely reformat the computer, delete both systems and the partition, and install a new OS. I have the Live CD for Ubuntu 14. Can I just put the Ubuntu install disk and delete and install the new system from there, or do I have to delete partitions or do anything else before the install? 

I don't mind much losing Windows Vista, but I'd need the new OS to be functional. 

Again, thank you in advance for any help! I'm pretty much a noob at these things.

---

### Post by sudodus on 2016-01-22
Try some versions (start with 14.04.1 LTS) and flavours of Ubuntu (start with the light-weight Lubuntu and maybe Xubuntu and Ubuntu MATE). Try them 'live' without installing until you have found what works well. Then you can install that version and flavour.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

Probably 14.04 works well. If not, you can select a lightweight 'community re-spin' based on Ubuntu 12.04 LTS (which you know works in your computer). This version will be supported until 2017 (including the re-spins Bento, Bodhi and LXLE).

Edit:

> Can I just put the Ubuntu install disk and delete and install the new system from there?

Yes, but I think another flavour (with a lighter desktop environment) might work better :-)

---

### Post by mitchan on 2016-01-22
Thanks for the answer! I might have to try other versions. Somehow the live Ubuntu 14.04 doesn't load on my computer. I boot from the DVD, the screen comes on, but whether it starts automatically or if I select the option to try the live version without installing, it starts loading and then freezes. Pretty much something similar happens when I try to boot from my current Ubuntu version. That's why I was considering deleting the partition, or the current Ubuntu, before trying another OS. Is that possible?

---

### Post by Vladlenin5000 on 2016-01-22
You're probably barking at the wrong tree...
The symptom suggests hardware problem, probably RAM.

---

### Post by mörgæs on 2016-01-22
I see no signs of hardware problems but you should follow the advice given above: Leave Ubuntu and try something lighter like L/Xubuntu.

---

### Post by Vladlenin5000 on 2016-01-22
This are the signs of a potential hardware problem:> I boot from the DVD, the screen comes on, but whether it starts  automatically or if I select the option to try the live version without  installing, **it starts loading and then freezes**. Pretty much **something  similar happens when I try to boot from my current Ubuntu version**.
Also, > Windows Vista never worked very well and **it's slower than ever**.
And, last but not least, > Acer Extensa 5230 from **2009**

The first suspect would be the HDD but considering it shows the same symptom in a live session other components like RAM, VRAM (if applicable) or the graphics chip itself should be considered (among many other possibilities).

ACERs are know for their low price (sort of), not for build quality and definitely not longevity. Their alternative brand - eMachines - is even worse, being synonymous of "disposable PC"...

---

### Post by $yl9pAR%t on 2016-01-22
I can bet $2 this hardware is not good enough to handle Compiz, hence you can only use Ubuntu 12.04 in 2d mode. If you want something newer, I suggest installing Xubuntu 14.04.

To remove your old partitions, just chose "use entire disk" at the beginnig of the installation process.

---

