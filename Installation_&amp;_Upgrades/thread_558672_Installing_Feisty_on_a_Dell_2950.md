---
title: "Installing Feisty on a Dell 2950"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by Almost A Ghost on 2007-09-24
I'm getting ready to install Feisty on a Dell 2950. I've read the other threads and hopefully going with Feisty will help side step the driver problems other people have had with earlier Ubuntu versions. Even with Feisty is there anything I should be aware of?

Michael

---

### Post by Pumalite on 2007-09-24
Have you tried the Live CD? Post your specs, so to advise you as to what iso. Dual booting? It all makes a difference.

---

### Post by Pumalite on 2007-09-24
This might end up being your only problem:

Embedded ATI ES1000 with 16MB memory

Better use the Alternate CD

---

### Post by Almost A Ghost on 2007-09-24
Here is the system print out from dell.com

1	0R215	CORD, POWER, 15A, 125V, 10, 5-15/C13
1	4D175	CORD, POWER, 125V, 10FT, 2TO1, SJT
1	Y8132	POWER SUPPLY, 750W, REDUNDANT, DELTA PRODUCTS
1	PN610	PRINTED WIRING ASSY, BACKPLANE, SERVER, SERVER CHASSIS, DELL2950, 3.5X6SAS
1	KC411	ASSEMBLY, CABLE, SASX4-PERC5X4-X4BKPLN
1	MC360	ASSEMBLY, CABLE, SASX4-PERC5X4-X6BKPLN
1	WX072	ASSEMBLY, CARD (CIRCUIT), PERC5I, SERIAL ATTACHED SCSI, 1950, 2950
1	H6183	PRINTED WIRING ASSY, RISER, SERVER, SERVER CHASSIS, DELL COMPUTER CORPORATION, PE2950, PERIPHERAL COMPONENT INTERCONNECT EXPRESS, LEFT
1	FC554	PRINTED WIRING ASSY, INPUT/OUTPUT, CD-INTRPSR, PE2950
1	NC074	ASSEMBLY, CABLE, CDROM-SIDEPLANE
4	NP948	DUAL IN-LINE MEMORY MODULE, 1G, 667M, 128X72, 8, 240, 2RX8
1	TX235	KIT, DOCUMENTATION ON COMPACT DISK, DOCUMENT OBJECT MODEL, V5.2, WORLD WIDE
1	0R215	CORD, POWER, 15A, 125V, 10, 5-15/C13
1	GG460	KIT, STRAIN RELIEF, CABLE, POWER
1	RP016	ASSEMBLY, COMPACT DISK DRIVE, 24X, 12.7MM, HITACHI LG DATA STORAGE, BLACK
3	WR711	HARD DRIVE, 146G, SERIAL ATTACHED SCSI, 3, 10K, 3.5, SGT2, T10
2	UM837	HARD DRIVE, 73G, SERIAL ATTACHED SCSI, 3, 15K, 3.5, SG2, 15K5
1	DT021	ASSEMBLY, PRINTED WIRING ASSY, PLANAR (MOTHERBOARD), FOX ELECTRONICS, PE2950
1	FG027	CARD (CIRCUIT), BACKPLANE, KEY, TOE, 2PORT, ENTERPRISE SYSTEMS GROUP
1	PR700	PROCESSOR, 80556K, XCL, E5310, LGA771, BURN 3
1	PR700	PROCESSOR, 80556K, XCL, E5310, LGA771, BURN 3
1	YY443	OVERPACK KIT, 3R23SE, SP2, ENGLAND/ENGLISH

My plan is to install Feister Server, so would that negate video card issue?

This system will not be dual booted, it is being setup as a VMWare server.

Thanks for your help

---

### Post by Pumalite on 2007-09-24
Even a server needs a working xserver I think; being CLI and all.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check Server Edition and then mark the box below the green sign 'Start Download'

---

### Post by Almost A Ghost on 2007-09-24
> **Pumalite said:**
> Even a server needs a working xserver I think; being CLI and all.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check Server Edition and then mark the box below the green sign 'Start Download'

I don't believe so, Ubuntu Server comes pretty stripped, just a console.

---

### Post by Pumalite on 2007-09-24
I checked and you are right. Good luck.

---

### Post by Almost A Ghost on 2007-09-28
Today I should be installing 7.04 server on the 2950. I have tested compatibility with a 7.04 Desktop/Live CD, it sees both NIC's and Raid controller with volumes and partitions without issue.

Edit: X-Windows worked fine using whatever driver it uses for the live CD, even though I won't be running XWin.

---

### Post by Almost A Ghost on 2007-10-02
Yesterday morning I installed Ubuntu 7.04 Server on the 2950, very straight forward and clean install. There were no extra steps required, all hardware worked "out of the box". Currently it is running VMWare serve with a Windows 2003 VM chugging along just fine.

---

### Post by zayindaleth on 2008-01-15
Tomorrow I should be installing 7.10 on a poweredge 2950.
I have had issues in the past with detecting ethernet cards and raid controllers, but I'm hoping with a newer version of ubuntu these issues would have become a thing of the past.

A similar setup to yours will be what I have in mind (ie, vmware and win2003).
Hopefully it won't take more than a couple of hours to get this going.

---

### Post by zayindaleth on 2008-01-15
> **Almost A Ghost said:**
> Yesterday morning I installed Ubuntu 7.04 Server on the 2950, very straight forward and clean install. There were no extra steps required, all hardware worked "out of the box". Currently it is running VMWare serve with a Windows 2003 VM chugging along just fine.

Just a quick question, did you use the server or the alternate server iso?

---

### Post by Partyboi2 on 2008-01-15
From what I understand the alternate cd allows you to setup raid during the installation. Not sure about the server cd

---

