---
title: "Computer won't recognize DVD"
date: 2014-07-04
forum: Installation &amp; Upgrades
---

### Post by Kenc3 on 2014-07-04
I have been trying for 3 days to get my computer to boot from my live DVD for Ubuntu Studio 14.04.
I have an Acer Aspire All-in-one and I have it set to boot from a removable device. It ignores that and goes to windows 7 64 bit. I tried opening the DVD and then opening Wubi and when it says to reboot, the computer still goes back to Windows. Have they taken over my computer?
 I further found that if I turn CSM to Never in the Boot menu the DVD will load however there is no Internet so I am sort of dead in the water. They also do not load any programs from the DVD.
 I almost feel like Microsoft is punishing me for trying Ubuntu.

Ken

---

### Post by yancek on 2014-07-04
Are you trying to use WUBI (Windows UBunti Installer) on your windows?  It is apparently no longer supported and not expected to work on 14.04. It won't work on windows 8 but maybe you can get it to function on windows 7.   I've never used wubi to install Ubuntu but everything I have read about it tells me that it installs inside windows and creates a boot entry in the windows bootloader to boot windows.  Have you completed the installation using wubi?  got a message that it was successful?  been told to reboot?
The wubi guide at the Ubuntu site below seems pretty detailed to me:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Kenc3 on 2014-07-05
I found a thing at the top of the boot options that has the choices of always or never. It was set to always and I changed it to never and the DVD opened up. The problem then was that the DVD I have does not seem to have any programs on it. I cannot get the Internet because there is no firefox or anything else. It took me over 12 hours to download Ubuntu 14.04 and then I burned it to a DVD. It said it was a few GB nut when I looked at the install on the DVD it said a few KB. Something is definitely not right. I have been trying to get some of the older disks to work and they seem to stop with the wubi.
 I have been away so long that I am not sure I can even do this anymore. There is a book on Kindle that says you need to turn off Secure Start and another one if you are using Windows 8. I bought this computer awhile back with no operating system on it. Now I want to change it and it looks like Microsoft has modified it so much that it will only take their stuff.
 I haven't backed up my files yet so I don't want to take the chance of downloading it alone. Maybe that will be my next step.
 I have been doing this for the past 4 days and am just now beginning to ask questions on here. I am lost..
Ken

---

### Post by Kenc3 on 2014-07-05
This may be my last post for awhile. I made a DVD with my files on it and am going to press the button to install Ubuntu 14.04.
I am praying that it works and I have a system to contact you with the results in awhile if not a few days.
Ken
UPDATE: It looks like it is installing 14.04 and erasing everything else. It is either adding all those programs or bringing over all my files from Windows.(That would be nice.)
I have a back up disk of the files so that shouldn't hurt anything.
Ken

---

### Post by Kenc3 on 2014-07-05
After 5 days I am finally seeing a little light at the end of the tunnel. My computer is going slow but it is running on Ubuntu 14.04 Studio. I would have rather had one of the supported ones but this will do if I can keep it runnng.
I had to find a hidden icon on the bottom of the screen to locate Firefox and then go from there.
 I still haven't seen Libreoffice or any of the other programs that are supposed to be there. It may still be uploading.
 I did manage to let it do its thing last night and got up later in the night and turned the computer off.
 Hopefully things will speed up and a lot more will appear as the day  goes on.
Ken

---

### Post by yancek on 2014-07-05
The Secure Boot and Fast Boot which usually need to be disabled are only used on computers which come with windows 8 preinstalled, AFAIK.
I haven't used the most current release of Ubuntu Studio, but about a year ago I downloaded and installed it and the downloaded iso file was about 2GB.  Twelve hours to download doesn't seem right, unless it is a computer that is 10 or more years old.

On Ubuntu Studio, do you see any tabs at the top of the Deskktop, Applications, Systems, Places?  Not sure what the current Desktop should look like.
If you are using wubi to do this, I'm not sure it will work as it isn't really supported anymore but, you may get lucky.

---

