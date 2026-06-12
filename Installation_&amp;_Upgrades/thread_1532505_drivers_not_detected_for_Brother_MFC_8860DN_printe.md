---
title: "drivers not detected for Brother MFC 8860DN printer"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by bill56 on 2010-07-16
Hello everyone.  I have just installed Ubuntu 10.04 LTS on my AMD 64 bit desktop.   I have a usb connection for my Brother MFC 8860DN printer. I used the synaptic package manager to install the printer drivers ubuntu already had in their repository for my printer model.  When I connect my printer to the computer Ubuntu recognizes the model, but cannot detect the printer drivers I have already installed. The printer drivers were installed to /usr where a Brother folder was created.  the Cupswrapper and lpd files are in the Brother folder.  How can I get the system to detect its own files so I can get the printer to work?

---

### Post by davidmohammed on 2010-07-16
this is a very old [thread]("http://ubuntuforums.org/showthread.php?t=590793") - but there has been some recent activity on the thread saying that the original instructions work.  Suggest, has a read to see if anything there helps.

---

### Post by bill56 on 2010-07-19
Thank you for your response David. Your reply is helpful, but it doesn't really address my question completely. Ubuntu 10.04 does have drivers in synaptic package manager for the brother mfc 8860dn printer. I installed the drivers for that printer using synaptic package manager. When I plug in my brother mfc 8860dn printer using a usb cable Ubuntu identifies the printer and starts a "search for drivers", but Ubuntu does not find the drivers I just installed. I don't understand how Ubuntu would not find the drivers it has for my printer in synaptic package manager? If I installed the drivers for my printer from Ubuntu's software repository, I would think Ubuntu would find the drivers. Could the system be looking for the drivers in a directory other than the one the system placed them in? Any help would be appreciated.

Bill56

---

### Post by oldsoundguy on 2010-07-19
Linux is not Windows.  You don't have to install a driver before you plug in a printer.

---

### Post by bill56 on 2010-07-20
Yes I understand what you are saying, but the point is that Ubuntu does have a GUI that does search for drivers when the system tries to install my printer.  How can I get Ubuntu to find the drivers through its "search for drivers GUI" that it already has installed for my printer?

---

### Post by oldsoundguy on 2010-07-20
Plug in the printer
turn it on
boot up
go to system> administration> printing
click add>
find your printer and install the driver
close
print

---

### Post by bill56 on 2010-07-21
I did Plug in the printer and turn it on and boot up and go to system> administration> printing click add>, but it did not find my printer driver.

There must be some step missing or some other way to install a working printer driver for my Bother MFC 8860DN printer.  I used the Brother Corp instructions to install the drivers, but it simply didn't work. It seems that directories and or files have to be manually created.

---

### Post by davidmohammed on 2010-07-21
... bill56 - I think you have correctly guessed that the synaptic driver doesnt create and configure your printer correctly.

I suspect you'll need to follow the link I gave you - when you come to "install" the .deb files, I would presume that the install from synaptic would cover that step.

---

### Post by bill56 on 2010-07-27
I have followed the instructions on the thread that  davidmohammed kindly suggested. The printer lpr and cupswrapper drivers I downloaded from the Brother solutions page were downloaded and installed in the order suggested. The thread added a few things in the installation instructions that the Brother printer solutions page did not include. Those were the addition of two file paths, /var/spool/lpd and /usr/share/cups/model and a cp command for a printer brlpdwrapper filter that my setup does not require, because the printer filter file is already in the right place. Otherwise, I did everything suggested in the thread, but the Brother MFC-8860DN printer would not print when I tried to print a test page. I checked the [http://localhost:631](http://localhost:631) web page as suggested by the thread and everything looked fine, but the printer still did not print.

I also checked the Brothers solutions web page and followed their instructions. The downloading and installation of the drivers was the same, but there were a few steps in the Brother solutions page instructions that the thread did not include in its installation instructions. 

The Brother solutions page states that a user should check the printer configuration in the /etc/printcap file for the following entry: :lp=/dev/usb/lp0:\.  The printcap file, however, is not at the /etc/printcap location. My printcap file is to be found at the /etc/profile.d path on my Ubuntu 10.04 64 bit system and it does not contain the information as shown on the Brother printer solutions page. My printcap file contains the following information:

# This file was automatically generated by cupsd(8) from the
# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
MFC8860DN|MFC8860DN:rm=bill-desktop:rp=MFC8860DN:

The /etc/cups/printers.conf file mentioned above contains the following:

# Printer configuration file for CUPS v1.4.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<Printer MFC8860DN>
Info MFC8860DN
MakeModel Brother MFC8860DN for CUPS
DeviceURI usb:/dev/usb/lp0
State Idle
StateTime 1280260821
Type 8392724
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 0 brlpdwrapperMFC8860DN
Accepting Yes
Shared Yes
JobSheets classified classified
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option fitplot false
</Printer>

The Brother solutions page shows the following for a printcap configuration file in the  /etc/printcap file for a printer USB connection:

printcap or printcap.local file (for USB connection)
$ cat /etc/printcap
DCP540CN:\
      :mx=0:\
      :sd=/var/spool/lpd/dcp540cn:\
      :sh:\
      :lp=/dev/usb/lp0:\
      :if=/usr/local/Brother/Printer/dcp540cn/lpd/filterdcp540cn:

The Brother solutions page also points to an /etc/init.d/lpr file to restart the print system.  A command line search however states there is no such file or directory.

My suspicion is that if I could somehow join the install instructions of both the thread and the Brother solutions page I could get the printer working. It is clear to me that the problem is an incomplete or incorrect printer configuration that has something to do with the missing /etc/printcap file and the missing /etc/init.d/lpr file. I just don't know how to do it. Do I create these files? If yes, how do you create these files and where should I put them? Am I on the right track? Or is there another solution? Any help would be appreciated.

Bill

---

### Post by johnx760 on 2010-08-07
Hi Bill,

I just installed a similar Brother MFC printer.  When you enter the CUPS web interface at [http://localhost:631](http://localhost:631), go to Admin->Manage Printers.  Do you see your printer here?  If so, try deleting it (Maintenance->Delete Printer), then adding it again through 'Add Printer', where you should be able to see your network printer again.

Sometimes you won't see a driver in the list of available options if it's already in use by an installed printer.  So, maybe your originally installed printer (which was configured wrongly somehow) is hogging that driver?

John

---

