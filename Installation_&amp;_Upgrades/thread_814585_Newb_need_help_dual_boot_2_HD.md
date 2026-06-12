---
title: "Newb need help dual boot 2 HD"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by sfagent07 on 2008-05-31
hey guys,

I have been looking all over for this site and good for how to install a dual boot for xp & unbuntu. I got xp on my C: drive and I have a D: drive with 30gbs on it completely blank. I would like to put unbuntu on it so I dont have to worry about killing my xp and want to take advantage of the space since Im not using it.

I cant find any info on how to do it everything trys to put it all on same drive. I would like to have a choice when my pc boots between xp and unbuntu though pleas. Any help is greatly appriciated.

By the way I get up to the partitioning part and have no clue what Im doing. Thanks

---

### Post by james_vanb on 2008-05-31
I have dual boot on 2 drives - XP and Hardy.  When you install Ubuntu, it will ask you where you want to install.  Just install on the second HD.  It will also ask during the process if you want to edit mbr to allow Ubuntu to also boot.  When you boot, you will get a screen listing available OS's to boot into.

---

### Post by MQMike on 2008-05-31
See:

Bigpond, home:   [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
(click to his GRUB page)

---

### Post by sfagent07 on 2008-05-31
ok I know this is a dumb question but. Do I just select the 2nd drive and hit next? or do i need to change partitions and all that stuff? I dont know what to change them 2.

C: has windows is 85gb
D: blank<want unbuntu on it> 28gb

do I just choose drive d and hit next?

---

### Post by Pumalite on 2008-05-31
Boot your Live CD and post:
sudo fdisk -lu (from the Terminal)

---

### Post by james_vanb on 2008-05-31
First drive listed should be the one set to "Master" and the second "Slave".  Install on whichever doesn't have XP.

You have the option of manually partitioning or automatically partitioning the whole drive or partitioning free space on one drive.  I partitioned the whole drive automatically.  If you want to manually partition, you'll find threads on this forum giving you instructions on how to do same.

---

### Post by Pumalite on 2008-05-31
Make sure you have both SATA or both IDE or it's not so simple. Also when you go Manual during the installation you will have to know what partition to choose. Keep in mind the limit of 4 primaries per drive.

---

### Post by Pumalite on 2008-05-31
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

