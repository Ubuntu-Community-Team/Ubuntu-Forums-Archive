---
title: "Hardware RAID installation - Ubuntu 10.10"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by netwidget on 2011-04-23
I am setting up a file server for a small business with RAID 10 for the data drive.   The  OS and server applications will be installed on a separate smaller HDD not apart of the RAID.  I want this to be a hardware RAID, so I purchased a SIIG 4-channel SATA RAID  (PCI) controller card and installed it in the server.   The card's RAID configuration utility came up separately after the BIOS announcement  screen upon pressing ctl-s-f4 it recognizes the four 1 TB hard drives in my hotswap bays, and I used the auto configuration option to choose RAID 10.  I used all of the drive space as one partition with the channeling set to 64k.

With the 10.10 server installation CD in the DVD drive I continued to boot the installation CD and started the installation process.  I have gotten to the stage where 10.10 server has detected the disks  and has stopped at the following screen:

> [!] Detect Disks

One or more drives containing Serial ATA RAID configurations have been found. do you wish to activate these RAID devices?

Activate Serial ATA RAID devices? 

<yes> <no>

Which should I choose?  The RAID Array is only for file data the OS will not be installed on  the array.   Shouldn't the RAID drive just be seen as another drive?  Why would it need to "activate" the device if it is controlled by a hardware RAID card. 

At this point the installation program has not even asked me to select the drive on which to install the OS.  Nor have I seen a formal list of drives yet. 

Please help.

---

### Post by dino99 on 2011-04-23
look at this howto:

[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

[http://simplysimple.info/installing-ubuntu-server-hardware-raid/](http://simplysimple.info/installing-ubuntu-server-hardware-raid/)

---

### Post by punkybouy on 2011-04-23
If your hardware raid bios firmware did its job it should be presenting to the Ubuntu installer the chosen configuration that you made.  I would answer "yes" and see if what Ubuntu sees is the configuration that you made.  Ubuntu would still need a SIIG Linux driver to work properly and if that is not available its possible Ubuntu is using a generic SATA driver and thus sees 4 separate drives and not your RAID 10 configuration.
Rerun the installation and then select "no" and see if that changes anything.  If after trying installations and answering both "yes" and "no" you do not see your RAID configuration then I would say Ubuntu lacks the proper driver.  You could see if SIIG has a driver on their website with instructions for using it.
Since your OS is not on those drives you could use some Linux utility for creating a software RAID configuration.
I know for a fact that Ubuntu recognizes Compaq/HP SmartArray cards and uses a driver called "cciss" for SCSI cards anyway.

---

### Post by punkybouy on 2011-04-23
Looking at the SIIG website it appears the only SATA four port card they have that does RAID is the SC-SA4R12-S2.  Under "requirements" I see this:
Windows 7 (32-/64-bit) / Vista (32-/64-bit) / XP (32-/64-bit) / Server 2003 & 2008 (32-/64-bit) / 2000.  I don't see any references to Linux so there may be no driver available.
HP does make a controller called the E200 that might fit your needs and does have Linux driver support for Red Hat and Suse or Ubuntu might inherently have the same driver too.

[http://h18004.www1.hp.com/products/servers/proliantstorage/arraycontrollers/smartarraye200/index.html](http://h18004.www1.hp.com/products/servers/proliantstorage/arraycontrollers/smartarraye200/index.html)

[http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?lang=en&cc=us&prodNameId=3182562&taskId=135&prodTypeId=329290&prodSeriesId=1157688&lang=en&cc=us](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?lang=en&cc=us&prodNameId=3182562&taskId=135&prodTypeId=329290&prodSeriesId=1157688&lang=en&cc=us)

---

