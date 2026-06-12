---
title: "How to make my old GRUB to be activate on the startup ?"
date: 2017-06-17
forum: Installation &amp; Upgrades
---

### Post by yanshof on 2017-06-17
I have on my machine 3 linux that i installed. 
On installing the second linux (ubuntu 17.04) i define the GRUB as i needed. 


I installed the 3rd linux (ubuntu 16.04) and its override my GRUB that i edit and its loading other GRUB 


How to make the **first** GRUB to be loaded ? 


I try the run the commands below when i running the main linux ( 17.04 ) but nothing work and i still get the bad grub (grub of ubuntu 16.04) that i dont want 


    sudo update-grub
    gksu update-grub

---

### Post by westie457 on 2017-06-17
For best results boot into your main Linux (17.04) > open a browser > go to here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Choose the 2nd Option to install and run. Click the 'Advanced' button to see all the available options in the tabs.

You will probably have to purge and reinstall grub, Boot-repair will guide you through this: You will be prompted to open a terminal at some point. You must complete the suggested commands before you click 'Next' on the Boot Repair console.

---

### Post by oldfred on 2017-06-17
Boot-Repair will help you fix it.

But if you can boot into the main working install, you can just reinstall its grub boot loader to MBR.

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo parted -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub 

But be aware that each install on major updates of grub2 may reinstall that versions grub to MBR.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  

But you can change that so the other installs do not have a reinstall location, or reinstall to a partition which normally is not recommended.
      
 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions - in your case choose no location if available or partition where that install is.
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

