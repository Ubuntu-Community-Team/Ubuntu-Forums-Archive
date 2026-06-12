---
title: "Dual boot windows 10 with Ubuntu on new Asus Core i3 Laptop"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by misswham2 on 2016-07-30
Good evening forum, I just purchased the Asus 2 in 1 13.3 Touchscreen Intel Core i3 6gb Memory 500GB Hard Drive-Black Hairline Laptop and I want to dual boot Windows 10 with Ubuntu.  I have done this for years but this is my first (I Think you call it) UEFI and I have seen videos of installations and they all are confusing.  I have Ubuntu on a flashdrive already and I used Unetbootin.  

Question 1.  Is using Unetbootin ok or do I have to use something else?

Question 2.  Do I have to go and resize the partition in windows by freeing up space first or can I do it the old Fashioned way by just booting up from the flashdrive in Ubuntu and just choose Install alongside Windows and size it from there?

Question 3.  I have seen them all go to systems in Windows and then disk management and then when you go to install, they are using Install alongside Windows and just clicking install after that but one video said that wasnt good to do it that way, Is that true?

Question 4.  Once they resized the partiion in windows then they choose something else in Ubuntu installation, they went and added swap space and then they clicked windows boot efi I guess to override that with grub and then installed.  Is that the best way.

Question 5.  My concern is, If I have to return this for a hardware problem and in fear of warranty not being upheld because I tinkered with the harddrive partition, can I just boot back into windows and do a recovery and will it erase all of the harddrive and reinstall                          windows 10 over the COMPLETE harddrive and it will erase Ubuntu and take the laptop back to the original windows 10 only?

---

### Post by yancek on 2016-07-30
The official Ubuntu documentation page on dual booting windows/Ubuntu UEFI is at the page below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
1.  unetbootin should work
2. Shrink the windows partition from windows to create unallocated space.  Reboot windows and run chkdsk at least once.  Do not use the install alongside option
3.Use the manual option "Something Else"
5.I hope you would have a recovery disk for windows before you try to install Ubuntu.  Yes, it sets to factory defaults which means any changes you have made and any data you have such as personal files will be gone so make sure you have a backup.

---

### Post by misswham2 on 2016-07-30
I went to the UEFI link and it mainly is telling me about windows 8.  Is there a tutorial on installing on windows 10?  I found how to get into the boot menu and some tutorials on youtube are telling to disable the fast boot option.  I dont know which one to follow.

---

### Post by ubfan1 on 2016-07-31
Windows 8 and 10 instructions are pretty much the same.  There may be a boot speed/delay option in BIOS/UEFI Settings which is best to normal/non-zero so you have a chance to hit a function key at power-on if necessary.  Within Windows, there is a power option to turn off fast boot, which prevents  the shutdown from hibernating.  This option is harder to find in Windows 10, but keep digging and you can find it.

---

### Post by oldfred on 2016-07-31
Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

With my new Dell, it wanted a full Dell backup, a full Windows backup and I used Macrium Reflect to do a full image backup. Multiple DVDs & flash drives. I also made a repair/recovery flash drive just to make repairs.
Windows 10 likes to turn its fast start up on (hibernation) and grub will not then boot it. With UEFI you can directly boot Windows from UEFI boot menu or one time boot key menu which may work. But best to have a Windows repair flash drive.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm) 

           
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)

---

### Post by misswham2 on 2016-08-02
I've done is successfully.  I went to the boot menu and turned Fast Boot off and everything is working fine so far.  Thanks for your help.

This is the video I followed

[https://www.youtube.com/watch?v=MYiytR-1tYU](https://www.youtube.com/watch?v=MYiytR-1tYU)

---

