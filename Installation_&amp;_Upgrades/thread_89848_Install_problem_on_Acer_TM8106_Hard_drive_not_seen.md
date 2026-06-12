---
title: "Install problem on Acer TM8106: Hard drive not seen?"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by Lievre on 2005-11-13
Hello,

I tried to install Ubuntu on a Acer TravelMate 8106WLMi, as a dual-boot. It seems that it has problems to find my harddisk during the installation. 

This is how I did:
In Windows I re-arranged my partitions in order to make space for Linux Swap and root partitions. 
When I boot on the Ubuntu install CD, first I had problems with the PC-card and other hardware (ACPIthat he couldn't find and the installation was blocked at that point. 
Looking on these forums I found some starting options currently advised for TravelMate or other laptops. 
So I put the following commands in the boot to disactivate some materials:

acpi=off
pnpbios=off
noapic
nolapic
hw-detect/start_pcmcia=false

With these options the installation goes on after the language, keyboard etc settings, and it comes to the partition window.
Here, I only have the choice of "manually editing partition table", and then when I come to the window shown here (this is not a printscreen, just an image taken from the web), I have the different options (configure software RAID, etc), but nothing in the middle part, describing the current partition. 
The last options (finish partitioning, etc) are right under. 

As if he asks me to re-arrange partitions on an unexisting disk. 

Can someone provide me some help? As my message shows, I am not really an expert on Linux...

Three remarks:
- I'm using the distribution 4.10 of Ubuntu, because I do not yet have the 5.10. Do you think it could solve the problem to use 5.10?
- My hard disk is SATA 120Gb Seagate ST9120821AS
- I checked the HardwareSupport pages on the Wiki but found nothing about the Acer8100 that could solve my problem.

Thank you very much everybody for your dedication to this forum

---

### Post by Lievre on 2005-11-14
Hem, my problem isn't clear enough? There are some precisions lacking? Or nobody can provide any help...?
Thank you...

---

### Post by yesplease on 2005-11-14
Did you select the partition where you want to install (click on it)? You can 1) mount existing partitions, and create new ones / (root) /swap and /home, or 2) let ubuntu make partitions (guided partitioning, or something like that).

You move through the windows with arrows and tab, sometimes an item is not on screen till you use the arrows.

I also found this: [http://free32.free.fr/serendipity/index.php?/archives/7-Linux-on-an-Acer-Travelmate-8104WLMi-Part-I.html](http://free32.free.fr/serendipity/index.php?/archives/7-Linux-on-an-Acer-Travelmate-8104WLMi-Part-I.html) it recommends acpi=off noacpi and Gentoo (instad of Ubuntu and others :) )

---

### Post by Lievre on 2005-11-14
I cannot see any partitions, and there is no blank space between the editing options (configure software RAID, etc) and the ending options (finish partitioning, etc).

In fact my window looks like the image below:

Except that instead of guided partitioning, I only have the choice of manual editing of partitions, but when I try to select this option (or any other, such as configure software RAID or configure the Logical Volume Manager), he tells me that I have no logical volume, or something like that (I can check, but it means I cannot go any further).

---

### Post by daffy_ on 2005-11-17
My guess:

Your controller is not recognized, or there are no drivers for your controller in the kernel. This has nothing to do with the HDD.

First you should try with the latest Ubuntu (I guess it's running on the 2.6.12 kernel). 

Second, try downloading the network-install iso of SuSE 10.0. (Or Fedora Core 4). Both SuSE and FC has better support for "strange" hardware than what Ubuntu has. (In my experience, anyway).

Third, find out what controller is present on your motherboard and what driver it is supported by, and discover some way to specify the driver during install. (I don't know how to do this, I'm looking for the same info.)

---

