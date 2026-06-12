---
title: "[SOLVED] Install on External USB Hard Drive HELP"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by darren_07 on 2007-09-10
Hi all..

Im new at using Linux and want to install it for the first time... I Have been playing around with the Ubuntu Live CD for a few days now and decided i wanted to install it on an external USB Hard Drive..

The problem im facing is that the external hard drive i have is and 80GB harddrive and i still require to use some (most ) of this space for backup in windows..  I can start with the drive empty work from there however i only wish to install Ubuntu on about 10GB of this drive until im comfortable using it..

Im having trouble getting the installation to only accept the external drive and ignore the internal (of the laptop) drive and only partition with a smaller than 50% of the external drive space.. 

If someone has done this and can offer some step by step instruction on how to do this you would make my day....

Cheers
D

:confused:

---

### Post by merlinus on 2007-09-10
You might try gparted live cd to make the partitions before attempting install.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by darren_07 on 2007-09-10
You might try gparted live cd to make the partitions before attempting install.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
__________________
-merlin 


Thanks for the quick reply... :)

ill give it a go....

---

### Post by darren_07 on 2007-09-11
for anyone who may wish to do exactly what i did. The easiest was that i have found is to physically disconnect all other hard drives.. Then boot from the Live CD and install on the USB hard drive using the guided partition.  This was you are 100% you are only installing on the USB hard drive and the install is not trying to get space from C: drive as i found it was... Then modify you BIOS to allow for boot from usb before the internal hard drive.. Once installed reconnect any other hard drives and your good to go... 

cheers
D
:)

---

### Post by shakyone on 2007-09-11
Darren, I put a nice simple summary of the method that works here:

[http://ubuntuforums.org/showthread.php?p=2859767&mode=threaded#post2859767](http://ubuntuforums.org/showthread.php?p=2859767&mode=threaded#post2859767)

The info is also below.  Follow this then run GPARTED via LiveCD or use PartitionMagic on the USB, not while Ubuntu is running..  

I have been running Ubuntu exactly as you described for about two years now.

[INDENT]Re: HowTo: Install Feisty on a bootable USB Flash drive
Fellas, you are doing this the hard way. Use the live CD.

I spent this weekend smoothing out how to install Ubuntu 7.04 to a external USB 2.0 hard drive. The procedure also works for a USB thumb drive, 8GB or larger. I do not recommend running via a USB 1.1 connection. You don’t have that kind of time.

Prep work:
1. Download the LiveCD iso and burn to CD.
2. Prep your USB drive by deleting all partitions, no matter what kind they are.
3. Disconnect your internal hard drive(s).
4. Change your system BIOS boot priority by whatever procedure required for your specific hardware, to:
1. CD
2. USB
3. Hard drive.

If you cannot set the USB, because your motherboard is too old, this entire method will not work for you.

5. Connect the USB drive
6. Insert the LiveCD and boot your system
7. When the Gnome desktop is visible and the Boot is complete select the following pull-downs from the menu:

System > Preferences > Removable drives & media.

8. In the Removable drives & media window deselect:

* Mount removable drives when hot-plugged
* Mount Removable Media When Inserted
* Browse Removable Media When Inserted

9. Close this window.
10. Select the Install Ubuntu Icon and run through the install routine steps. When you get to the step regarding the hard drive, the easiest method is to select Use Entire Disk.
You can partition out any space you require later.
11. Run the installation. Even though the system says it will install GRUB to (hd0) the only drive connected is the USB drive, and it will place it in the right spot. Choosing sda or anything of that nature is not required when using the new install cd. It puts it on the right disk, when no other disks are connected.
12. Restart the system when it is done.[/INDENT]

Enjoy.

Pete.

---

### Post by darren_07 on 2007-09-13
Pete..

In your step 10. you said you can partition the drive later... what do you use to do this??
Do you do this from within Ubuntu?
cheers
D

---

### Post by logos34 on 2007-09-13
I believe he meant you can shrink the main/root partition down later to make room for additional partitions.  Since it has to be unmounted, you'll need to use gparted on the ubuntu live cd or the gparted live cd.

---

### Post by shakyone on 2007-09-15
Darren,

     Logos is spot on.  I actually have more than one version of ubuntu around my house, so yes, I use gparted from a different machine, and it works great. It should also work just fine from the LiveCD.  I would recommend though, 

keep the internal hard drive removed, 

boot using the liveCD, 

then uncheck the auto mount features before you attempt to use the GPARTED program on the LiveCD.  (same as step 8 in my above post).

Then plug in your USB drive to re-partition.

I don't think it will work if the USB drive is mounted by the automatic settings that are defaulted on with the liveCD.  

Enjoy.

Pete.

---

### Post by darren_07 on 2007-09-16
logos34 and shakyone

Thanks guys.. I tried this on the weekend and its all working well and as it should... 

Thanks heaps for you help.. i now can begin down the Path of learning Linux.. :)

Another quick question.. Do you guys know of any good software development software for Linux?? i have see some ages ok similar to Visual Studio (windows) however i cant remember what they were??


cheers
Darren

---

