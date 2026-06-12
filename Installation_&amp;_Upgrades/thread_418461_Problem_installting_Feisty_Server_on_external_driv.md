---
title: "Problem installting Feisty Server on external drive"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by krolben on 2007-04-22
Hi all, I really hope you can help me out. I've been struggling with installing Feisty for 4 days now.

The problem is that during file copy when installing Feisty Server I get errors while installing Debootstrap. 

My system is a bit special:
Via Epia ME6000 LVDS motherboard (mini-ITX)
1GB memory (actually, it may be just 512MB, I'm not sure)
1GB internal flash card attached to IDE port as HDD
320GB external harddisk attached using USB2

These are the errors I can see when going to the log using alt-F4:
kernel: usb 4-1: new high sped USB device using ehci_hcd and address 6
kernel: usb 4-1: device not accepting address 6, error -71
kernel: usb 4-1: new high speed USB device using ehci_hcd and address 7
debootstrap: dpkg: unable to access dpkg status area: Read-only file system
kernel: usb 4-2: device not accepting address 7, error -71
debootstrap: dpkg: unable to access dpkg status area: Read-only file system
debootstrap: dpkg: unable to access dpkg status area: Read-only file system
kernel: scsi 0:0:0:0 rejecting I/O to dead device
kernel: EXT3-fs error (device sda1): ext3_find_entry: reading directory #2850817 offset 0
debootstrap: /usr/sbin/debootstrap:
debootstrap: cd: 1:
debootstrap: can't cd to /target/var/lib/apt/lists
debootstrap: 

The partitioning scheme I'm using:
IDE2 master (hdc) 1.0 GB CF300
	- #1 primary	 49.3 MB 	B f ext3	/boot
	- #2 primary	978.8 MB	  f ext3	/

SCSI1 (0,0,0) (sda) - 320.1 GB
	- #4 primary	261 GB		  f ext3	/home
	- #6 logical	  2 GB		  f swap	swap
	- #5 logical	  1 GB		  f ext3	/tmp
	- #2 primary	  6 GB		  f ext3	/usr
	- #1 primary	 50 GB		  f ext3	/var


Note: When starting the install I add "debian-installer/framebuffer=false" as a parameter. Othwerwise the install screen appears totally screwed. I don't know if this can have any effect?
I've previously had Edgy Desktop installed on the same machine. This was with another external HDD and another case for the external HDD.

What can be done to get around this problem?

---

### Post by krolben on 2007-04-22
Addon question: I've seen that others have had issues with USB 2. How can I turn off USB 2 during install and only use USB 1?

---

### Post by krolben on 2007-04-22
Update:
The problem seems to have been solved by shifting to my old external harddisk case. I get a new error now, though. 
New thread for that error: [http://ubuntuforums.org/showthread.php?t=418795](http://ubuntuforums.org/showthread.php?t=418795)

---

