---
title: "Boot repair iso for Xenial 32 bit"
date: 2016-09-18
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2016-09-18
I am looking for the latest release of yannubuntu's Boor-repair.iso, suitable for Xubuntu 16.04, 32 bit. Please don't send me to sourceforge. I have their .iso, and it was released in 2014 and doesn't work for xenial. I've been looking for the past two hours with no luck. Launchpad has Yann's files for Xenial, from June 15, 2016, but I have no clue how to access the files and get the .iso.

---

### Post by oldfred on 2016-09-18
Not sure then if he has updated his ISO as older one usually works.

But just install Boot-Repair into your installer. See second option:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

His ISO is just Lubuntu with Boot-Repair added as above.

---

### Post by ineuw on 2016-09-19
> Not sure then if he has updated his ISO as older one usually works.
But just install Boot-Repair into your installer. See second option:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
His ISO is just Lubuntu with Boot-Repair added as above.

It's shows here [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair) that the code was updated recently, but I couldn't find the ISO package. The old version boot-repair didn't have the required packages for version 16.04. Also tried to add the ppa to Lubuntu but it also failed because it didn't know about repositories. If there is no repository then there can't be a sources.list or installation of synaptic. I finally managed to upgrade the boot-repair through the terminal (sudo apt-get upgrade) which immediately identified the outdated boot repair components and updated them, and this worked. However, I still prefer to have the iso file. I store them for whenever a USB fails.

---

### Post by oldfred on 2016-09-19
The updates are to the ppa downloads. 
You may have to email Yann to see when he is updating his ISO.

I also keep Boot-Repair as an ISO to loopmount with grub, but also have Ubuntu, Knoppix, gparted, parted magic, super-grub and whatever else may fit. My newer flash drives are larger, so I usually now have a full install and several ISO. Having the ISO on one repair flash drive (actually several one UEFI & one BIOS) makes it easy to update when newer release comes out. I used to burn CDs and soon had a stack of old version CDs.

---

### Post by ineuw on 2016-09-19
oldfred, thanks for the info, I wasn't sure what other software was reliable, so I retained boot-repair. Stopped using CD's a long time ago.

---

