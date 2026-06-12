---
title: "Urgent help!!!"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Mehektet on 2008-02-08
I forgot the origional post but I had asked for help because the installation would freeze on me and I was told to go for the installation with out the live section on it.  I did so and the thing froze at 92% of installing the core system and now my computer will not boot to anything.  It tells me the following.

PXE - E61: Media test faliure, check cable.
PXE - M0F: Exiting PXE Rom

I have little experience with computers and this was suposed to be an easy installation.  I followed all the directions to the letter and not I can't even load Windows.  Someone pelase tell me what to do I really need the info on my labtop as it pertains to work.  Thank you.

-Mehektet-

---

### Post by Mehektet on 2008-02-08
I mean that I used the text installer.

---

### Post by jeffus_il on 2008-02-08
I found this:
> [FONT=Arial,Helvetica][SIZE=2] The Intel support page (scroll down to almost the bottom of the page):[/SIZE][/FONT][FONT=Arial,Helvetica][SIZE=2]http://www.intel.com/support/motherboards/desktop/sb/CS-010254.htm#pxeerror[/SIZE][/FONT]
[FONT=Arial,Helvetica][SIZE=2]describes this error message:[/SIZE][/FONT]
[FONT=Arial,Helvetica][SIZE=2]Quote
Error "PXE-E61 Media Test Failure" at Boot
The error PXE-E61 Media Test Failure can occur at boot, if all the following are true:[/SIZE][/FONT]
[FONT=Arial,Helvetica][SIZE=2]Boot to LAN is enabled in BIOS Setup. 
A network cable/connection is not present. 
Network Boot is in the boot order before a present boot device. 
To resolve this, remove Boot to LAN from the list of boot devices in BIOS Setup.
End of Quote[/SIZE][/FONT]
[FONT=Arial,Helvetica][SIZE=2]Open your BIOS and check to see if Boot to LAN is in the startup order.  Then remove or disable it.[/SIZE][/FONT]


on this page:
[http://www.nocrash.com/ncbbs/msgs/3247.shtml](http://www.nocrash.com/ncbbs/msgs/3247.shtml)

---

### Post by Mehektet on 2008-02-08
> **jeffus_il said:**
> I found this:


on this page:
[http://www.nocrash.com/ncbbs/msgs/3247.shtml](http://www.nocrash.com/ncbbs/msgs/3247.shtml)


I tried most of what they say and it still does the same thing.  The last thing I remember is that it said something about the Kernel.  But I am not sure what that means.

---

### Post by jeffus_il on 2008-02-08
It seems like the message appears in Windows installations (see the link I gave you) as well, and is connected to a hardware problem, not an operating system problem, the kernel is the "heart" of the Linux OS. I would check all hardware, have you changed hard disks or other drives/media recently?

---

### Post by MonctonJohn on 2008-02-08
The PXE messages mean that your computer is trying to boot from the Local Area Network. In your boot order PXE is usually last after the Hard drive. Since it doesn't boot of the Hard drive I would say you installation of Ubuntu is bad. If you have access to the internet and a cd-burner, try to burn another copy of Ubuntu. It could be that your original cd had errors on it. Try to boot the live version of the new cd. If your installation does not finish then you most likely have a hardware problem (bad cd, bad cd-rom drive, bad hard drive). Try a new cd to start. If that doesn't work then run a diagnostic on the hard drive (google ubcd).

---

### Post by Mehektet on 2008-02-08
> **jeffus_il said:**
> It seems like the message appears in Windows installations (see the link I gave you) as well, and is connected to a hardware problem, not an operating system problem, the kernel is the "heart" of the Linux OS. I would check all hardware, have you changed hard disks or other drives/media recently?

I made no changes to my hardware and before I tried installing Ubuntu it was loading just fine.  I was thinking of buying a USB Key and trying the installation that way to avoid having to format ans lose my info.  Does anyone think this is a good idea? 

Also is there a way to force a DOS command prompt so I can try to boot up windows mannualy?

-Omar-

---

