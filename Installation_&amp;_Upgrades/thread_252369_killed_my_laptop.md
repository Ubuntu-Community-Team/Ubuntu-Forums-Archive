---
title: "killed my laptop"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by chefjames on 2006-09-06
If I need to be in a different forum please direct me there.  

Sorry for the long post for help, but I don't know the technospeak to shorten it up.  Thanks in advance for any suggestions.

I have a Micron Trek 2 laptop with the following:
Intel Mobile Pentium II 400MHz
128 MB RAM
ATI Rage LT Pro AGP 2x video card
ATA 27 GB Hard Drive
Phoenix BIOS 4.0 Release 6.0
Windows 2000 pro
ESS Maestro sound
ATAPI Sony CD-RW/DVD rom model CRX810E
ATAPI LS-120 SLIM 03 UHD floppy

I tried to run the Ubuntu Dapper Drake live CD on with the hope of installing it and replacing Windows 2000.  Somewhere in the process of loading Ubuntu the machine froze.  I was left with a black screen and a cursor blinking in the top left corner.  After several hours of this I gave up, removed the CD and pushed the power off button because no other combination of keys did anything noticible at all.

Now I get a blue screen with an error with a bunch of zeros and the message inacessable boot device.  I can still access the BIOS setup  area and the Windows boot mode options, but no combination of boot mode or bios setting gets me anything other than the same error screen.

Windows support websites all basically said to repair or reinstall W2K from floppy or CD.  I don't have these disks.  I bought the laptop used off e-bay and it didn't come with any disks floppy or otherwise.

Since I don't care about having Windows how can I just replace it.

Puppy Linux works from liveCD, but I really want a hard drive resident OS that doesn't require a CD everytime I start the machine.  An annoying reason for this is that the BIOS on my Micron absolutely refuses to boot from the CD drive.  I have to use a floppy with BCDL on it to direct the machine to the CD drive in order to boot from CD.

Thanks again

---

### Post by meng on 2006-09-06
The LiveCD is only recommended for machines with 192MB RAM and upward. You should still be able to install and run Ubuntu/Kubuntu/Xubuntu, but you should download the Alternate ISO/CD. BTW Puppy can be installed to a hard drive, but it defaults to running all the time as a privileged/root user.

---

### Post by chefjames on 2006-09-08
Many thanks!  The alternate CD worked great except for the partition utility.  I had to download a utility and erase the partition and rename it as a linux area (Maybe because it was NTFS?).  I am now enjoying getting used to Ubuntu.  Thanks again.

---

### Post by meng on 2006-09-08
Perfect. Don't hesitate to post again if you hit a snag.

---

