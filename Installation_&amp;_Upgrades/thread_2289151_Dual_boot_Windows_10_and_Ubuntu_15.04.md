---
title: "Dual boot Windows 10 and Ubuntu 15.04"
date: 2015-08-01
forum: Installation &amp; Upgrades
---

### Post by fernando52 on 2015-08-01
Hi

I made a fresh install of Windows 10 Pro and after that, I tried to dual boot it with Ubuntu 15.04 and everything was fine until I reached the part where I have to create the Ubuntu partitions. There was a message on top of the installer: "There is no other operating system in this computer", something like that. I shrank the Windows partition and left 100 GB for the installation of Ubuntu. I do not have UEFI firmware. I have made some research in the forum and other sites but since Windows 10 has just arrived there is not much information. 

Does anyone have ran into the same problem? How should it be fixed?

---

### Post by grahammechanical on 2015-08-01
I do not know the answer but I suggest that you load the Ubuntu lives session until you get to a desktop and then load Gparted. It is a partitioner. What partitions does it show? Take a screen shot and post the image in your thread. The picture will be more informative.

Regards.

---

### Post by oldfred on 2015-08-01
Did you leave Windows fast start up on. 
Or did you resize the NTFS partition and not reboot immediately so it can run chkdsk and update to its new size? 
Then the Linux NTFS driver cannot see it as it does not mount hibernated NTFS or NTFS needing chkdsk to prevent any damage.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by fernando52 on 2015-08-01
I got this picture running Ubuntu from CD. 
And, yes, I had Windows fast start up off. I have tried with Ubuntu 14.04 and 15.04; installer still doesn't recognize Windows 10.
Should I wait for Ubuntu 15.10 or am I missing something?

[https://lh3.googleusercontent.com/-8Yg2k6h7fBk/Vb1dESRd-XI/AAAAAAAAEmk/05MHz-SeDts/w769-h577-no/20150801_185004.jpg](https://lh3.googleusercontent.com/-8Yg2k6h7fBk/Vb1dESRd-XI/AAAAAAAAEmk/05MHz-SeDts/w769-h577-no/20150801_185004.jpg)

---

### Post by yancek on 2015-08-01
Your fdisk output shows the two windows partition totalling about 365GB.  Are you selecting the "Something Else" option under Installation Type?

---

### Post by fernando52 on 2015-08-02
Yes, I have selected "Something else" option and I can see the partitions. But I have read other peoole experiences with this kind of issue saying that after the computet reboots, GRUB doesnt show Windows option anymore. 
Is that true? Is that issue fixable? I wouldnt like to loose all my Windows setup

---

### Post by Rishabh Jain on 2015-08-02
If grub doesn't show windows option. You may want to try this [SIZE=2]https://help.ubuntu.com/community/Boot-Repair
[/SIZE]

---

### Post by oldfred on 2015-08-02
If your hard drive totally failed tomorrow, would you have a way to restore your data to a new system?
While not normal I have had hard drive fail within a year. But have several that are almost 10 years old, but not used daily anymore.

Or you should always have good backups.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

