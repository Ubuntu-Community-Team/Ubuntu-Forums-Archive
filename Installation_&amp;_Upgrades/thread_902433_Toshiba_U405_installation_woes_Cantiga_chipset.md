---
title: "Toshiba U405 installation woes Cantiga chipset"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by jzarr on 2008-08-27
Hi,
I just purchased a brand new shiny Toshiba U405-S2856 which has the new Cantiga chipset. When i boot from the 8.04 CD my graphics are un-readable. Apparently i have to download and compile in the newest intel drivers. 

Is there any boot command i can use to get a viewable display (some sort of graphics safe mode). 

Someone in another forum suggested i try 8.10 alpha 4 which has Cantiga support, anyone know that for sure?

---

### Post by guido_damico on 2008-08-28
Hi jzarr,
I am having a similar issue on a different HW (see my post [here]("http://ubuntuforums.org/showthread.php?t=903182&highlight=cantiga")): can you direct me to where those driver would be?

As for the safe mode: when you boot from the CD you can click F4 and then choose "safe graphics mode". In my case it did not help, though.

---

### Post by mamber-m on 2008-08-29
Hello,

I have the same Laptop (U405-S2856) and exactly have the same problem. I tried the safe graphics mode but it didn't change the result...

I erased Vista already; I will try the alpha release tomorrow.

Hopefully we can run Ubuntu smoothly soon :)

---

### Post by mamber-m on 2008-08-30
I tried 8.10 alpha 4. The splash screen (with the ubuntu logo) looks weird (how it is weird changes everytime, which is not a good sign), but actually installation is completed. However, after the first reboot right after the installation is over, ubuntu starts up, and blackout... I am still trying to figure out.:(

---

### Post by eeejay on 2008-08-31
Hi mamber-m,

It sounds like we have similar experiences. Could you post your logs, etc to the following bug? Of course do so only if you think this could be the same issue.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/263114](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/263114)

---

### Post by mamber-m on 2008-09-04
> **eeejay said:**
> Hi mamber-m,

It sounds like we have similar experiences. Could you post your logs, etc to the following bug? Of course do so only if you think this could be the same issue.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/263114](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/263114)

I checked the bug link you provided and it seems that it was resolved. Could you possibly explain step by step how you solved the problem? I am such a newbie to using X.

---

