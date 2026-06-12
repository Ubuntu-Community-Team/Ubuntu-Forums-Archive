---
title: "[SOLVED] strange behaviour after heron clean install"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2008-08-23
I have been trying 8.04 kernel version 19 for a couple of weeks dual booted with m,y 7.10 installation with gutsy on /dev/sda2 and the temporary installed heron on /dev/sda5  which I created for the purpose of testing. 

Tonight I decided to pull the trigger and do the switch, so using Gparted from gutsy I formatted sda5 to give a clean data storage partition and then using the live cd installed heron onto [COLOR=Blue]/dev/sda2[/COLOR] using the manual partition during install and formatting /dev/sda2 to ensure a clean install. 

[COLOR=Blue]My home partition is on /dev/sdb1 [/COLOR]

After what appeared to be a faultless install I started to use it, did the obligatory program and security updates (all 236 of them) and then following that found that I now have two kernels -- 2.6.24-16-generic and 2.6.24-19 Generic.. 

Booting into 2.6.24-19 I found that everything worked like -- mega slow, (made vista appear fast) and none of the processes requiring admin rights would actually open. ie I tried synaptic, and can see two titles in the bottom bar saying something like, opening syanptic and opening admin rights, and then Poof! they are gone and nothing happens. 

Sooo I have possibly decided to reinstall again. 

1st question -- do I need to in order to fix the speed and program launching? 

2nd question if I do, when I get to the partitioner part, can I edit the**[COLOR=Blue] [/COLOR][COLOR=Blue]/dev/sdb1[/COLOR]**  partition and select the mount point as [COLOR=Blue]/home[/COLOR] **without overwriting my data filled home directories? **(I am not selecting 'format' in this tab) 

Would appreciate some help

Doug

---

### Post by livestockPimp on 2008-08-23
as for question 2)
you can always not create a separate partition for home and once you are installed edit the fstab (nano /etc/fstab) and add a line in for the new home dir and then adjust the permissions (chown username:username: /home/username -R)

---

### Post by tropdoug on 2008-08-23
That makes sense, I presume that once I have done that the /home disk will automount on boot, is that correct?

---

