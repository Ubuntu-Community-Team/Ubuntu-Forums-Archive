---
title: "No common CD-ROM drive detected"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by hnzz on 2006-08-13
I am trying to install ubuntu on my new system. I got the i386 server iso. the systems boots fine, but after the whereabouts and keyboard questions it just says that it can't find a common CD rom drive. The system is a Gigabyte GA-965P-DS4 with 3 SATA drive and a IDE CD-ROM drive. Any help much appriciated!

hnzz

---

### Post by Encryptor on 2006-08-13
same problem here. I have an ASUS P5B Deluxe WiFi with a JMicron controller. I am installing Ubuntu over the network, as I couldnt get it to detect the CDROM. There is a mm patch to the 2.6.18 kernel that is supposed to fix this (IMHO) so I am working on that right now. You might want to find out what PATA controller are you using and search on the internet for posts from people that had the same problems with it.

---

### Post by Lord Erik on 2006-08-17
Same problem here.  I was having the problem with the install hanging at mounting root filesystem.  Used the alternate CD instead and it now stops with that CD drive error.  

I've tried with a pioneer dvd burner and a much older ACER x32 speed CD drive.  Both give the same common cd rom not found.  Also tried hoary and breezy and get the same.

---

### Post by thotz on 2006-08-28
Could you have a look at Ubuntu Bug [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502)

It will be fixed in Ubuntu Edgy soon.

---

### Post by jrcmuniz on 2006-09-10
> **thotz said:**
> Could you have a look at Ubuntu Bug [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502)

It will be fixed in Ubuntu Edgy soon.


Damn! I'll send my LG-H10DVD/CD back to the store and buy a Samsung SATA! Gosh!

Joao.

Sorry, I'm just really annoyed.

---

