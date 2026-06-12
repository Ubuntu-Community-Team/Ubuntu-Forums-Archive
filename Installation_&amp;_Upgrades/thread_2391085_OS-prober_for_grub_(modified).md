---
title: "OS-prober for grub (modified)"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by jonnykickinbut on 2018-05-05
Wondering if anyone has seen a file for OS-probing in /etc/grub.d folder that does NOT create the additional menu options for "Advanced options" with each OS.  I only run a dual boot system, and I am basically intrigued by Ubuntu seemless implementation of Grub for bootloader among other things that takes a lot of the guess work out of the picture.  However what I would really like to see when running update-grub is a more narrowed list of options at the grub boot screen which could include Ubuntu, Advanced Ubuntu, and my Rescue Partition.

Right now in addition to those there is another entry which says Advanced Rescue Partition.  

I realize that modifying the script for os-prober is always an option, but what about a different script altogether that serves the same purpose as probing for OS but without this feature of creating useless additional entries in the bootloader configuration file?

---

### Post by oldfred on 2018-05-05
First thing I do is turn off os-prober in grub configuration settings and add my own 4-0_custom with whatever I want to boot. Sometimes I do copy some settings from a saved copy of grub that os-prober creates.

       sudo nano /etc/default/grub
#Add this line:
GRUB_DISABLE_OS_PROBER=true
sudo update-grub 


 Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
sudo -H gedit /etc/grub.d/40_custom
sudo -H gedit /etc/grub.d/40_custom
sudo nano -B /etc/grub.d/40_custom
Then do:
sudo update-grub 

Lots more details:
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

