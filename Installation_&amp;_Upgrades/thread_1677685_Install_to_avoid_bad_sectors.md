---
title: "Install to avoid bad sectors?"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by goodwin57 on 2011-01-29
Had issues getting into current install over xmas, so just decided to download a new live usb and install over the top. 

 However, I have some **bad sectors**.  I downloaded PartedMagic and using one of the utilities I think the bad sectors are   323649-323655.  



When I try to** install, I get a message "input/output error on /dev/sda1"** (my main partition), I've looked to see whether it's possible to change partitions to avoid sectors, but I don't really understand either whether it is, or if it is, how.  I've tried using gpartedto change partition sizes but it fails whenever I attempt it.  I know this may be the death knell of my harddrive, but it's an acer aspire one, and I don't keep anything important on it (but I do want to be able to use it!)  so...


Is it possible to do something to avoid those sectors and install over?
Thanks
SK

---

### Post by ronnielsen1 on 2011-01-29
Copy of a post I made to someone else but you need a new hard drive (especially if you're getting IO errors)
Hirens boot cd has a lot of hard drive tools. You can try to use it.

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

[http://www.hirensbootcd.org/files/Hi...ootCD.13.0.zip]("http://www.hirensbootcd.org/files/Hirens.BootCD.13.0.zip")

> **Active Kill Disk 4.1.2393** Securely overwrites and destroys all data on physical drive.
**Darik's Boot and Nuke (DBAN) 1.0.7** Completely deletes the contents of any hard disk it can detect.
**DiskView 2.4**  to view graphical map of your disk, allowing you to  check where a file  is located or, by clicking on a cluster, seeing  which file occupies it.
**DiskWipe 1.2** Securely erases the contents of a disk replacing it with random data or leaving the drive completely blank.
**ExcelStor's ESTest 4.50** ExcelStor hard disk diagnostic utility.
**Fujitsu HDD Diagnostic Tool 7.00** to check IDE drives for possible defects/problems.
**Fujitsu IDE Low Level Format 1.0** Low Level Format Tool for Fujitsu Drives.
**Gateway GwScan 5.12** Gateway hard drive diagnostic utility.
**Hard Disk Sentinel 1.00.5** Hard Disk health, performance and temperature monitoring tool.
**HDAT2 4.53**the  main function is testing and repair (regenerates)  bad sectors for  detected devices. A freeware alternative of HDD  Regenerator.
**HDD Capacity Restore 1.2**  This tool allows you to restore factory  capacity of any hard drive. it  does not read from or write to the user  data area or perform any kind of  formatting, only alters HDD firmware  (HPA and DCO settings).
**HDD Erase 4.0** Secure erase using a special feature built into most newer hard drives.
**HDD Low Level Format Tool 2.36** Low-level format tool for S-ATA (SATA), IDE (E-IDE), SCSI, USB, Flash Cards and FIREWIRE external drive enclosures.
**IBM Hitachi Drive Fitness Test 4.16** quickly and reliably tests SCSI, IDE and SATA drives.
**IBM Hitachi Feature Tool 2.15** allows you to control some of the features of the the HDD.
**Maxtor amset utility 4.0** Utility for changing Acoustic Management on the hard drives.
**Maxtor Low Level Formatter 1.1** Maxtor's Low Level Format Utility works on any harddrive.
**Maxtor PowerMax 4.23** designed to perform diagnostic read/write verifications on Maxtor/Quantum hard drives.
**MHDD 4.6**  Precise diagnostic of the mechanical part of a drive,  perform Low-level  format, Bad Sector Sepair, access raw sectors, manage  S.M.A.R.T.  (SMART) and other drive parameters such as acoustic  management,  security, Host Protected Area, etc.
**Samsung Disk Diagnose (SHDIAG) 1.28** to diagnose the disk when suspected to have failures.
**Samsung ESTOOL 3.01v** Drive Diagnostic, Automatic Acoustic Management, Enable/Disable SMART etc.
**Samsung HDD Utility(HUTIL) 2.10** The Drive Diagnostic Utility.
**SeaTools for Dos** GUI 2.22 Text 1.10 versions to test Seagate or Maxtor Parallel ATA (PATA and IDE) and Serial ATA (SATA) interface disc drives.
**SmartUDM 2.00** Hard Disk Drive S.M.A.R.T. Viewer.
**Toshiba Hard Disk Diagnostic 2.00b** Toshiba hard drive diagnostic utility.
**Victoria 3.33e and 3.52rus** a freeware program for low-level HDD diagnostics.
**Victoria 4.46** Universal program for testing storage devices
**ViVard 1.0** HDD low-level diagnostics, Surface test with remap, SMART-attributes etc.
**WDClear 1.30** Restore/Erases the drive back to a factory condition.
**Western Digital Data Lifeguard Tools 11.2** for the installation of Western Digital EIDE Hard Drives.
**Western Digital Diagnostics (DLGDIAG) 5.19** to quickly and efficiently verify the status of the drive.
**Western Digital Data Lifeguard Tools 1.22**  to perform drive identification, diagnostics, and repairs on most WD drives 			 		

---

### Post by goodwin57 on 2011-01-29
Thanks ronielsen1 I think I'll resign myself to running a live usb, I ran a couple of those tools but on the 'idiot' level (auto run throughs, etc.) nothing useful is happening/I can't get info to do anything useful.  I guess some people might be able to use this [http://gparted-forum.surf4.info/viewtopic.php?id=13825](http://gparted-forum.surf4.info/viewtopic.php?id=13825) which describes just partitioning to find bad areas and setting those to 'do not use'...for some reason, I'm not having any luck with that though.  If anyone has any bright ideas I'd appreciate them

EDIT: I meant to mention, this is an acer aspire one, so SSD, not sure if that impacts on the tools I can use and their effectiveness, etc.

thanks
sk

---

### Post by nogoodnamesleft on 2011-01-29
bad sectors tend to spread over time, you should get a new drive - less stressful to install when prepared vs recover when it dies

also they can produce random errors in programs or data, which can be frustrating

most hard drives have a 3 year plus warranty of some kind, you might be able to send it back to the manufacturer for a replacement (just scrub the private data first)

i would recommend the manufacturer's drive diagnostic tool as not all bad sectors are actually "bad" and can be formatted out - you do seem to have a big bunch of them though which leads me to suspect they are genuine

edit - sorry did not see where you said SSD - ignore above about warranty !!! SSD have a limited life (5,000 to 1million writes or something depending on the type of SSD) so yea they go bad.

---

### Post by goodwin57 on 2011-01-29
Thanks for the advice, I'm a bit surprised given I thought SSD was supposed to be v. reliable, but never mind.  If I decide I use it enough for it to be cost effective, I'm thinking about replacing with CF card (faster according to web posts).
nogoodnamesleft - I've done a couple of formats, and writing 0s to the whole drive, but then when coming to partitioning it's still not letting me partition and/or format to ext4 to install ubuntu...

---

### Post by nogoodnamesleft on 2011-01-29
Lifespan is not the same as reliability.

Reliability means "chance it will break unexpectedly"

Lifespan is how long it will last.

[http://en.wikipedia.org/wiki/Solid-state_drive#Comparison_of_SSD_with_hard_disk_drives](http://en.wikipedia.org/wiki/Solid-state_drive#Comparison_of_SSD_with_hard_disk_drives)

What i said about formatting out bad sectors doesn't really apply to SSD. I wrote that when I thought it was an HDD.

---

### Post by goodwin57 on 2011-01-30
ah of course, I guess I've had it 2.5 years now.  If there are any ways to avoid the bad sectors, it'd be good to know but I'm going to assume not and take the 'replace' option!  
Thanks for the help, I'll mark this as solved.

---

