---
title: "deleting partitions/fresh install"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by generollins on 2008-04-24
Hi

I'm fairly new to Linux and have installed Fedora and Ubuntu. The problem is I don't really understand too much about partitions and what i can delete and what i shouldn't. 

I have 7 partitions!!

partition 1 = 4GB stores XP and backup software for my Acer laptop. Kinda like a restore partition to use if i want to revert to it at anytime

partition 2 = C drive which is like 50GB or so

partition 3 = D drive which was 50GB but now has a version of fedora and ubuntu on. so now its 1MB yes MB!

partition 4 = i tihnk is the fedora partition 17GB

partition 5 = the GRUB loader for Ubunutu i think 850MB or so

partition 6 = the old grub loader for fedora 102MB

partition 7 = 14.02GB which i set for ubuntu

The question is what can I delete so i can dual boot with a one version of linux! I want to install a fresh version of the new ubuntu cos the one i have at the mo has an annoying blue block on the right hand side which has appeared since trying to install a sidebar.

I believe i can delete the partitions but wasn't sure and i know the GRUB loaders shouldn't be touched because it could screw my laptop up and not even let me into XP.

I've attached a screenshot of the layout so it might make more sense. I have one hard drive the 2 blocks of partitions are split so i could attach them properly. The light blue blocks should be next to the dark blue blocks if you see what i mean! If anyone could advise me what to do it would be much appreaciated. I tried to install Ubuntu again but it just offered me another partition to create.

---

### Post by Pumalite on 2008-04-24
You can install on top of partition 7 if that is where your old Ubuntu is. Where is /swap?

---

### Post by generollins on 2008-04-25
ye thats where the Ubuntu 7.10 was/is! i presume i'll get another GRUB loader so i'll have 3?? :mad:

---

### Post by generollins on 2008-04-29
the other thing is when i go to install it again it asks if i want to install it on hda07. I know when i was installing fedora that it showed the partitions and my first partition was hda0. So i thought the hda07 was an 8th partition that was going to be created, hence why i've held off reinstalling it.

---

### Post by Pumalite on 2008-04-29
Post:
sudo fdisk -l
Post a screen shot of Gparted.

---

