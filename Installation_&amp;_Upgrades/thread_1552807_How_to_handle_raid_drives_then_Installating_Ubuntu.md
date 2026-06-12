---
title: "How to handle raid drives then Installating Ubuntu to a HP Proliant server"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by martinradbo on 2010-08-14
[FONT=Verdana]I am trying to install the latest release (10.04) of Ubuntu server. Hardware is a brand new HP Proliant DL380 G6 with four SAS hard drives at 146 GB each. I want to run RAID5 or similar with one spare disk. [/FONT]
 
[FONT=Verdana]Since linuxinstallations are not my best area of knowledge I got stuck. [/FONT]
 
[FONT=Verdana]First attempt I just run the installation, choosed the 440 GB harddrive in the partitioning part of setup for installation and went on. All went fine until setup was done and server rebooted, it then stopped without any message in the beginning then trying to find bootable devices (I.e., it did not find the Ubuntu installation at all I think). [/FONT]
 
[FONT=Verdana]So after some reading I decided to go for software raid. I went into disk manager at BIOS (F8) and deleted the array so that I should be presented with four 146 GB disks during setup. At least I thought. In the config application in BIOS the array was deleted and it says: "No arrays definied". [/FONT]
 
[FONT=Verdana]This time, at the partitioner during installation, still only one disk shows up. See "screen dump" below.[/FONT]
 
[FONT=Verdana]Since it still tells me the disk is 440 GB (raid5 with 3 units x 146 GB) there are three cause for this:[/FONT]
[FONT=Verdana]1 I failed to delete the array in the BIOS setup of raid array[/FONT]
[FONT=Verdana]2. Ubunbu installation has automatically created it for me (hardware raid)[/FONT]
[FONT=Verdana]3. Ubunbu installation "guess" I want i RAID5 with 3 units and have already done it for me with software raid.[/FONT]
 
===========
 
Screen dump of partitioner view:
 
[FONT=Courier New]Guided partitioning[/FONT]
[FONT=Courier New]Configure software RAID[/FONT]
[FONT=Courier New]Configure the logical volyme manager[/FONT]
[FONT=Courier New]Configure excrypted volymes[/FONT]
[FONT=Courier New]Configure iSCSI volumes[/FONT]
 
[FONT=Courier New]SCSI.CCISS (-,0,0= (cciss/c0d0) - 440.3 GB Compaq Smart array[/FONT]
[FONT=Courier New]pri/log 440,3 GB FREE SPACE[/FONT]
[FONT=Courier New]SCSI3 (0,0,0 (sda) - 4.0 GB Kinston DataTRaveler 2.0[/FONT]
[FONT=Courier New]#1 primary 4.0 GB B Fat32[/FONT]

---

### Post by ronparent on 2010-08-15
With a fakeraid setup initially, removing the raid in bios doesn't delete the raid metadata already on the disks. To do that you have to use dmraid to explicitly erase the metadata (sudo dmraid -E /sd(x) etc.- including all the pertinent drives in the command line). If you aren't using it you should probable uninstall dmraid. 

Though just uninstalling dmraid itself would eliminate the problem, it would be cleaner in the long run to eliminate the metadata - otherwise the matadata could reappear to haunt you in a future system install or if you recycled the disks.

---

### Post by anrix on 2011-03-10
I am having the same issue with [507127-B21]("http://servercaddy.co.uk/HP-507127-B21-300GB-2-5-Hot-Swappable-SAS-SFF-10-000rpm-Dual-Port-Hard-Drive.html"), did you manage to find a solution to this?

---

