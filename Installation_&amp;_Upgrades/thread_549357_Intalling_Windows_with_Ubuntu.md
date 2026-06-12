---
title: "Intalling Windows with Ubuntu"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by rajkd on 2007-09-12
I installed Ubuntu Recently based on the documentation on Ubuntu site. In the documentation it said both the OS wil be working and the partitioning done automatically, but windows OS was remove after I installed ubuntu and I am not able to install it.

---

### Post by Bungo Pony on 2007-09-12
I think you may have got the partitioning part wrong. Partition the drives yourself using the Gparted live CD (free download) before installing your OSes.

---

### Post by rajkd on 2007-09-12
I have already installed Ubuntu and now it does not allow me to install window at all

---

### Post by init1 on 2007-09-12
> **rajkd said:**
> I have already installed Ubuntu and now it does not allow me to install window at all
What do you mean? What does it say?

---

### Post by Midwest-Linux on 2007-09-12
I have Ubuntu 7.04 and Windows 2000 on one computer. Windows was on first, and then I installed Ubuntu using the text based installer. It was very intuitive and partioned around the Win 2000 OS. On start up (after installation) the grub gives you a choice for windows 2000 or Ubuntu.

 I think it is easier to install Ubuntu around windows, rather than the other way around. Try the test based installer for Ubuntu, my only suggestion would be is to install Windows first and then Ubuntu.

---

### Post by rajkd on 2007-09-13
I think I was not clear earlier. I had windows 2000 on my laptop. I installed Ubuntu on top of it. In the installation instructions of ubuntu it said the partition for Windows and Ubuntu will be done automatically, but it dint happen and windows got wiped out.

Now when I try to boot through windows CD. It does not read it and directly goes to Ubuntu booting.

---

### Post by Redache on 2007-09-13
Try checking in the BIOS to see if the boot from CD has been selected (Sounds so so obvious I know but sometimes it gets turned off along the way). Or as it's a laptop choose the key that'll get you to the boot menu and select CD Drive (Should come up with text saying setup = F2 and then Boot menu=F8).

Install Windows 2000 then you should use Gparted to do a manual partition all you need to know is to put in Ext3 in the partition type option and to set it's mount point as /

This will install Ubuntu onto it's own separate partition.

Make sure that while you are installing Windows select a partition size that gives you room to install Ubuntu and Windows so you minimise the chance for a mistake.

---

### Post by sstusick on 2007-09-13
Ubuntu attacked Windows? :-D

---

### Post by amixroed on 2007-09-14
i'm following this thread closly since i realy want to try out ubuntu but without removing windows :D

---

### Post by mips on 2007-09-14
> **rajkd said:**
> I think I was not clear earlier. I had windows 2000 on my laptop. I installed Ubuntu on top of it. In the installation instructions of ubuntu it said the partition for Windows and Ubuntu will be done automatically, but it dint happen and windows got wiped out.

Now when I try to boot through windows CD. It does not read it and directly goes to Ubuntu booting.

I don't think you followed the onscreen installations properly. When it caim to partitioning the drive you either selected "automatic" or use "entire drive" or something to that effect. That will wipe windows of your HD, you should have selected "manual partitioning". That way you could have resized the windows partition and created a new partition for ubuntu.

---

### Post by mips on 2007-09-14
> **amixroed said:**
> i'm following this thread closly since i realy want to try out ubuntu but without removing windows :D

Don't worry. Just resize your windows partition and then create a new partition for ubuntu after it with Gparted (which is on the livecd). When you run the installer and it comes to drive partitioning select the "manaul partitioning" option.

---

### Post by rajkd on 2007-09-14
I changed the setting in BIOS. I tried the following changes

1. Set CD-ROM as the default boot.
2. ESC+F12 to choose CD-ROM to boot from CD
3. Disable the other options in BIOS and only select the CD-ROM option. 

NONE of the above works. I am able to select the CD-ROM option for booting, but then it automatically goes to Ubuntu booting.

I have tried several combinations NONE worked for me now. The only way out seems to be Uninstalling Ubuntu somehow and re- installing both Windows and Ubuntu, but dont know how?

Yes you are right I selected the Autumatic Options and hence it wiped our windows entirely

---

### Post by K.Mandla on 2007-09-15
Moving to Installation and Upgrades.

---

