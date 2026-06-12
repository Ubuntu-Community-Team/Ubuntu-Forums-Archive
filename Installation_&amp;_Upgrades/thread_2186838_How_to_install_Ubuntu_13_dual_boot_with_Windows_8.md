---
title: "How to install Ubuntu 13 dual boot with Windows 8"
date: 2013-11-09
forum: Installation &amp; Upgrades
---

### Post by olly-xquest on 2013-11-09
I have just completed a couple of successful installations of Ubuntu Studio on Toshiba Satellite laptops with Windows 8 pre-installed.
During the last installation, I took the following notes and thought that they might be some help to anyone attempting a dual boot with Windows 8 for the first time.
It is important to make sure your network and video drivers are supported before you start.
If this seems a lot of hassle, don't be put off - IT IS WORTH IT - Studio is excellent!  

Windows 8/Ubuntu Studio dual boot installation notes


Login to windows 8
Find and select Recovery Media Creator
Create recovery DVDs
In addition, ***BACKUP YOUR DATA*** separately.  
Find File Manager 
	Select C: drive
	Select Manage
	Run Clean Up then Optimise to free disk space and defrag drive


Create space on Hard Disk
Open Windows Explorer
Select Computer | Manage | Storage | Disk Management
Select C: drive
Right click and select Shrink Volume
'Amount of space to shrink' is the amount available for the Ubuntu installation.
Overtype this to change if you want.
Shrink


Determine network card spec:
Control Panel | System and Security | System | Device Manager
if
	PCI-E Qualcomm Atheros AR8161
	Wireless Qualcomm Atheros AR956X
	Ubuntu Studio Version 12 not Supported - Download  13.10 dvd-amd64 (13.04 has Jack Latency issues)
else
	Download Ubuntu Studio 12.04 dvd-amd64

Burn DVD
Put DVD in tray and restart
If DVD will not boot
disable Win 8 Secure Boot
	Restart Win 8 holding down shift
	Select Troubleshoot | Advanced Options | UEFI Firmware settings 
	Restart (looks like BIOS screen)
	Select Security
	Select Secure Boot 
	F5 to change
	Exit saving changes
	
refer to:
[http://news.softpedia.com/news/Installing-Ubuntu-13-04-348582.shtml](http://news.softpedia.com/news/Installing-Ubuntu-13-04-348582.shtml)
for a good visual procedure for a normal (single boot) installation


Boot up DVD
Choose Try Ubuntu 
Blank screen? probably video driver issue
No Network connection? probably network driver issue - see above


Install from disk 



Check box for:
	Download updates while installing
	Install third party software
Installation type
	Note! ***does not detect Win 8***, only previous linux installations, so select 'something else'
	previous linux partitions if any - click '-' to delete
	create new primary partitions
		swap area - 2048 MB
		ext4 mount point /home - free space less 20000 MB
		ext4 mount point / - 20000 MB (new installation uses about 7GB)
Install now
	the installation should now proceed as normal
	
When insallation is complete, restart the computer
After the manufacturer's welcome screen there should be a blue screen with several options
Ubuntu Studio is the first option and is the default if you take no action
To boot up Windows 8 select Windows Boot UEFI Loader with the down arrow
If this does not work you will need to run boot repair:


To install and run boot repair
check secure boot disabled - see above 
insert ubuntu disk and select try unbuntu
open  2 instances of terminal
at command prompt of first terminal type:
sudo add-apt-repository ppa:yannubuntu/boot-repair 
sudo apt-get update 
sudo apt-get install -y boot-repair 
boot-repair


Select Recommended Repair
rename EFI files - yes


if given lines to type in copy and paste into command line of other terminal


do not re-enable secure boot - it will need to be passworded

Best of Luck!:)

---

