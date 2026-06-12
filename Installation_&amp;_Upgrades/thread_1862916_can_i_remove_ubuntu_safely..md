---
title: "can i remove ubuntu safely?."
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by R_bd_23 on 2011-10-17
i wanted to try and install ubuntu but can risk my computer(warranty). but my friend asked me to reformat his comp, so he told that i can "try" and install ubuntu on it if i want. but i need to be sure.. its says that ubuntu can share its partitions of another OS. and i can make it 50 50. but if i ever did that can i return it to its normal state.. lets say its a winVista im using and i want to try and install ubuntu on it.. can anyone tell me a full guideline/instructions (preferably instructions)

---

### Post by graphius on 2011-10-17
two things. First, installing Ubuntu should not void your warranty, but unfortunately, many technicians are more comfortable in the windows world, so getting warranty work is more difficult and a bit problematic.
But more to your point, you have a number of options to "try" Ubuntu. You can even run Ubuntu off of the install cd without installing it. That is, [LIST=1]
[*]put the cd in the tray,
reboot the machine,
choose "try Ubuntu".
[/LIST]
This is not a great method because it will be slow (a cd is much slower than a hard drive) and it is more difficult to save files or customize Ubuntu.
You can run Ubuntu from within windows using something called Wubi. I have never used this.
The best method, and what I think you are wanting to do on your friends machine is dual boot. This is what I do for when I need to (very rarely) boot into windows. The procedure is the same as above except choose "install Ubuntu". It will guide you until you get to a screen that asks you if you want to install alongside the detected windows (I can't remember the exact wording). Again follow the instructions. I think Ubuntu is much easier to install than windows, and it gives clear instructions along the way.
If for some reason you decide to remove Ubuntu, just remove the two linux partitions (operating partition, and swap). At this point you can continue to use windows as if nothing happened.

---

### Post by Rubi1200 on 2011-10-17
Before you start doing anything make backups of all important data!!!

If you don't have the installation/recovery disks for Windows then try and get hold of them (ask the manufacturer if needs be).

And, read these guides first:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by kurt18947 on 2011-10-17
> **Rubi1200 said:**
> Before you start doing anything make backups of all important data!!!

If you don't have the installation/recovery disks for Windows then try and get hold of them (ask the manufacturer if needs be).

And, read these guides first:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

 Excellent advice. Another excellent idea would be to create an image of your entire disk before doing anything. That way no matter what you do to your disk, you can restore it to its exact state when the image was created. All your existing programs & settings will be preserved. If you have multiple partitions, it's a good idea to note the size and order of each partition. In the event you need to restore one or more partitions, you may have to recreate them using a tool like Gparted or similar before restoring. A widely recommended tool for creating images is Clonezilla. I haven't used it personally; I use a shareware program but clonezilla is widely used. [http://clonezilla.org](http://clonezilla.org)

---

### Post by Mark Phelps on 2011-10-18
> **R_bd_23 said:**
> ... but i need to be sure.. its says that ubuntu can share its partitions of another OS. and i can make it 50 50.
This is shrinking the original OS partition to make room.  Which generally is OK if the Windows version is XP, but if it is Vista or Win7, doing the same risks corrupting the Windows OS and rendering it unbootable.  In those cases, you need to use the MS Windows Disk Management utility to shrink the OS partition from INSIDE MS Windows.
>  but if i ever did that can i return it to its normal state.. 
Not easily.  

PCs that come preinstalled with Vista or Win7 often have a way of "restoring" that PC to the original Factory Condition.  This generally reformats the drive and reinstalls the original Windows version in its place.  But ... if you mess with the partitions, as you would when installing Ubuntu to its own partitions, tht can cause these Restore functions to get confused and not work.

The best way to prepare for a reinstall is to download and install the FREE version of Macrium Reflect (MR) on the PC.  Then, image off the Windows install to an external drive.  Finally, use the option to create and burn a Linux Boot CD.  NOW, you have the means to reinstall Windows -- should you need to do it later.

> lets say its a winVista im using and i want to try and install ubuntu on it.. can anyone tell me a full guideline/instructions (preferably instructions)

Others have better links to these than I ...

---

