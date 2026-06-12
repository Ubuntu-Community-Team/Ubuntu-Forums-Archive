---
title: "Tutorial: Installing Ubuntu without CD"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by augustuen on 2010-04-17
**This tutorial will teach you how to install Ubuntu (any version) without a cd/dvd**

[I]You will need some things: 

1. A computer with a operating system on it

2. A Ubuntu .iso file

3. VMWare Workstation (I use VMWare Workstation 7.0)

4. Free space on your hard drive (a blank one is recommended)[/I]

Step 1. Partition your hard drive (don't format or give it a drive letter (Windows)).

Step 2. Open VMWare Workstation and create a new virtual computer.

Step 3. Choose "Custom(advanced)", click next.

Step 4. Click next, Select your .iso image (or choose "I will install operating system later", I had problems with my password not beeing long enough, click next.

Step 5. Select Linux as the operating system and Ubuntu as the version. (Or a different distro), click next

Step 6. Give it a name, the default folder path is good, click next.

Step 7. If you have several processors or cores, you can add some more here, but if you don't, then just click next.

Step 8. Give the virtual machine a good amount of memory, half of the total RAM you have installed is good, click next.

Step 9. Select your network connection, I recommend option two (NAT), click next.

Step 10. Select the I/O adapter type (I'll go with the recommended one), click next.

Step 11. Select "Use a physical disk (for advanced users)", click next.

Step 12. Choose your hard drive from the drop down box (if you are installing it on a partition on the primary hard drive, select physical drive 0), select the option "Use partition" (if you made a partition, if not, select "Use entrie hard drive"), click next, and select the partition you wish to install on.

Step 13. Click on the name you gave the virtual computer, click inside the box quikly and hit F2, then go to the boot tab, and use + and - to move "CD-ROM" to the top, then move over to the "Exit" tab and hit enter twice, the virtual machine will start up, and should boot up into the live CD (if you downloaded a live CD).

Step 14. Go trough the normal installation as usual, don't worry about using the "entire" disk when installing, it wont effect the other OS on your computer if you choosed a blank hard drive or a partition ;) 

Step 15. Shutdown your computer, on start up, hit F12 or what ever button that opens the boot device menu, if you don't have one, just open the BIOS setup (normally the Del or the F2 key)

Step 16. Go to the "Boot" tab, and select your secondary hard drive as the first boot device, and your primary as the second (if you have to set the hard drive boot priority, do this and don't select the hard drive twice), go to the "Exit" tab and choose "Save and exit", your computer will now reboot, and it should boot into Ubuntu. 

Step 17. Enjoy Ubuntu, and send a link to this tutorial to all your friends and visit [my website.]("http://augustuen.ush-clan.co.uk")

---

