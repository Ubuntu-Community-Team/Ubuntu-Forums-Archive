---
title: "I need to install Ubuntu 10.10 but it looks tricky"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by bluejimmy on 2011-04-07
Hi,
 
I'd like to install Ubuntu 10.10 in my laptop. So, I downloaded the iso file and burned into CD. I'd like to install into D drive since I use Windows Vista in C drive.
 
Below is the specification of my laptop.
Mobile AMD processor 2 G HZ, 1G RAM 32-bit Windows Vista Home basic 
Harddisk C : 46 G (18giga free), D : 10 G (10giga free) How can I make partition and where should I start with, either Beginning or End of existing partition? SWAP? I watched a few videos but stlll can't grasp clearly how to do.
 
I tried to boot w/ Live CD. But I didn't see the 4 different options: Try out without installing, Memory test, Ubuntu Disk test, Install Ubuntu, and Booting w/ harddisk. I had only 2 options; Try out w/o installing, Installing. Why is it so?
 
In addition, while booting w/ Live CD, I saw a message as following.
Error: b43.../firmware file not found.. something like this.. it was too fast to catch!!
However, ti went on and show its desktop screen. May I not be able to install in my laptop? Does my laptop have any faulty disk or memory? I wonder.
 
Finally, I use Wireless connection in the library so when I boot with Live CD, then internet is disconnected. Should I need to be connected before installing?
 
 
Thank you for your help.

---

### Post by Quackers on 2011-04-07
Welcome to UF.
You won't be able to install to the D: drive, as it will be a NTFS partition. If you have nothing in that partition you can delete it from within Windows. That will leave free space for Ubuntu to install into.
Obviously, if you have data in D: don't delete it :-) You may be able to make new partitions for Ubuntu separately.
How many primary partitions is Windows already using? Check that in Disk Management screen.
The firmware error could be related to a wireless network driver (Broadcom??). If that's the case you may need to connect to a router by ethernet cable until wireless drivers can be installed.
Finally, don't use the "install alongside" option in the 10.10 installer. It tends to eat Windows partitions!!!!
Instead select the "specify manually" option and create the partitions yourself.

---

### Post by Kirboosy on 2011-04-07
Welcome to the forums! :D

Well I think you were looking at older install CD how to's. Ubuntu tries to keep it straight forward and easy to install... If you can install MS Windows you can totally install Ubuntu.

I would select install alongside other operating systems and drag the slider to adjust how large you want everything to be. SWAP is generally 2x the size of your RAM but thats an old standard. Just let Ubuntu do its thing. I wouldn't sweat to much. 1 Gb sof RAM should run pretty good.

The B43 Error is not a big deal. It actually is your wireless problem. Its really easy to fix, just connect your computer to the internet over ethernet **after** the install. Then run the update manager (System-->Admin-->Update Manager) and once that finishes the Additional Drivers (System-->Admin-->Additional Drivers) If you are connected everything will work no problem. After all those updates/drivers you will need to reboot to initialize the new kernel. 

Once you are rebooted and wireless working go ahead and open Synaptic Package Manager (System-->Admin-->Synaptic) and type in the quick search box "ubuntu-restricted-extras" Mark the package for installation and Apply the changes. This will add media support for video and audio. Also flash is included in that package.


Hope that helps,
~Caboose

---

### Post by Sef on 2011-04-07
> In addition, while booting w/ Live CD, I saw a message as following.
Error: b43.../firmware file not found.. something like this.. it was too fast to catch!!
However, ti went on and show its desktop screen. May I not be able to install in my laptop? Does my laptop have any faulty disk or memory? I wonder.

The firmware was not installed. Click [here]("http://ubuntuforums.org/showthread.php?t=1604868") to read a sticky about installing it.

---

