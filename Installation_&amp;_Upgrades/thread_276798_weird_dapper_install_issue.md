---
title: "weird dapper install issue"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by jnicita on 2006-10-13
Just finished installing dapper on multiple systems with no real issues, got everything working great. After making sure that liked the distrobution and wanted to go with it, I decided to install it on my premium machine. Weird thing is that with ALL releases of dapper, it wont even allow me to install, after hitting enter to start the install, I get a refreshed screen with booting linux, loading the kernal and the system hangs. Its a asus a8n-sli motherboard with a AMX x64 4800 processor. I have tried booting the amdx64 64 bit DVD, the x32 bit DVD, the x32bit CD and none of them get past the inital boot of the kernel. I grabbed my old 5.04 live cd and it booted fine. As did some of the other distro's with a little age. Leads me to believe that it must be the new kernel since none of the ubuntu's at 6.06 are booting, I havent tried 6.10 (except on another computer and it was still too beta for me). 

Not sure if the other hardware would matter but I'll list it

A8N-SLI 
Amd X2 4800
4 Gigs corsair high speed memory
(2) GForce 7900 GTX 512mb/DDR3 in SLI mode
1.1 Terabyte SATA Raid (using Motherboard Raid, not sure if its FakeRaid or not)(4 WD 400 GIG Sata3Raid WD4000YR drives)
(2) 300Gig IDE (hda/hdb) hard drives 
(1) 400gig SATA hard drive (SATA-3G connector)
(2) Plextor 16X DVD+-R drives

Like I said, its not even booting the kernel to start the install, so I havent even gotten that far, however, I want to install Ubuntu on the HDB drive (ide) as all SATA disks at NTFS right now (I own VMWare for Linux, so if I can get this working correctly, I may scrap dual boot for XP in vmware for apps that wont run with Crossover Office Pro and Transgaming Cedega).

I already have been told that the nvidia performace in x will suck since accelerated X doesnt have support for it, and yada, yada, yada. And I havent tried Nvidia's linux drivers yet, but I have a ati on one machine using ati's proprietary driver (lame gl performace) but its a lame ati radon x200 onboard) but hope nvidia's (as I have also been told) drivers are better for linux. Lots of conflicts. Anyways, Im going to start reading and see if I can find out whats up. 

I know 5.04 will install, maybe I have to start there and then upgrade everything slowly to newest revs. This is where my noob comes in, I am not too familar with recompliling the kernel as most of the os's I have used the most recent releases and the included built in tools to perform modifications and/or upgrades. Is using 5.04 and then the upgrades the same as just starting with 6.06 (I can see if there is something wrong with compatiability with 6.06's kernel that I could potentially just upgrade a working box to not working status) 

Anyways, any help, Off to read more now, just hoping someone chimes in with a quick do this..

JN

---

### Post by wpshooter on 2006-10-13
Things to try.

1) clean your CD drive.
2) Make sure CD drive has latest firmware version.
3) Assuming you have nothing on the drive you need to keep (O/S or otherwise) get KILLDISK wiping program and clean everything off of drive and then try install.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by Haegin on 2006-10-13
Good luck getting it working...

(THATS ONE HELL OF A NICE SYSTEM!)

---

### Post by jnicita on 2006-10-13
I need to keep my data on the existing drives, I have 2 dvd drives, I will try booting from dvdr #2. 

I just started messing around with a couple of outher live cd's. Knoppix boots the two penguins, then feeds the "Checking for USB" and hangs there.

I have no USB drives, but do have multi-card pro drive on it (mmc/sd/msd,etc,etc) all the formats around, The bois posts 5 usb devices (all high-speed), I have no media cards in (I assumed maybe it was looking at the 2 2gig memory cards trying to parse them for bootable data?) I dont know..

Im downloading ubuntu 5.10 64bit and since Im playing, if it boots, I'll install it and follow the dapper upgrade instructions, maybe I can identify the issue by upgrading and finding what breaks it...

weird...

Fedora 5 booted, so now I have some weird "does boot" , "doesnt boot"

JN

---

### Post by jnicita on 2006-10-13
Just pushed it further. You maybe on to something with the dvd drives. I pushed the installer farther by attempting to install 5.10. After it got through all the prelimiary questions, and started to locate the cdrom packages, I got the redscreen with cant read cd. I tried to verify media, and althogh the rom light was spinning, it couldnt find the cd or move forward. Guess I'll boot to windows and see if I can update the rom code?

---

### Post by omega_c on 2006-10-13
I don't know how to fix it, but thats a nice system....

---

### Post by jnicita on 2006-10-13
Got it...

Turned out one of the 2 gig XD memory cards was not completely removed from the media card device. 

Weird, but having it in caused the system to hang and/or have problems addresing the cdrom.

I would have never believed it if I read it. 


JN

---

### Post by wpshooter on 2006-10-13
> **jnicita said:**
> Got it...

Turned out one of the 2 gig XD memory cards was not completely removed from the media card device. 

Weird, but having it in caused the system to hang and/or have problems addresing the cdrom.

I would have never believed it if I read it. 

JN

What kind of devices are these ?

Looks like you may have some exploring to do here !!!

---

### Post by jnicita on 2006-10-13
Its a "Flash Genie" (XCR0007BO) Device. Basically its a 5.25 drive bay Card Reader/Writer with a cf/mmc/sd/md/sm/ms/mspro card reader. It comes with a "card" module that pops into a cartridge in the front of the drive bay, and you can eject the whole module and cary it to plug into another computer. The cartridge module shows up as 5 Highspeed USB 2.0 devices in the bios, with the module loaded, I COULD NOT pass USB inspection of the OS installations. 

I did the install with it out, and all worked fine. Rebooting of the system has it hang for 2 seconds during boot, but passes by it fine and everything works. 

Just thought I'd add to this since maybe someone else was experienceing the same issue, it was weird, I couldnt get anywhere with any of the newer kernel based install/live distros, and the older 2.4.11 (I think) versions made it to the media check routines, where they hung as well.

Weird, weird, weird.

JN

All is fine and working now, just trying to locate NVIDIA drivers for X that might actually make use of the 1600 worth of video cards in this box.

I have 4 Dell 2005FP 21" lcd's to feed to the 4 digital outputs as well, but dont think I am going to mess with more than 2 screens...

Later

---

