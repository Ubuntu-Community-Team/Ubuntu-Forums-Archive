---
title: "Cannot instal on VAIO AR71s"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by casagan on 2008-08-26
Hello All.

Recently I bought a sony VAIO, which comes with Vista installed. The machine has 4Gb of RAM, core2 duo t9300 processor, Nvidia 8600m GT, an integrated webcam, and a RAID0 HDD, consisting in two 250 Gb HDDs. Vista is nice looking, and it seems to work ok, and the VAIO comes with some nice preloaded software. But I wanted to install ubuntu 64 bits on this, may be using dual boot with vista. Mainly because vista only sees 3Gb of memory and opengl performance under vista is not very nice. 

I tried the live cd and seems like everything works out of the box, even the webcam, except one thing, the partitions in the raid HDD are not seen. I have tried the alternate cd, and it doesn't see the partitions I have made from vista. Initially I had one hidden recovery partition, and almost 450 GB with vista installed. From vista I reduced its partition to 300 Gb, and left 150 Gb free space for ubuntu to install there. I cannot get ubuntu to see this partitions. I have read the alternate cd installation guide, and seems like I should be able to see the free space in the disks and assign this to partitions for ubuntu and later use them as a RAID 0 system or device. But the installer keeps telling me to use all the space in the 2 disks (250Gb X 2).

I think that something is wrong with the installer, because I have tried the fedora 9 installer and it detects perfectly the 350Gb space and the 150 Gb space left for installation... So, if someone can tell me how to do this, perfect! :-) If not, I will have to install fedora on this machine. I already have ubuntu on two other machines, and I started to fell very comfortable with ubuntu. 

Thanks in advance, and excuse my English... ;-)

Casagan.

---

### Post by loxan on 2008-10-02
I turned off the fakeraid in BIOS. Then I setup software raid 1.

---

### Post by casagan on 2008-10-03
Thanks for your answer. Finally I installed fedora 9. It recognizes the raid 0 setup and I can do dual boot with the preinstalled vista, which I need for some of my apps. 

Casagan.

---

