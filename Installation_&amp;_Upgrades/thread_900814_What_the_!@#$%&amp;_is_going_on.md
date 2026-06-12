---
title: "What the !@#$%&amp; is going on?"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by squashpup on 2008-08-25
I've installed Hardy on no less than four different computers now, from three different install disks.  Not one hitch in the bunch...everything went as smooth as silk.

Until this morning.

At the school where I teach, I have a bank of computers for student use.  Not wanting to wait on tech support and actually needing them to run, I chose Xubuntu.  

Since it's the start of a new school year, I thought I would do a HD wipe/upgrade to start the new year right.

So, before leaving for work this morning, I burned two install CD's from an ISO of the alternate installer I had sitting on my laptop.  This is the same ISO from which I installed Xubuntu on my brother-in-law's laptop last week without problem.

When I got to school, neither disk would complete a full installation.  I kept getting error messages saying that a particular part of the installation failed, usually "selecting and installing packages".  So, using the school's computer, I downloaded a fresh Xubuntu and, checking the MD5sum, verified that all was well, both before and after burning two fresh alternate install disks.  

So, I took my two fresh install disks and started installing.  I have five computers.  I started the install on 1 and 2 at the same time.  Computer 1 failed, and computer 2 went off without a hitch.  Then, computer 3 failed *on the same disk I used to successfully install to computer #2*!, and computer 4 installed flawlessly on the same disk that failed on #1!.  I haven't tried computer 5 yet, but when I got home, I checked the MD5 on that ISO that I still have on my desktop.  Perfect match.  So, I decided to take the advice of some others and slow the burn speed down to 1x.  

Finished burning and tried to boot Xubuntu into VMWare.  No dice.  Kept giving me the "no operating system" error. 

So, I rebooted my computer. The disk didn't even boot.  It won't mount at all, and dmesg | tail returns: 

[  370.982120] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  370.982128] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  370.982134] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
[  370.982141] end_request: I/O error, dev sr0, sector 1169832
[  373.378607] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  373.378616] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  373.378622] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
[  373.378629] end_request: I/O error, dev sr0, sector 1169824
[  373.378697] UDF-fs: No partition found (1)
[  373.738545] ISOFS: Unable to identify CD-ROM format.


Looks to me like a bad disk.  But, that doesn't explain why I was able to make a perfect copy earlier.  Also doesn't explain why I get error messages with disks made on other computers, either.

Is this user error, a string of bad luck, or a bug in the Xubuntu installer?  Anyone else having this much trouble all of a sudden?

---

### Post by mrsteveman1 on 2008-08-25
How old are the cd drives? I've seen a bunch of them fail on me, my laptops drive refuses to even read pressed CDs now, and some others i have won't read burned discs anymore either.

---

### Post by squashpup on 2008-08-25
The drives range anywhere from 10 years old to barely two months old.  

This morning, when I burned those CD's, I turned on Burnfree and set the speed at 2x.  Both of those were defective.

This evening when I burned here at home, I set the speed to Auto and turned off Burnfree.

Worked...the disk booted and I just finished successfully checking its integrity right now in VMWare server.  Going to try a full install so I know that the disk is good.

Good idea about the age of the drives.  If I continue to have no success, worst case scenario, I'll move a known good CDROM drive from one computer to another to complete the installations.

I might try to use one of those laser lens cleaners, too, just to see if that might help.  Thanks again.

---

### Post by squashpup on 2008-08-25
Install complete...started VMWare and booted into Xubuntu (running inside Xubuntu) without issue.

Now, I have a known working install CD that has successfully installed at least once.  That's a good starting point.

I guess the moral of this story is that Gnomebaker knows best.  Don't mess around with the default settings!

---

