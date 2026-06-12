---
title: "'Bout to lose it here. migrating from fedora 15 to ubuntu 11.04"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by Jverm on 2011-08-30
Alright, Ill start from the beggining. This is gonna be long so get comfortable...
I originally got this computer from a friend with linux mint 9.
I tried a bunch of different things because i wanted my ipod touch 4g (4.2.1 JB'D), and my roommates ipod nano 5th gen to be able to sync on the computer. Its not a new computer so i do not have the xp disk, If it even came with one that is. The partitions have nothing in them related to windows either. 
After failing with ubuntu 11.04 from mint, I decided to instead try fedora 15, Which i have running now.

Turns out fedora doesnt work with the devices either. So i went ahead and tried to install 11.04 from usb. Which lead me to another problem, The fedora f****in liveusb-creator doesnt work whatsoever. 

As a result of that problem, I used virtualbox to create a desktop of linux mint 11 and got the startupdisk creator to work in that. Got the usb all ready and rebooted from usb just to get that problem everyone else gets where it cant find a volume blah blah blah. so i edited the ui out of that file that everyone says fixes the problem and rebooted.It made it to the start menu with all the options like install ubuntu, Try ubuntu etc.. and it just took me back to the command problem with the "help" prompt. i pressed enter multiple times, nothing happened...

Im gonna throw this computer out the window pretty soon here...

Ragequit charging

---

### Post by oldfred on 2011-08-31
Not sure if you have a verified download or possibly video issues??

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

---

