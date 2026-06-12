---
title: "Ubuntu install problems"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by luke9511 on 2007-01-17
ok i downloaded the iso and burned it to a cd and put it in the cd drive and restarted the computer and it booted from the cd and i chose the first option, and it starts booting and it gets to the gnome desktop and it keeps loading from the cd or something and when it stops, i double click install and it starts accessing the cd and it keeps doing this, i left it on all night and its still accessing the cd, its not doing anything, anyone have any advice,? im also trying to install it on a older computer, P3 600mhz 128mb, it runs mandriva fine. and thanks in advance for any help/advice

---

### Post by taurus on 2007-01-17
With only 128MB of RAM, you should use the Xubuntu or even the fluxbuntu instead of Ubuntu version.  

[http://www.xubuntu.org](http://www.xubuntu.org)

Also, try to burn it at a slow speed like 4x.

---

### Post by luke9511 on 2007-01-17
well right now i dont want to since i may get the same problem im having now, so i just want to try and fix this first and then download the others

---

### Post by luke9511 on 2007-01-18
ok i got it installed and i have to say i like this alot, i like it alot better than mandriva thats for sure, but now i have another problem, my sound card is not installed and when i follow the guide on here on how to try and install it, im getting an error saying alsa source isnt installed and i cant figure out how to get it installed, so any help on this would be great and the sound card im using is an isa sound card

---

### Post by highneko on 2007-01-18
> **luke9511 said:**
> ok i got it installed and i have to say i like this alot, i like it alot better than mandriva thats for sure, but now i have another problem, my sound card is not installed and when i follow the guide on here on how to try and install it, im getting an error saying alsa source isnt installed and i cant figure out how to get it installed, so any help on this would be great and the sound card im using is an isa sound card

There's a package called "alsa-source". Try "sudo apt-get install alsa-source".

---

### Post by luke9511 on 2007-01-18
> **highneko said:**
> There's a package called "alsa-source". Try "sudo apt-get install alsa-source".

i did that and it said E:Couldnt find package alsa-source

---

### Post by luke9511 on 2007-01-18
ok im just posting to say that i got one of my sound cards installed and playing sound, though its really low and the sound is turned up all the way

---

### Post by taurus on 2007-01-18
Look in alsamixer!

```
sudo alsamixer
```

---

### Post by UncleFoo on 2007-01-18
Check this out.

[http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")

The most commonly requested apps, codecs, and tweaks that are not found in the base distribution.

---

### Post by luke9511 on 2007-05-10
i figure i would postr my question here rather than start a new one, basicly im trying to install ubuntu on my 250gb sata harddrive and i made a custom partition for it with partition magic like i have done before, but for some reason ubuntu doesnt see it and so i cant install it, is there anyway i can fix this? cause im wanting to dual boot ubuntu and xp, so any help on this problem would be awsome

---

### Post by taurus on 2007-05-10
Partition magic and Linux don't work well together.  Therefore, you should use gparted from the LiveCD to format your harddrive first.

---

### Post by luke9511 on 2007-05-10
> **taurus said:**
> Partition magic and Linux don't work well together.  Therefore, you should use gparted from the LiveCD to format your harddrive first.
i dont want to format the whole drive just a certain partition and i have used partition magic in the past with linux and never had any trouble

---

### Post by taurus on 2007-05-10
You can format certain partitions with gparted too.

---

### Post by luke9511 on 2007-05-10
> **taurus said:**
> You can format certain partitions with gparted too.
im getting an error saying that theres no root drive in the partition or something like that

---

### Post by luke9511 on 2007-05-10
ok i got it installed but now im having video card problems, i got a ATI Radeon X1600 Pro PCI-E 512mb video card, im also having problems logging in its saying it cant find my profile or something

---

### Post by luke9511 on 2007-05-11
how would i go about fixing this error > .: 106: Can't open /etc/profile

EDIT: i got it fixed but im still having problems with my video card not being detected even know i can see the desktop etc, i got the linux drivers for my card but they dont seem to be helping anyone got any advice?

---

