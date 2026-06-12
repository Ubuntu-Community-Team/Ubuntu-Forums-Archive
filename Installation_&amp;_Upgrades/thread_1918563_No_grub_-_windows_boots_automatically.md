---
title: "No grub - windows boots automatically"
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by cespinal on 2012-02-01
Hi there, 

I just ran through a kubuntu installation in a friend's laptop. Everything seemed to be fine, but upon restarting after installation, no grub menu appeared. Windows boots automatically. 

Any ideas on how to solve this? 
Cheers!!

---

### Post by mankand007 on 2012-02-01
Try to reboot with the Kubuntu CD and reinstall grub again. Make sure to install grub to the MBR and not on the partition. That might work. And don't ever boot even once with Windows CD, cos even if you're not doing anything with it, it kills grub.

---

### Post by raja.genupula on 2012-02-01
hi while booting HOLD SHIFT key to get grub menu .from there choose Kubuntu and  change your boot time to 10 sec . 
Install Grub customizer from my signature . you can use it for all GRUB operations

 [http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)


If you dont get GRUB still after holding Shift key then look at my signature for grub recovery .

Let us know what you got .
All the best.

---

### Post by cespinal on 2012-02-01
thank you guys...will try these and report!

---

### Post by cespinal on 2012-02-01
A quick update: the iso had 1 file error... 

We are giving in another try now...

---

### Post by electroken on 2012-02-05
I have recently (today) had the same issue when installing Ubuntu alongside of a windows installation. The windows menu comes up as usual after installing ubuntu with no grub menu. The windows install on this computer has 3 choices to load a version of windows by virtue of having to install windows on the computer 3 total times before loading ubuntu.
I will try to hold the shift key to get to the grub menu after my last attempt to install ubuntu again. I have 2 partitions on the drive which has windows on one of the partitions and this time I made the 2nd partition be a free partition with the hope that ubuntu would install there. During the first part of the install from a dvd (from one of the magazines I get) there was no choice given about where to install ubuntu, only for a choice to install alongside windows (which I chose to do) or replacing windows or doing something else. I hope it works this time and I will report back here in a while to let you know.

---

### Post by electroken on 2012-02-05
Hello again. I did get the install to be successful finally. I used the hint and by hitting the shift key and finally getting the ubuntu to boot up. I did not get the initial grub screen at first, but I was able to get ubuntu to boot up. Then by running sudo update-grub it finally did find everything and make the menu like it normally would. I am not sure what finally worked, but it remains that I do now have the menu come up where I can choose ubuntu or windows as I figured would be the case. BTW my first install was 64 bit and windows install is 32 bit so I went back and booted into windows and deleted the partition for the free space and then rebooted the computer and installed a 32 bit version of ubuntu. I was still not able to get things to run until I used your hint so I am not positive that using the 32bit version made any difference. I do not think that was the reason for my problem.

---

