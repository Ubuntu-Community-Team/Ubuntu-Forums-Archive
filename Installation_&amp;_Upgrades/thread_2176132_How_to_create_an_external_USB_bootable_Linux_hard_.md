---
title: "How to create an external USB bootable Linux hard drive (without dual-boot)"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by rick_dunn2 on 2013-09-23
I wrote this as a technical document on April  25th, 2008; I just used this exact method to install Ubuntu 13.04 on a  WD external USB 2 TB harddrive and it worked flawlessly. I will give you  this one piece of advice... 

_**Follow this to the letter and it will work for you and if you do not I   am not responsible for the end result**_
 
  The topic of a bootable external USB Linux hard drive (without  dual-boot) is an area that is not well documented. A simple Google  search shows many articles, blogs and forum posts written on this topic,  all of them discuss setting up dual-boot strategies. While I did not  specifically test a USB Thumb Drive and did not intend to address this  device in this article, I see no reason why this would not work for  Thumb Drives as well. This article was written with the goal of defining  an alternative to the traditional dual boot concept and keeping each  operating system isolated from each other. While the dual-boot scenario works, this can cause undesirable issues  when grub installs its files on the external drive. Should Grub install  its files to the external drive, the drive must be connected before  booting the computer or you will receive a Grub 17or 21 error. Based on  the testing I have done in an effort to achieve the desired results, I  did not want a dual-boot on either the laptops operating system  (internal hard drive) or on the external USB drive.


  This document applies to all Linux distributions that I have tried  since writing the original document in 2008. You will want to use laptop  or desktop hardware in which the BIOS supports booting to a USB device.
  Why would you want to do this?

  Small foot print USB powered external drives are very obtainable and  affordable. These drives come in various sizes with the most common and  cost effective today being 500GB to 1TB. This gives you the ability to:


[LIST=1]
[*]   Test new OS versions 
[*]Test multiple OS types 
[*]Carry multiple working OS’s with you in the field 
[*]Lab issues in the field 
[*]Test patches 
[*]Perform demonstrations 
[/LIST]
   
All of the above and more without risking the OS installed in your  laptop or desktop. While this solution may not be right for everyone;  this will provide you with more options.
  There are several ways to achieve the results described herein; I  will describe two of these methods and you can choose which method works  better for your scenario.
  [B]
Method 1:[/B]

  
[LIST=1]
[*]Insert the Linux OS Install CD/DVD 
[*]Reboot the computer 
[*]Enter the “Setup Menu” 
[*]Disable the internal hard drive 
[*]Save settings and exit 
[*]The computer will reboot so you can see the Post Screen 
[*]Push the appropriate key (F12 for Dell Laptops) to bring up the “One Time Boot Menu” 
[*]Select boot from CD/DVD 
[*]Install Linux OS (Follow your normal install procedure) 
[/LIST]

The only device that should appear is the external USB drive
  
***Note: Since the internal hard drive is disabled the Linux OS will  have no choice, it will install all of the required components for the  external USB drive to become a bootable device.***
  
_***When the install has completed:***_

  
[LIST=1]
[*]Remove the Linux OS Install CD/DVD 
[*]Reboot the computer 
[*]Enter the “Setup Menu” 
[*]Enable the internal hard drive 
[*]Change the boot order to resemble 
[*]USB Device 
[*]Internal Hard drive 
[*]CD/DVD 
[*]Save settings and exit 
[/LIST]
 
The computer will reboot so you can see the Post Screen (Let the system boot as normal)
  The machine will boot into your newly installed Linux OS and will  have no knowledge or connection to the OS that is installed on the  computers internal hard drive.
  [B]
Method 2:[/B]

  
[LIST=1]
[*]Insert the Linux OS Install CD/DVD 
[*]Shout down the computer 
[*]Remove the internal hard drive 
[*]Start the computer 
[*]The computer will boot so you can see the Post Screen 
[*]Push the appropriate key (F12 for Dell Laptops) to bring up the “One Time Boot Menu” 
[*]Select boot from CD/DVD 
[*]Install Linux OS (Follow your normal install procedure) 
[/LIST]
 
The only device that should appear is the external USB drive
  
Note: Since the internal hard drive was physically removed the Linux  OS will have no choice, it will install all of the required components  for the external USB drive to become a bootable device.
  When the install has completed:

  
[LIST=1]
[*]Remove the Linux OS Install CD/DVD 
[*]Shut down the computer 
[*]Install internal hard drive 
[*]Enter the “Setup Menu” 
[*]Change the boot order to resemble 
[*]USB Device 
[*]Internal Hard drive 
[*]CD/DVD 
[*]Save settings and exit 
[/LIST]
 
The computer will reboot so you can see the Post Screen (Let the system boot as normal)
  The machine will boot into your newly installed Linux OS and will  have no knowledge or connection to the OS that is installed on the  computers internal hard drive.
  [B]
Issue:[/B]
  
During one of my tests, after all of the above steps were completed  Linux on the USB External Hard drive would not boot. The computer did  not see the device as a bootable device therefore the machine booted to  the OS installed on the internal hard drive.
  [B]
Solution:[/B]

  
[LIST=1]
[*]Plug the external USB device into the USB port on the computer 
[*]Place the Linux install CD/DVD in the CD/DVD drive on the computer 
[*]The computer will boot so you can see the Post Screen 
[*]Push the appropriate key (F12 for Dell Laptops) to bring up the “One Time Boot Menu” 
[*]Select boot from CD/DVD 
[*]The main install screen will give you the option to repair the Installed OS (during my tests this did not have any unwanted effects on the computers internal hard drive or the OS installed on it) 
[*]Once the repair is completed remove the CD/DVD from the CD/DVD drive 
[*]Reboot the computer 
[/LIST]
   
The computer should boot to the OS installed on the external USB  drive without issue. However you need to understand the BIOS in your  machine; I would suggest removing any USB devices except for the hard  drive before booting the computer.

---

### Post by sudodus on 2013-09-23
Nice tutorial :KS

You can consider having it in the [Tutorials]("http://ubuntuforums.org/forumdisplay.php?f=100") Forum too (if you want to do that, press the Report Post button and ask a Forum admin to move it). An alternative is to convert it to an Ubuntu Wiki page and link to it and from it.

I intend to link to your tutorial from this wiki page [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) if you don't mind.

---

### Post by rick_dunn2 on 2013-09-23
I don't mind at all!

---

### Post by MethosCR on 2013-09-23
Great post. Thanks a lot.

---

### Post by rick_dunn2 on 2013-09-24
[**[COLOR=#000000]MethosCR[/COLOR]**]("http://ubuntuforums.org/member.php?u=465683"), you are most welcome!

---

