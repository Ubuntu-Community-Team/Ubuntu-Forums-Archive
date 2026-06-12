---
title: "Karmic Koala ASUS M2A-VM"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zaiboot on 2009-09-15
[FONT="Verdana"]Hello to everyone.
I just download Karmic Koala Alpha 5 desktop i386 and when I try the live CD session shows me this sequences of errors:

I have 2 HDD and it fails to mount it, then shows me:
stdin: error 0 a lot of times until I get:
Busy box v1.13.3
Unable to find medium containing a live file system.

In a quick specs I have this:

Asus M2A-VM 64 X2 5600+
Amd Athlon
4 GB RAM
Integrate Video ATI Radeon X1200
Realtek HD Audio
Samsung SyncMaster T240HD

More detailed description in the attachements.

Is this a bug or is just that my computer configuration is not suitable for Ubuntu, because since **9.04 i386 & x64 **ubuntu live CD won't work in my computer.

Thank you to everyone.
[/FONT]

---

### Post by 00b00nt00 on 2009-09-15
Have you tried an older version of Ubuntu, such as 9.04? Karmic will not be ready until the end of October, so you should understand that it's not in a usable condition for everyday use.

By the way, the message may indicate some difficulty reading the live CD. Make sure you burn your CDs at 8X speed or less.

---

### Post by zaiboot on 2009-09-15
I know that Karmic Koala is in alpha stage and is not ready. I just wanted to know if this issue was fixed in Karmic Koala. Because I have tested 9.04 and 8.10 but unsuccesfully.

I will try to burn it in 8x speed. Thanks in advance.

Tested with 8x speed burn disc and same error.

---

### Post by rajeev1204 on 2009-10-13
Hi
The ASUS M2A VM board wont boot from live cd either intrepid,jaunty or karmic.Its a bios issue with the amd 690 g chipsets.Hardy works ok for me with this board.

I have filed a bug but no idea if it will ever be fixed.

There are some parameters which can be used when live cd menu shows, press f6 then add acpi=off pci=nomsi irqpoll and see if it goes forward.

You might have noticed that the HDD light stays on which means that its trying to read HDD as a cdrom but since contents are on cdrom ,it wont go forward.

---

### Post by monogo on 2009-10-13
Hm, strange. Got the same mainboard and had no problems since 7.10 Gutsy Gibbon. Actually under Jaunty, will test Karmic these days.....

---

### Post by rajeev1204 on 2009-10-14
> **monogo said:**
> Hm, strange. Got the same mainboard and had no problems since 7.10 Gutsy Gibbon. Actually under Jaunty, will test Karmic these days.....

Maybe you can save me.Which bios version is yours.And what type of cd/dvd drive?

Its been 1 year since i have watched any dvd movies. :(

---

### Post by zaiboot on 2009-10-14
Hello and thank you to everyone.

My pc BIOS version is: 

BIOS Vendor	Phoenix Technologies, LTD
BIOS Version	ASUS M2A-VM ACPI BIOS Revision 1604
BIOS Date	12/19/2007

My DVD is:
IDE ATAPI DVD ROM
ATAPI DVD A DH20A4H	 	
[General information]
	Drive Model:	ATAPI DVD A DH20A4H
	Drive Revision:	QP53
	Device Type:	DVD+R DL
 		
[Device capabilities]
	Drive can read:	CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD-RAM, DVD+R DL
	Drive can write:	CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD-RAM, DVD+R DL
:guitar:

---

### Post by rajeev1204 on 2009-10-15
This is my bug report

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425756](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425756)

---

