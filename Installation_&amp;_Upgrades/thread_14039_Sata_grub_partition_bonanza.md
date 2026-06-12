---
title: "Sata grub partition bonanza"
date: 2005-02-04
forum: Installation &amp; Upgrades
---

### Post by inging on 2005-02-04
Hi, I installed ubunti yesterday and I have the following two problems;

1. no XP
2. no linux GUI

To take the second first, I tried the nvidia fix as suggested in the unofficial documentation. It doesn´t find the repositories. [link](http://ubuntuguide.org/#installnvidiadriver) This is not of a lot of concern to me, I think it maybe is because I use the 64 bit version? nforce 3 150 "vanilla" 2800 a64. (I have a network problem, next post)

What bugs me slightly more is no XP.

I´ll explain what I did, and what I believe happened. I freed up space for a new partition in xp, 10 gig. This is one the singular sata seagate disk, running on SiL 3512 chip controller. I put the cd in, language norwegian, I select the space, I select configure automatic and that´s about it.

Grub doesn´t detect xp initially. I made the edit, if i use the xp hd0,0 option it goes to black with nothing.

I tried fixmbr, no use as windoze can´t see any disks. also I tried fixboot, same problem. I used the list command and it only showed the cd, E:

After the first time I (didnt) use(d) fixmbr, the "boot" flag changed, as shown with the fdisk -l . Before it was the linux partition, now it is on the ntfs (first).

My windows boot c: partition shows in the list as ntfs. My second win partition shows as win95 / lba. linux partition shows as well, nf3.

After I started writing this, I tried to boot win once more. It now starts and loads a lot of .sys files until acpispy.sys, in safe mode, then hangs.

instead of c:\windows\blabla, it shows:
multi(0)disk(0)rdisk(0)partition(1)\windows\blabla

 :confused:

---

### Post by inging on 2005-02-04
I have 71 views, and noone have any clue about this?

Is there at least some other thread that explains some of this? There have to be more people that clicked the automatic partition button on a new XP box?

I have another question. It seems I don´t have network either, i tried the ping and ftp commands and they didn´t get contact. I suspect this is an issue with the nforce drivers.

1. Is there nvidia drivers present in the package? Is there some command I have to type?

2. My internet worked in the setup of ubuntu. Is there some way to sort out what is wrong, or even fix it?

2. Can I install the stuff I can get off nvidia´s site without a internet connection?

3. Can I burn it to a cd? Any particulars with this, I have alcohol 120%.

4. How do I access the cd drive from ubuntu?

---

