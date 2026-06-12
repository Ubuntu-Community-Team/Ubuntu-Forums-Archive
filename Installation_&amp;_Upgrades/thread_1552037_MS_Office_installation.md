---
title: "MS Office installation"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by gpdas on 2010-08-13
Hi All, Can somebody tell how to install Microsoft Office 2007 in Ubuntu. I am not satisfied with OpenOffice.

---

### Post by TNT1 on 2010-08-13
You will need wine, or a VM...

---

### Post by mörgæs on 2010-08-13
Yes, that is the only option, but not all Windows applications run well in this environment. It is worth trying, though.

---

### Post by lordhaworth on 2010-08-13
Are there any specialist needs you have of Office? I would probably agree it is worth moving to MS Office as far as databases are concerned but I found (after initial disliking) that word processing/spreadsheet stuff is just as good in Openoffice (if not better, and backwards compatible unlike some software...)

---

### Post by ronnielsen1 on 2010-08-13
You don't say what version you're trying to install . This one is 2007

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

This is a link to other versions

[http://appdb.winehq.org/appview.php?appId=31](http://appdb.winehq.org/appview.php?appId=31)

---

### Post by lechien73 on 2010-08-13
You can check out Microsoft Office 2007 compatibility with Wine at this link: [http://uri.tl/12](http://uri.tl/12)

You will then need to click on each of the Office components individually (Word, Excel, Access etc.) to see how they work with Wine.

As to installing, make sure that you have Wine installed (Applications > Ubuntu Software Centre, search for Wine). The following Office 2007 installation instructions were taken directly from the AppDB entry on WineHQ:
> 
How To Install Microsoft Office 2007 

In current Wine, simply install as you would in Windows: 

Make sure your version of wine is set to Windows XP. 

Insert the disk.

Open the disk and right click on setup.exe and select "Open with wine windows program loader." Or open a terminal, navigate to the disk, and run the installer with:  

wine setup.exe 

The progress bar in the installer window may stop when it reaches about 2/3 of the way. The installation is continuing, even though the the progress bar is not moving. Wait for it to finish.

Note : No overrides are needed to install Microsoft Office 2007. However to get Microsoft Office 2007 to run correctly once it has been installed some overrides may be necessary. See below for instructions.

Post Installation Instructions

Once installed, one override is necessary. Without it, Powerpoint and Infopath with not start, and some dialog boxes in other Office apps will not display correctly. Follow the steps below: 

Open winecfg by going to Applications > Wine > Configure Wine. Or open a terminal and type:  

winecfg 

In the Libraries tab in the area labeled "New override for library" type in riched20.dll and click on Add.

You will see it appear in the list below. Now select the riched20 in the list that we just added and click on the Edit button.

Set it to Native (Windows) and click OK.

This will allow Powerpoint and the other applications to run correctly.

Note :Do not install riched20 with winetricks. Office 2007 installs its own version of riched20.

If Office is installed in a separate wineprefix, you can safely set the override globally. If not, set the overrides separately for each Office application

---

### Post by TNT1 on 2010-08-13
Running virtualbox XP, Office 2007 runs fine.

---

### Post by gpdas on 2010-08-13
What is this virtualbox XP?. How to install it  to run MS Office 2007 ? I am using Ubuntu 10.04. I face problem in 'Multiple Filter' and VLOOKUP function in OpenOffice CALC.

---

### Post by Sef on 2010-08-13
> What is this virtualbox XP?

A [virtual box]("http://en.wikipedia.org/wiki/VirtualBox") allows you to run other operating systems on your computer without dual booting.

---

