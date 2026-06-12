---
title: "Partitioning Problem...Please Help...."
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by nsnchat_12 on 2008-06-11
I have this major problem here... help please....

I have a 250GB hard disk with C,D,E,F, and G drives......all 50 GB each and C with XP installed previously....

then later i had some major virus attack and had to reinstall XP.....instead of reinstalling it i had formatted only C drive and then divided C into 2 drives (35GB for Windows XP...i did not install windows yet....... and the rest 15GB for Ubuntu)then installed Ubuntu with a ubuntu live cd and after that everything went allright.....


i installed many applications through Add/Remove applications and all went right for 4 days.....then i took my old original Windows XP cd and then did boot from cd.....there i could see all the 6 partitions and 1 swap partition in the partition manager.......and then chose that 35 GB empty space and then formatted it.......


once formatting is complete it copies necessary windows files and after that the system automatically rebooted......then next when i was supposed to start installing when instead an error had occurred stating that "Partition Table Invalid".......


i could not do anything else.....i again put the Ubuntu Live CD  and booted through it and saw in the partition Manager that the whole hard disk was being shown as "unallocated space"...This totally freaked me out....


When i click the drive volume i get an error saying that "Unable to Mount Volume"......Again I booted through windows and at the Windows Partion Manager i could clearly see all the drives each well defined and totally prefect.....Again i tried to reformat the 35GB space and again got the same error......


What is the problem and how to rectify it please help me guys.....I want both WindowsXP and Ubuntu under 35GB and 15GB space each and also need all my data available under both the Operating Systems without formatting the whole hard disk......or atleast one drive completely on Linux and the other 4 in XP

---

### Post by Pumalite on 2008-06-11
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by nsnchat_12 on 2008-06-12
Is there any particular order to install OS's........I mean Can I install Ubuntu Linux and then later XP on the same hard disk as dual boot ........or is it necessary that i install my windows partition first and then install ubuntu or something like that.....

---

### Post by zvacet on 2008-06-12
>  is it necessary that i install my windows partition first and then install ubuntu

It is not necessary but it is easier.

---

