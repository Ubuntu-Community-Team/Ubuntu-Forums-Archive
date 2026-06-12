---
title: "Ubuntu tools to back up Windows XP and ntfs"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by russelld on 2006-08-15
Hi All

What Ubuntu tools are there to back up WinXP/ntfs partition?

I used ntfsclone and partimage last night to back uo a WinXP box to get it ready for repartitioning and dual boot with Ubuntu.

I could have used Norton Ghost or Powerquest DriveImage, but wanted to only use Ubuntu tools. 
(secretly practicing for Software Freedom Day :) ) 
This turned out much harder than I thought.

I couldn't get partimage to network to another computer and eventually got images onto a usb hard-drive,

What is your experience these or other tools to backup ntfs partitions using Ubuntu?

and very importantly, what is the success of doing a working restore?

TIA

Russell

---

### Post by geekphreak on 2006-08-15
> **russelld said:**
> Hi All

What Ubuntu tools are there to back up WinXP/ntfs partition?

I used ntfsclone and partimage last night to back uo a WinXP box to get it ready for repartitioning and dual boot with Ubuntu.

I could have used Norton Ghost or Powerquest DriveImage, but wanted to only use Ubuntu tools. 
(secretly practicing for Software Freedom Day :) ) 
This turned out much harder than I thought.

I couldn't get partimage to network to another computer and eventually got images onto a usb hard-drive,

What is your experience these or other tools to backup ntfs partitions using Ubuntu?

and very importantly, what is the success of doing a working restore?

TIA

Russell

Partimage worked on and off network for me. I was using the sysresccd CD (sysresccd.org) I was surprised how smoth it went and was glad to see some alternative to Ghost.

---

### Post by russelld on 2006-08-16
> **geekphreak said:**
> Partimage worked on and off network for me. I was using the sysresccd CD (sysresccd.org) I was surprised how smoth it went and was glad to see some alternative to Ghost.

can you post the details of what you did, please?

I followed the instructions from [http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)
but still got 
"Connexion refused by server: "incompatible networking options. Try disabling login option for server with -L" 

these are the steps I did:

0) open port 4025  on server to local network 10.0.0.0/16
1) add user in server: partimag
	sudo adduser partimag
2) do not make partimaged SUDI, run as root
3) get IP address of server: ifconfig, look under ethO (10.0.0.5)
4) then add users name, user has to be a user on system and present in /etc/passwd
	sudo echo username > /usr/etc/partimaged/partimagedusers
	When logging in the password must be the same as the user in the system
5) run partimage server:
	change directory where images are to be saved
	cd /imagedir	
	sudo partimaged -L
	(to get help: partimaged --help)
6) start partimage client
	insert sysresccd into client computer cd-dvd drive
	reboot client computer
7) at prompt enter:
	partimag
	(follow prompt in partimage gui)
	filename:image.partimag.gz
	[X] Connect to server
	server address: 10.0.0.5
	port [4025]
	next [F5]
	 ......fell over....."incompatible networking options..."

---

### Post by russelld on 2006-08-18
The network imagining with partimage  eventually worked.  This was done by having Ubuntu Dapper running on both server and client (boot disk) and and installing partimage via apt-get on both machines.  My mistake was to use different linux distros on server and client. ie Ubuntu Dapper on server and System-rescueCD on client. Even though the binaries were the same version, the slight difference between the distros made the binaries incompatible and it would not connect.  It did take along time ~3hrs and limited to the Ethernet speed whereas the Ubuntu imaged to usb hard drive took about 15 minutes.  

Also, partimage is not installed on Ubuntu Dapper CD and doesn't seem to be in active development.  Compare with ntfsclone which is  installed on the CD and actively developed.  Just having it installed on the CD makes it easier to use.

---

### Post by koshari on 2008-06-04
> Just having it installed on the CD makes it easier to use.

i agree , it would be great if partimage was a part of the live disc, 

then i wouldnt need to lug round a gparted/partimage live disc,

---

