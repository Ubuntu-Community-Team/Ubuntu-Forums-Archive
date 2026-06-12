---
title: "Can't boot Ubuntu - please help"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by zhinker on 2007-04-19
Hi, I've been trying to dual boot linux on my computer for a while.  First I tried Mandriva, but after installing it, Mandriva would run properly maybe 5% of the time, the rest of the time it would just freeze in the boot screen.  So I tried installing Ubuntu 6.10 and that installed fine as well, but when I tried running it I would get this error saying something about the x graphical interface being wrong/missing (or something like that).  I recently downloaded the newest version of Kubuntu hoping it might have fixed whatever problem I have, and while the Grub screen came up and seemed to work fine (the grub screen is the linux equivalent of microsoft's command screen, right?), when I tried to start a proper image-based desktop (by typing in xstart or startx) it would run for a bit and then say that the x graphical interface is missing (again, it was something like 'x graphical interface', I didn't write down the exact error message when it came up)
:confused: 
Is it some incompatibility with my hardware?  This is the information I thought would be relevant from my device manager.   Any help in joining the linux community would be appreciated.

Computer
.....ACPI Mulitprocessor PC
Display adapters
.....Raedon X600 Series
.....Radeon X600 Series Secondary
IDE ATA/ATAPI contrillers
.....Intel(R) 82801 GB Serial ATA Storage Controllers - 27C0
.....Intel(R) 82801 GB Ultra ATA Storage Controllers - 27DF
.....Primary IDE Channel
.....Primary IDE Channel
Modems
.....Intel(R) 537EP V9x DF PCI Modem
Monitors
.....Dell E173FP
Network adapters
.....Intel(R) PRO/100 VE Network Connection
Processors
.....Intel(R) Pentium(R) 4 CPU 2.80 GHz
.....Intel(R) Pentium(R) 4 CPU 2.80 GHz
SCSI and RAID controllers
.....D347PRT SCSI Controller
Sound, video and game controllers
.....Audio Codecs
.....AVerMedia AVerTV Video Capture (M113, Phillips FM1236MK5 Tuner)
.....Legacy Audio Drivers
.....Legacy Video Capture Devices
.....Media Control Devices
.....SigmaTel High Definition Audio CODEC
.....Unimodem Half-Duplex Audio Drive
.....Video Codecs

---

### Post by rillip on 2007-04-19
It's not clear how you're trying to install it.  The error would seem to indicate xserver-xorg is not installed.

Grub is just a boot manager, it has nothing to do with the Linux terminal session, excepting that it can load one.  It just lets you pick where you want to boot to.

It sounds like you are getting to a terminal session.  Try 

sudo apt-get install xserver-xorg

Let that run, and if succesfuly, run

sudo dpkg-reconfigure xserver-xorg

It'll take you through a text based menu system to configure xserver for your hardware.

The try 

startx

Please write down any error messages you get so we can help you further.

Additionally, if you haven't tried it, burn a LiveCD iso. You download the image from ubuntu.com, burn the CD, then you can boot directly from it.  It's a fully, live version of the OS running from your CD.  It lets you figure out if you're going to have compatibility problems in advance. It doesn't sound like you're trying to use this to install, though.

---

### Post by expatCM on 2007-04-19
I was wondering whether this is a hardware issue or an installation challenge.

Does the computer boot and operate if you boot Ubuntu as a Live CD?

---

### Post by xyz on 2007-04-19
> **expatCM said:**
> I was wondering whether this is a hardware issue or an installation challenge.

Does the computer boot and operate if you boot Ubuntu as a Live CD?
Yes it does if your BIOS is set to boot on the CD-ROM first.

---

### Post by expatCM on 2007-04-19
So again, just to be clear, in order to install, did you first boot to the CD having changed your BIOS boot order and then click on the desktop icon in order to start the install process or did you follow some other route?

---

### Post by xyz on 2007-04-19
> **expatCM said:**
> So again, just to be clear, in order to install, did you first boot to the CD having changed your BIOS boot order and then click on the desktop icon in order to start the install process or did you follow some other route?
That's right if you downloaded the Desktop Install CD.

If you have the Alternate CD, just follow the install procedure once you popped the CD into your CD-ROM. Hope this helps.

---

### Post by zhinker on 2007-04-19
Yeah, I tried booting from the live CD first, but even then I could only get access to the grub screen (and that was only with the Kubuntu live CD, I couldn't even the the Ubuntu 6.10 and Mandriva 2007 live CDs to finish booting), not the KDE or anything else.  Then being the smart person I am, I tried installing the software anyways thinking that it might just happen to work better once it's installed.  No such luck :( 
So right now I've got Ubuntu 6.10 installed on my pc.

---

