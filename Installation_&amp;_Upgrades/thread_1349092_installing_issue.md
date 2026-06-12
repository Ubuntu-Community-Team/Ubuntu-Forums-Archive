---
title: "installing issue"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Nadurru on 2009-12-07
Hi All, 
 
Well I have been debating to install Ubuntu for some time now and finally decided to really give it a try. I have the 9.10 Live cd. I clicked on the install and got all the way to step 7, (so I thought, hey the install is easy enough) well after step 7 completed I got booted back to step 4. so I completed the rest of the steps again. well got booted back to step 4 again. When I started to complete the steps again I noticed the my partition stated that Ubuntu was installed. I exeted out of the install and rebooted my PC. Went to a blank screen and sat there. I did a soft boot and no dual boot option came up, I booted straight into Windows. 
 
Any ideas what I have done or not done to put me in this fix? 
 
Here are some of the statistics for my machine:
 
P7N SLI Motherboard
3.33 Ghz Intel Duo Core Processor
4gb 800Mhz Ram
1 external WD hard drive 1tb
1 internal WD hard drive 1tb
1 360 Gb internal WD Drive 
1 80 GB internal WD drive
 
Any assistance would be greatly appreciated.
 
Nadurru

---

### Post by darkod on 2009-12-08
First of all, if you don't remove the cd before reboot it will boot from the cd again. Second, unplug the external hdd unless you are trying to install Ubuntu on it. No need to be plugged when installing an OS.
Try to give more description like on which of the drives you told it to install. And if you didn't set up that drive as first in boot order, then it's normal that windows boots up. Probably your windows drive is still first in boot order and it just boots windows. It can't see linux installation.
With multiple drives you have to make a plan from whichdrive you want to boot, make sure the grub2 bootloader is installed there during installing ubuntu, and make that drive first option in BIOS.

---

### Post by Nadurru on 2009-12-08
I installed Ubuntu on the 1Tb internal drive. When in windows I don't see the internal drive that I installed Ubuntu on, so I'm assuming that all is well with it. I'll set the first boot drive to the Ubuntu drive and let you know what happens. 
 
I know that with dual boot options with wiindows the NTloader checks to see if there are more than one os to boot from, how does that happen with a windows os and Ubuntu installed?
 
Thanks for the info

---

### Post by darkod on 2009-12-08
Windows only finds windows OS. That's why Ubuntu (and other linuxes) come with grub (now grub2) bootloader which can boot boh linux and windows.

---

### Post by dhavalbbhatt on 2009-12-08
It seems to me that you have a bad CD. How did you burn your CD? Usually it is recommended that you burn at the lowest speed possible. Also did you do a check CD for defects test? What were the results of that? Given that you are able to boot using the LiveCD, I am assuming that your MD5 was OK, however, there is no harm in checking that again.

---

### Post by Nadurru on 2009-12-08
I redownloaded the the ISO file, burned it to the CD on the X1 setting and instead of going into the Live CD I installed after the language screen and everything went well. I changed the first boot device to the 1Tb internal that I installed to and rebooted. I got the dual boot screen and chose Ubuntu and it booted just fine. 

Thanks for all your help, now I am a happy camper. Now to see if I can manuver in it and get it running the way I want.

Nadurru

---

