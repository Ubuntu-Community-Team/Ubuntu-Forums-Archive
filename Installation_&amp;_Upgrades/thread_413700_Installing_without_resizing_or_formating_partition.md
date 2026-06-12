---
title: "Installing without resizing or formating partitions i don't want to use"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by rysh on 2007-04-19
Hi 

I have two HD's (250GB and 300 GB) in my computer with Debian, Windows XP and Ubuntu Edgy Eft aand a lot offdata i don't want to loose... Now i want a new install on the partition where now Edgy is. This is in my system hdb6 ... hdba10 is my 1 GB big swap drive which i want to share with Debian. I downloaded the Desktop install CD but during the installation when i try to manually choose the partition where to install Feisty, all other partitions are also automatically provided with some mount points. I would like to not use them and not mount them in Ubuntu, but whenever i choose to "not use" them with the choice 'edit the partition', the sizes of the partitions are always about 29453 MB big in this edit field (what is not the size it is right now); and when i say not use it still wants to resize the partition. ... i can not choose to not use them and leave them alone at all ... i think this is a pretty big bug for me and hope there are other ways to cleanly install Ubuntu Feisty Fawn (i rather don't do the upgrade) ... in where the installation program leaves my other partitions alone. 

Thanks

---

### Post by mikewhatever on 2007-04-19
Mounting partitions will enable you to access these partitions from Ubuntu. It will not resize them. Point 7.04 to 6.10 partition, format root and swap only.

---

### Post by rysh on 2007-04-19
Sorry for the misunderstanding. But i try to explain it again. I want to do a new install on a partition which now has Ubuntu Edgy Eft on. So the only thing which need to be done is: format this partition and mount it as / (root). This is in my system /dev/hda6 ... But the manual disk partition tool wants to mount it as /media/hda6 ... so i need to edit this partition. So this partition tool wants to resize it also ... i can nowhere say it should leave the size alone and just format it. And the same with all other partitions which i rather don't want to use at all ... when i say in this partition-setup-tool that i do not want to use them it still wants to resize them. I have data on those other partitions which i want to keep save from the ubuntu installation. So i quit the install

---

### Post by rysh on 2007-04-20
To bad, Seems it is not possible with the desktop install CD. So i downloaded the alternate-install CD and with this i could let the installation leave my data partitions alone.

---

