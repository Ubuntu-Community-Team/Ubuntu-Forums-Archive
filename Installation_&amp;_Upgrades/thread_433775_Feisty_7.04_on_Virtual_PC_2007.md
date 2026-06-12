---
title: "Feisty 7.04 on Virtual PC 2007"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by nunja business on 2007-05-05
I am trying to start/install from the regular (32-bit) iso.

Machine is AMD X2-4800 with Vista Ultimate
2GB RAM, 1GB Readyboost drive and PLENTY of hard drive space
Radeon x850 video through dual monitors.

I am trying to mount the iso in MS Virtual PC 2007 so I can either run it live or install it to the virtual hard drive. Unfortunately, the only way it will even boot to the desktop is in SAFE VGA mode. Then, while I can see the desktop, I can't mouse-click or keyboard anything. I end up killing it by closing the virtual pc.

I have tried every VGA configuration available and no luck.

I have successfully installed and operated XP Pro SP2 in a Virtual Machine, so I know VPC is not the problem.

Has anybody managed to do what I am trying to?


Thanks!

---

### Post by boon72 on 2007-05-07
im in the same boat :) ive got XP pro on there ok, but all i get is the first choice menu where i pick install, then it goes black for a while before giving me a messed up screen.

my pc spec is

C2D E6600
4gb ddr Geil Ultra low 4-4-4-12
ATI X1900XT 512mb
650gb hdd's


anybody any ideas?

thanks in advance :)

---

### Post by NicB on 2007-05-07
The first issue is there seems to be a problem with the latest linux kernel and virtual pc which will stop the mouse working. I have looked around and several people have logged this as a bug. Therefore Ubuntu 7.04 seems to be a no go at the moment.

You can get Ubuntu 6.10 to successfully work under Virtual PC 2007, I have, but it requires using the alternate CD image and changing the colour depth. Have a look at the following page for more details.

[https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004) scroll down for the Virtual PC 2007 bit, works a treat. You may also need to make the sound card change listed on this page.

---

