---
title: "CD ROM problem"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by my_abousamra on 2010-06-17
hi all,

I was trying to install virtualbox on ubuntu 10.04 but it always give me this statement 

**For installing from CLI**

Media change: please insert the disc labeled
 'Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)'
in the drive '/cdrom/' and press enter

**For installing from Ubuntu Software Center**

CD/DVD 'Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)' is required

Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from the medium.

The problem here is that I have no cdrom in my computer, so I tried to mount the ubuntu iso file on /cdrom but it doesn't work

---

### Post by gadolinio on 2010-06-17
> **my_abousamra said:**
> hi all,

I was trying to install virtualbox on ubuntu 10.04 but it always give me this statement 

**For installing from CLI**

Media change: please insert the disc labeled
 'Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)'
in the drive '/cdrom/' and press enter

**For installing from Ubuntu Software Center**

CD/DVD 'Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)' is required

Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from the medium.

The problem here is that I have no cdrom in my computer, so I tried to mount the ubuntu iso file on /cdrom but it doesn't work

How is it that you try to install it? If it's from Synaptic or a downloaded .deb file, this might help: go to System--> administration--> software sources. If you see under "Instalable from CD-ROM" the name of your ubuntu version selected, remove the tick there and close the window. It asks if you want to reload... say yes. Then try to install again.

---

### Post by my_abousamra on 2010-06-18
Thank u, It worked for me

---

### Post by gadolinio on 2010-06-19
> **my_abousamra said:**
> Thank u, It worked for me
Great!
Please remember to mark the thread as "SOLVED".

---

### Post by satoof112 on 2011-12-18
> **gadolinio said:**
> How is it that you try to install it? If it's from Synaptic or a downloaded .deb file, this might help: go to System--> administration--> software sources. If you see under "Instalable from CD-ROM" the name of your ubuntu version selected, remove the tick there and close the window. It asks if you want to reload... say yes. Then try to install again.




great it worked for me thnx very very very very much

---

