---
title: "Install issues with 2 hard drives"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by Drott on 2008-07-14
OK, I encountered my first installation speed bump after successfully install 8.04 on my laptop with no issues.

I am trying to install 8.04 on my desktop which has 2 hard drives. The first 36 GB drive has XP and some games on it, and I would like to install Ubuntu on my second, 200 GB drive. I started the install process from the disk and got to step 4 out of 7 "Prepare disk Space" At this point the installation picked the 200 GB drive automatically (the first button that starts with "Guided....." and gave me the option to use the slider to select how much space I wanted to devote to 8.04. I selected several differant size options and each time I hit "OK" I got this error message:

"Resize Operation Failure"

"An error occurred while writing the changes to the storage devices. The resize operation has been aborted"


At this point I can not continue with the installation. I defragmented the drives before I started the install process and the 200 GB has 135 GB of free space on it. I am an extreme noob when it comes to Ubuntu and Linux as this is my first attempt to try a distro. (ultimately I would like to set up Edubuntu for my son) Any help in pointing me in the right direction would be greatly appreciated. My system specs are:

Pentium D 2.8 Ghz
2 GB ram
8800 GTS graphic card

If I am missing anything please let me know as I would love to start using this as my main OS and slowly reduce my Windows XP usage.

Thanks in advance.

---

### Post by untermensch on 2008-07-14
What format does the larger hard drive have?

---

### Post by Drott on 2008-07-14
> **untermensch said:**
> what Format Does The Larger Hard Drive Have?

Ntfs

---

### Post by Partyboi2 on 2008-07-14
What happens if you try to resize using gparted? You can do this by booting the live cd and at the desktop select System>Admin>Partition Editor. Once it is opened make sure to unmount the partiton you are wanting to work on and then choose the resize option.

---

### Post by Drott on 2008-07-14
> **Partyboi2 said:**
> What happens if you try to resize using gparted? You can do this by booting the live cd and at the desktop select System>Admin>Partition Editor. Once it is opened make sure to unmount the partiton you are wanting to work on and then choose the resize option.

When i go into the live CD and try to resize using the directions you gave I get an error message saying: "An error occurred while applying the operations"


Under the "Details" 2 items showed as errors. Here is what each line said under the details pane:

* Shrink /dev/sdb1 from 186.31 GiB to 150.91 GiB  "red error icon"
     * Calibrate /dev/sdb1 "green check mark"
     * Calculate new size and position of /dev/sdb1 "green check mark"
     * Check filesystem on /dev/sdb1 for errors and (if possible) fix them "green check mark"
     * Shrink filesystem "red error icon"
     * Check filesystem on /dev/sdb1 for errors and (if possible) fix them "green check mark"
     * Grow filesystem to fill the partition "red error icon"





Sorry about the format above, but I typed it all out. Now sure where to go from here.  :confused:

---

### Post by Partyboi2 on 2008-07-14
try running chkdsk /f in windows then try again. It probably wouldn't hurt to defrag again as well.

---

### Post by Drott on 2008-07-14
> **Partyboi2 said:**
> try running chkdsk /f in windows then try again. It probably wouldn't hurt to defrag again as well.

I defragged before I started this and chkdsk came up fine. I used partition Magic to create a 36GB partition but when I try to install again, it does not detect this partition automatically when the first partition option is listed when installing Ubuntu. When I select the "manual" option I see it listed as /dev/sdb5 NTFS. When I try to edit this partition I have no idea what options to choose. What should I select as the "use as:" option and also what "Mount Point" do I select? It also has a check box to "format the partition"

Anyway, thats where I'm at now. :(

---

### Post by Drott on 2008-07-14
Anyone have a good place to read up on the "Manual" option on step 4 of the install process (Prepare Disk Space)? Think this might be my only option at this point.

---

### Post by upchucky on 2008-07-14
I have found that doing one operation at a time is better, and i had to use qparted to work with my ntfs partitions.

I have the latest knoppix live cd that has both qparted and gparted, between using combinations of both i got my drives set up the way i wanted them. I used partimage to create a iso of ubuntu install, i save d that image to my usb drive and restored it later to the drive i wanted it on. since i had windows already backed up on the usb i did not care what happened to it, my windows files already were on the usb in their own partition, so it did not matter how i did the partitions on the main pc drives.

in addition to using the knoppix live cd to edit both windows and linux files, i have advanced supergrub to set up the win and ubuntu mbr when it gets borked by all the drive operations.

your choices are dictated by how you want your drives to boot, and what you want installed where.

typical is 
linux system ext3
linux home ext3
linux swap
windoze system ntfs
partition to store windows files ntfs

size of partitions are dependent on size of the drive and which you want to work with most. if you are keeping windows as a virus catcher which seems to be it's primary purpose in life, then it will not need a lot of room.
about 15gig

if you think you need lots of room for work in ubuntu the it needs about 10gig for system, 2x the size of your ram for swap, and lots for home partition

if you are not needing room for any files/programs that only windows can use that the windows files partition does not to be very big either about 20 gig.

the above partition listing is not in any particular order, it is just an illustration, *****you must install windows first then ubuntu, this is because windows is practicing world dominance and will corrupt the ubuntu install if ubuntu is installed first.*****

---

