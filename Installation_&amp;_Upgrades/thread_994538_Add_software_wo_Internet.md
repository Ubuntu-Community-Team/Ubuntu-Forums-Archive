---
title: "Add software w/o Internet"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2008-11-26
How do I add software w/o internet connection to PC running Ubuntu?  I need to install kppp so I can use my Sierra 881 usb wireless device.  I can access internet with my laptop (OS = xp pro).  Once I get software downloaded to laptop, I can move to PC running Ubuntu via thumb drive or CD-ROM.

Modem I have for Ubuntu PC is external Creative modem blaster v92.  No linux drivers

John

---

### Post by dohmer911 on 2008-11-26
Hey, newbie here but i might be able to help,
There are many websites hosting linux apps such as [www.icewalkers.com](www.icewalkers.com) that you can download as gzip (.gz) then extract it. you can also get .tar files however they require compiling and i know nothing about that. (i think its the .tar extension). As for the modem, try downloading the scanModemtool (see: "https://help.ubuntu.com/community/DialupModemHowto/ScanModem") and it will give you information on the drivers that can be aquired for that modem, if its external modem im not sure if that will work.

I have same problem with the modem but mine is internal and i have dial up so haven't had much time to test the scanModemtool. Anyway check the ubuntu link above that pretty much explains everything.

Sorry if my information is misleading,
Hope all goes well

Adam.

---

### Post by benhur99ph on 2008-11-26
The easiest way to install files without being connected to the net and getting them from the repos is to download the .deb files. They're pretty much like the program installers in Windows. You just have to double-click the .deb file and it should install itself.

But there are programs that do not have this kind of installer. Like dohmer911 said, there are installers available in the tar.gz format and some of them requires compiling. 

In your case, I understand that you need to install drivers right? I'm not sure if there are .deb installers for that. If you want to see a list of .deb installers, you can go to [http://www.getdeb.net/]("http://www.getdeb.net/").

---

### Post by lswb on 2008-11-26
You can use a web browser to go to the site [http://packages.ubuntu.com](http://packages.ubuntu.com) then navigate to the version & category you are looking for to download the package. Once you transfer the file to your ubuntu system, if you use the gui you can just double-click the .deb file to install, or from cli, cd to the directory where the package file is and type "sudo dpkg -i name-of-package"

However it is likely that you already have enough cli tools installed to connect. According to this Sierra website,
 [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607)
after plugging in your 881,  /dev/ttyUSB2 will be the correct device node to reference it. In a terminal you can type "sudo pppconfig" for a text-mode ppp configuration editor, enter the same parameters they show for kppp when prompted and give it a try if you like.

BTW, the sierra driver modules are included with recent kernel versions, it should be recognized and the correct modules loaded automatically when the card is plugged in.

---

### Post by lswb on 2008-11-26
Also wanted to add that if your Creative Modem is an external USB model it is probably recoginzed as /dev/ttyACM0 and can be configured to connect via ppp with the pppconfig program as above. If it is by some chance an old serial port modem, the device node will likely be one of /dev/ttySx, where x is a numerical digit.

---

### Post by cigtoxdoc on 2008-11-27
Information on where to get packages, worked like a champ.  PC says that Sierra on USB0.  When I go to location, you suggested, kppp says no device.  Still cannot connect though using instructions posted by gmanigault.

Thank you for your help.

John

---

### Post by lswb on 2008-11-27
From the Sierra web page at [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607)

> 
Configure the modem by doing the following:           

   1. Click ‘Configure’ to switch to the Configuration window.           
   2. Select the ‘Modems’ tab and click ‘New’           
   3. Type in the modem name in ‘Modem name’           
   4. Select /dev/ttyUSB0 as the device. **Aircard 881 use /dev/ttyUSB2**. New Aircard 885E, MC885,Compass 885 use /dev/ttyUSB4


---

### Post by cigtoxdoc on 2008-11-27
Some how, some way, I have gotten my AT&T USBconnect 881 to work with a desktop PC running Ubuntu 8.04 p- the Hardy Heron.  After getting kppp installed via the deb file I downloaded with my WinXP laptop, I then went to the instructions at the Sierra wireless web page.  URL = [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607).  I only used the parts of the instructions dealing with kppp.

The undocumented critical instruction requires changing nm-applet 0.6.6 to recognize what kppp is trying to do.  I kept clicking until I got into something that let me set connection manually.  I probably could not repeat the steps, but as soon as I got the magic combination, the connection started working.

Someone who really knows what they are doing needs to document the process.  I stumbled through things and beat on them until I got results.

John

---

