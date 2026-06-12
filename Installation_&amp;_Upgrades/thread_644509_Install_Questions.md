---
title: "Install Questions?"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by IK0N on 2007-12-18
I currently have Vista Business 64-bit installed on my which I only gave it 62 Gb of space. Now I am wanting to install Fedora Core 8 x86-64, and Ubuntu 7.10 AMD64. Below are is the partitioning schemes for both Fedora and Ubuntu that I came up with.

Should I add a /home mount point or anything else, or am I ok with what I have?

62 Gb of space:
400 Mb for /boot
8 Gb for /swap
53.6 Gb for /root
                                                          
specs on the machine
1 x MSI MS-171A86-002
1 x ATI Radeon HD 2600 (ATI Radeon M76 512MB)
1 x AMD TURION 64 X2 TL-66
2 x Kingston KVR667D2S5/2G R
1 x Intel Wireless WiFi Link 4965AGN
1 x Western Digital HD-WD2500BEVS

---

### Post by mikewhatever on 2007-12-19
You do not have to have a separate home partition. The only problem I can see is 8 GB of swap. That is a lot! You'll most probably never ever need more then 1-2 GB.

---

### Post by IK0N on 2007-12-19
Can Fedora and Ubuntu use the same /swap and /boot? 
The other problem I was having is after installing Fedora then installing Ubuntu; Fedora disappears but when I go to install Fedora again there is no need because the partition is still there. 
Any ideas on why it's doing that, or how I can fix it?

---

### Post by mikewhatever on 2007-12-19
> **IK0N said:**
> Can Fedora and Ubuntu use the same /swap and /boot? 
The other problem I was having is after installing Fedora then installing Ubuntu; Fedora disappears but when I go to install Fedora again there is no need because the partition is still there. 
Any ideas on why it's doing that, or how I can fix it?

Yes, there is no need for separate swap and /boot. Fedora does not exactly disappears after Ubuntu installation, but menu.lst of Grub boot loader gets overwritten by Ubuntu. Back it up before installing Ubuntu and then add the entries for Fedora manually to the new menu.

---

### Post by IK0N on 2007-12-19
If you don't mind can you tell me how to back up or copy the menu.lst I tried the stupid windows copy and past method but that did not work. I know there is a way to open up the file and copy the text but I'm not sure what the steps are to do so.

---

### Post by mikewhatever on 2007-12-20
I only know how to do it in Ubuntu, not in Fedora, so here you go. 

Graphical way: Press alt+f2, type <gksudo nautilus> (that will open Ubuntu's file browser with root privileges and enable you to access any partition and modify any file), navigate to your boot partition, find menu.lst and copy it somewhere safe.

CLI: Lets suppose your boot partition is named sda2 and your username is IKON. To get the backup in your home directory, open a terminal and copy/past the following command > sudo cp /boot/grub/menu.lst /home/IKON/menu.lst_backup

---

### Post by IK0N on 2007-12-20
I got it working thanks for all your help.

---

