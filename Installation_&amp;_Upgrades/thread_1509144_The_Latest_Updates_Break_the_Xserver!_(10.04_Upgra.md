---
title: "The Latest Updates Break the Xserver! (10.04 Upgrade)"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by berean1224 on 2010-06-13
Dear Colleagues,

Ubuntu has been great and it is a great Linux distro.  Unfortunately, the update of 9.10 desktop edition to release 10.4 failed on a couple of fronts.  
   
  1) Xserver is no longer working;
  2) An upgrade of grub-pc causes an exception.  
   
The system ran perfectly before the update was performed. 

  The update resulted in 
   
  Attempting to install GRUB to a partition instead of MBR. This is a BAD idea.. 
   
  /usr/sbin/grub-setup: warn:  Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and is use is discouraged.  
   
  Based on information found at [http://ubuntuforums.org/showthread.php?t=241254](http://ubuntuforums.org/showthread.php?t=241254) 
  an attempt was made to execute the following command.
   
  ‘sudo aptitude dist-upgrade’ 
   
  But that resulted in 
   
  E: dpkg was interrupted, you must manually run ‘sudo dpkg –configure –a’ to correct the problem
   
  The later launches an upgrade of grub-pc.  This routine requests the selection of which devices are to be used to store grub-install.
   
When that was done ...

  GRUB failed to install to the followed devices:
   
  /dev/sdb1 /dev/sdc1 /dev/sdd4
   
  Do you want to continue anyway?  If you do, your computer may not start up properly.
   
  GRUB installation failed.  Continue?
   
  Questions:
   
  1)      Can / should the upgrade of grub-pc be bypassed in order to get the system running?   
  2)      If not, what values should be selected when selecting the devices to store grub-install?  
  3)      Because the computer is a RAID configuration, would someone advise are there special considerations which should be considered? 
  4)      Once grub-pc is resolved or bypassed, should the commands found in the aforementioned article be used to repair xserver.
  5)      Are there additional measures which will be needed to in order to complete the update to release 10.4?
   
Your help and suggestions are sincerely appreciated.

Thank you,

Steve

-----------------------------------------------------------

  Here are some helpful details on the system configuration
   
  The computer has four disk drives using RAID 1 and RAID 5.  In the following configuration
   
  RAID5 Device #0 750.2 GB Sotfware RAID device
  #1                                            750.2 GB                                ext4
  SCSI1 (0,0,0) (sda) 320.1 GB ATA WDC WD3200AAKS-2
  #4        primary 250.1 GB       K raid
  #3        primary 16.0 GB         F swap
  #2        primary 16.0 GB         F swap
  #1        primary 38.0 GB         B ext4
  SCSI2 (0,0,0) (sdb) – 250.1 GB ATA WDC WD2500AAKS-0
  #1        primary 250.1 GB       K raid
  SCSI3 (0,0,0) (sdc) - 250.1 GB ATA WDC WD2500AAKS-0
  #1        primary 250.1 GB       K raid
  SCSI4 (0,0,0) (sdd) 320.1 GB ATA WDC WD3200AAKS-7
  #4        primary 250.1 GB       K raid
  #3        primary 16.0 GB         F swap
  #2        primary 16.0 GB         F swap
  #1        primary 38.0 GB         K raid
   
  The /boot/grub/device.map contains
   
  (hd0)   /dev/sda
  (hd1)   /dev/sdb
  (hd2)   /dev/sdc
  (hd3)   /dev/sdd
   
  There are proprietary drivers for ATI installed.

---

### Post by berean1224 on 2010-06-20
Colleagues,
   
  For those who are willing to brave an upgrade without ‘official’ guided support from others regarding the reported anomaly, let me post further information which maybe helpful to the community.  
   
  After the initial problem was reported and without further guidance, the command ‘sudo dpkg –configure –a’ was executed without performing the update to the grub-pc.
   
  So, as you can expect, when prompted with where to install grub, no devices were selected.  Thus, the upgrade procedure was able to proceed to release 10.4.
   
  Scores of software packages were downloaded.  Thereupon, the system was rebooted and xserver services were successfully restored. 
   
  I am hopeful others will not have to experience the pain due to the problematic changes with the grub-pc component.
   
  Many should be cautioned an upgrade to Ubuntu can result in the loss of xserver functionality and thereby it can cripple the usability their system.   
   
  While may of us highly regard Ubuntu as a Linux distribution, further enhancements, resources, controls and support maybe necessary from their part in order to stabilize their releases. 
   
  For those who encounter a similar issue, may this post serve to be helpful to the community at large as well as input to Ubuntu. 
   
  These comments are intended to be constructive. 
   
  Respectfully,
   
  Steve

---

