---
title: "Ubuntu wont install!"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by Leomull87 on 2010-07-06
I want to dual boot my acer aspire m7711 which already runs vista with Ubuntu, keeping vista for games. I repartitioned my hard drive to create an unallocated space for Ubuntu. I created a usb stick instead of writing Ubuntu to disc and have no problem running Ubuntu live from the usb stick. However when I attempt to install Ubuntu I encounter problems.
 
The installation initiates fine and I select the language step 1 of 7, then my time zone step 2 of 7, then my keyboard set-up step 3 of 7 However the next step which should be step 4 of 7 and should ask me to select manual or automatic partitioning etc doesn't appear, instead step 4 of 8 appears which says Prepare partitions but without showing my disc drive and I am unable to perform any functions in the window. I can right click which gives the option of "revert" which does nothing and if i click forward "No root file system is defined. Please correct this from the partitioning menu." my disc does not appear in this window at all.
 
The steps can be viewed on this install guide  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) the step titled prepare disk space, step 4 of 7, is the step that is skipped when i attempt to install.
 
Any help with this would be much appreciated I am fed up with windows running slowly and Ubuntu has been great using the usb stick running it live.
 
Thanks in advance

I MANAGED TO SOLVE THIS PROBLEM MYSELF BUT LEAVING THIS UP FOR ANYONE WHO HAS THE SAME PROBLEM

Ubuntu Installer wasn't recognising my hard disk at all never mind the partition i had created for it. It turned out this was because it was deliberately ignoring my Hard disc.
Although I have a single hard disc, when my computer was first booted some nvidia software had prompted me to configure my hard drive and I had selected the "Recommended" setting but for some reason the recommended setting was to create a RAID striped array even though I didn't have more than one Hard disc. It took me a lot of reading through forums to discover that recent versions of Ubuntu ignore RAID arrays in the installation process. However I was able to enter the following code into the terminal and then launch the installation successfully:

sudo dmraid -r -E /dev/sda

sda is the name of my drive, to check the name of your own drive, whilst running Ubuntu live from usb or CD open System>Admin>Disk Utility

---

