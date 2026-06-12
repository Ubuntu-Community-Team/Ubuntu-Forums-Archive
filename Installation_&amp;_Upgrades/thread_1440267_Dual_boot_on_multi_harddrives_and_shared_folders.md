---
title: "Dual boot on multi harddrives and shared folders"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by BigBuntu on 2010-03-27
I need advise on setting up dual boot Ubuntu and windows 7. I have 3 hard drives installed on my PC. 1TB & 2 pcs. 500GB.
 My goal is to setup an OS on each 500GB and the a Share 1TB for common folders like Documents – Pictures – etc.
 So starting from scratch what is the best approach and how do I succeed in making a shared driver with the documents accessible from both systems.
 Can someone make me a guide – I a couple of time now with no luck. There is a problem when booting so do I need to install the desks in a different order!?
 Right now the order is:
 sda 1TB
 sdb 500GB
 sdc 500GB
 Maybe is it necessary for the 1TB to come in last on a boot?
 

 Furthermore when I setup the 1TB for NTFS, the it does not register in Window..... how does that work. It a mother f%#£@........ and it really getting on min nerves.
 

 Please help and with as precise description as possible.

---

### Post by raymondh on 2010-03-27
This is assuming there are no OS' installed yet .....

Feel free to have another member/poster verify this.

1.  I would change the order in BIOS.  500 - 500 - 1tb.  Note the type designators as you might get confused with both 500's.
2.  Install windows in the first 500 hd
3.  Boot into windows and update; making sure everything is ok.  For mounting the 1TB to windows, I think you need to assign it a drive letter.
4.  exit and shut down
5.  Start up ... access quick BIOS (a start-up menu where you can quickly change the HD booting order).  Otherwise, you'll have to access BIOS again, change the order and save & exit
6.  Make the OTHER 500gb as first to boot in BIOS
7.  Install ubuntu on it.
8.  In step 7 of the install process, click advanced and 2x-check that GRUB is indeed installing in the MBR of the Ubuntu hd.
9.  Finish the ubuntu install ... reboot without changing BIOS order ... update ubuntu and if needed, GRUB.
10. Assumning that the 1TB is already formatted in NTFS, ubuntu ought to auto-mount it.  If not, mount the 1TB .... just search NTFS in software center (or add/remove)
11. Keep the boot order as is.  Ubuntu - Windows - 1TB.  What you'll have is GRUB as your main bootloader accessing both OS ...... while you still retain the original windows configuration and bootloader.

Best of luck.  As always, have a back-up of your files.

---

### Post by oldfred on 2010-03-27
+1 on raymondh's suggestions.

Are you making the 1TB drive as one large partition or several smaller ones? Links to several suggestions on mounting windows partitions. You can directly mount in /home or mount elsewhere and link folders into /home.

[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

My version is having most of my data in EXT# partition but you can do the same thing (Link folders) for data in NTFS.
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of above blog
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by BigBuntu on 2010-03-27
Thank you for the quick responses.


 I changed the hardware setup so the to small desks come before the bigger. That seams to do the trick. Now both OS are up an running although – I was a bit quick on the Ubuntu setup – while I missed the last ”point 8 on Raymondh&#347; great description” so my GRUB is placed on the first desk and not with Ubuntu resulting in a prolonged boot...... (I will have to do everything one last time I guess, but everything is much easy'er the 2nd time around)  
 On the issue of sharing of folders – Success I assigned a drive letter in Windows and Vola – my folders Document, music, etc. created and then back in Ubuntu deleting the once already assigned and copying the back in to ”places” from my storage desk. This is simply fantastic. I guess this is the closes I ever get the the perfect system setup. (of whats available today) I am a very happy Ubuntu user with Windows as a need with a very few but necessary applications.
 

 Thank you – problem solved!:D

---

### Post by oldfred on 2010-03-27
You do not have to reinstall to move grub to the other drive.

reinstall from working system - first find Ubuntu drive change to sdb if that is correct:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

Then you can change drives in BIOS.

---

### Post by raymondh on 2010-03-27
> **oldfred said:**
> You do not have to reinstall to move grub to the other drive.

reinstall from working system - first find Ubuntu drive change to sdb if that is correct:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

Then you can change drives in BIOS.

likewise ... +1 on OldFred.

happy ubuntu-ing and congratulations on your set-up =D>

Raymond

---

### Post by BigBuntu on 2010-03-28
”Ignorance is bliss” but VERY time consuming.   ;)


   	 	 	 	 	 	  I have Ubuntu as my main OS for 2 years now. (the only way to fly) Of cause, always have an bacata minimize with the only real threat back is if my hd breakdown.  
 
):P

---

### Post by oldfred on 2010-03-28
With multiple drive some like to have multiple systems. I have 3 drives and 4 systems with at least one on each drive. I have 3 ubuntus and windows. Since all my data is not in the operating system partition my operating systems are using about 5GB out of 20 allocated. I have my old Ubuntu (Jaunty), my current install (karmic), and the current beta (lucid) just to learn what is changing. I will install lucid over my jaunty and continue to rotate installs. I also have space for other systems which I plan on trying,, without having very large drives.

Some install an operating system just as insurance:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

