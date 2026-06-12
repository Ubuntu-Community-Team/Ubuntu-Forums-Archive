---
title: "Unbuntu Install Screen Absent *Black*"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by richard113 on 2015-04-24
Hello All,

I am a new Ubuntu/Linux user and have run into a wall during the installation process of the 14.04 LTS.

Diving right into it;

I use windows 8.1 currently and have partitioned a second hard drive in my computer to use a strictly Ubuntu HD with my other HD being for Windows 8.1 only.
After downloading the 64bit install and creating a LiveUSB with the UUI Software suggested by the site I go ahead and begin the installation process of Ubuntu.
I mad sure Secured Boot was disabled and that I didn't have Fast Boot on either. 
My USB Drive shows up as a Bootable UEFI device in my boot menu and I go ahead and select that. 
Now once in the menu

 >Try Ubuntu
 >Install Ubuntu
 >(Something Else)
 >(Something Else)

I select Try Ubuntu and my screen go black and my monitor immediately goes into power saving mode. 
My Computer is still running however and nothing ever comes back on the monitor, granted the computer doesn't sound as if it is working more so of an idle state.

I cant for the life of me figure out how to fix the issue as it is keeping me from installing the OS which I need for some stats & model crunching for work.

If anyone has a fix or work around for this that would be wonderful and greatly appreciated.

[U]My Computer Specs are as follows.
[/U][FONT=tahoma]
[/FONT][SIZE=2][FONT=tahoma]**OS**: Windows 8.1 64bit
**Motherboard**: Gigabyte G1.Sniper M5
**BIOS: **Date 05/16/13 Ver; 04.06.05
**CPU**: Intel i5 4670k 3.4ghz
**RAM:** 8gigs Munchkin Ram
**Video Card**: GeForce GTX 660Ti 4gig
**Video Card Driver:** 9.18.13.4709
**Direct X 11**
**Monitor**: Dell U2415 - w/ mini Display Port connection
[/FONT]**Storage**: Two, 1TB Seagate HD's
[/SIZE]
**Note**: My ideal setup, once my SSD arrives on Saturday is going to be 
-50/50 Partitioned 256gig SSD for Windows 8.1 and Ubuntu Operating Systems
-1 TB HD Storage for Windows 8.1
-1 TB HD Storage for Unbuntu

---

### Post by dino99 on 2015-04-24
its a graphic driver issue, which 14.04 & 14.10 often met with recent graphic hardware like yours. Better to run 15.04 which have recent stable driver

---

### Post by richard113 on 2015-04-24
I did try 15.04 and it still fades my monitor to a power saving mode.

Would i be better off wiping all of my hard drives clean and then trying to install ubuntu on a technically "clean" system. 
I built this computer my self last year so there is no OEM restrictions for wiping it.

---

### Post by sammiev on 2015-04-24
What happens when you try to run a live session from DVD/USB?

---

### Post by Ian_MacQueen on 2015-04-24
This has to be a new problem. I built a new system using a GA-F2A88XN mini ITX MB, AMD A6 7400K processor, MUSHKIN 240GB SSD, and 16GBs of Kingston Platinum Pro. When I installed Ubuntu 14.10, Mint 17.1, Ubuntu 14.04, Ubuntu 6.06 and Fedora 21 I get the same problem. Please bear in mind I am using all new components and not duel booting. The problem is all the disks and usb drives get to the menu and when I pick the proper OS to load I get a blank screen on my monitor. All my bootable disks were made properly and two of them were made by Ubuntu. ( tried two different monitors, one was HDMI and the other was DVI ) goes blank and everything stops. I have been doing a little research on this and one person actually told me to find some older equipment to load Linux on. I want to run Linux as my main OS, I already have a machine with windows. I have also been told that Microsoft has something to do with this. If that's the case then hardware manufacturers are in on it too. I can't disable the secure boot on my VII hero MB so I bought the GIGABYTE MB to get around this. Has anyone got a work around for this yet? I believe we have the same problem.

---

### Post by Ian_MacQueen on 2015-04-24
Please read my reply dino99. I don't believe it's a driver issue with the graphics. My older legacy monitor has the same problem and I have used Ubuntu 6.06 and Debian in the past with it with no problems. Any other ideas?

---

### Post by sammiev on 2015-04-24
When you get to the menu select F6 and choose nomodset. Try to boot from there.

---

