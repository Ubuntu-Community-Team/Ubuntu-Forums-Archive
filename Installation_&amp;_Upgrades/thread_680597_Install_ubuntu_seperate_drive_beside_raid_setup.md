---
title: "Install ubuntu seperate drive beside raid setup"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by germike on 2008-01-28
I have been trying ubuntu on virtualbox, and i like it a lot. Now i got myself an extra drive to install ubuntu on. My setup and questions :

2 sata drives on Intel Matrix raid 0, contains vista install

1 new sata drive seperate from the raid setup

Can i install ubuntu on the seperate drive without messing up the vista install ?

I guess i could switch what to boot via the bios, switching between the raid array and the seperate drive as boot drive, is this correct ?

Is there a way to setup GRUB or any other boot-program from the seperate drive to allow vista to boot without switching things around in the bios ?

As i am quite a beginner i would not like to change anything on the raid setup. 

THanks !

---

### Post by imtheguru on 2008-01-28
> **germike said:**
> Can i install ubuntu on the seperate drive without messing up the vista install ?

I guess i could switch what to boot via the bios, switching between the raid array and the seperate drive as boot drive, is this correct ?Yes and yes.

> **germike said:**
> Is there a way to setup GRUB or any other boot-program from the seperate drive to allow vista to boot without switching things around in the bios ?Well, the simplest method would involve keeping grub unaware of the raid. Unplug the raid, install linux+grub on the harddisk, it will become hd0 (grub uses BSD notation, so even serial driver, sd, remain hd).

Reconnect your raid and use the bios to switch between operating systems.

---

### Post by germike on 2008-01-31
Ok thanks for the answer !

1 question remains : Would it be possible have GRUB (or something else) boot vista from the raid, having installed ubuntu as you wrote with disconnecting of the raid and installing ubuntu on the new drive ?

This to prevent having to go into the bios each time.

---

