---
title: "[SOLVED] Alternate Install Disk. HELP!!!!"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by lapishc on 2008-09-25
I am having an issue with the alternate install disk...even after burning it 3Xs!!!

I get the same error when attempting to install or when I check the disk at this install prompt.  

The error is as following:
'The .dist/heardy/main/debian/-installer/binary-amd64/Packages.gz.  Your CD-ROM or this file may have been corrupted.  

Can anyone point me to the proper method to burn this ISO?  Or give me a hint as to what may be going wrong. 

I am using InfraRecroder to burn the ISO to disk...I think at 16x speed.

---

### Post by wpshooter on 2008-09-25
If possible, burn the image at 4X or slower.

---

### Post by prshah on 2008-09-25
> **lapishc said:**
> I am having an issue with the alternate install disk...even after burning it 3Xs!!!

 give me a hint as to what may be going wrong. 

I am using InfraRecroder to burn the ISO to disk...I think at 16x speed.

Are you sure the ISO is OK? Check the md5sum```
md5sum -c ubuntu-alternate.iso
``` Replace the filename as suitable, and ensure that the MD5SUM.TXT file is in the same directory as the ISO.

---

### Post by lisati on 2008-09-25
A common piece of wisdom is to burn ISO images to disk (remember to "burn as disk image", NOT as a data file or bootable data disk) as slow as possible.

Once you've used the md5sum info to confirm a good download, you've burnt it to disk, and  you are able to boot from it and get to the menu, there should be a "check disk for errors" option.

---

### Post by lapishc on 2008-09-25
plz excuse my EXTREME lack of knowledge here.

When I choose to burn the iso at 1x speed infra recorder ramps up to ~17x during the write process.  Should I be concerned about this???

PRSHAH I can't seem to run md5sum from a cmd line(windows) but it does appear that the MD5.txt is indeed on the CDR which I burned the iso to.  

LISATI I was choosing Actions--> Burn image from infra recorder...is that correct??

THANKS FOR YOUR REPLIES!!!

---

### Post by zvacet on 2008-09-25
> When I choose to burn the iso at 1x speed infra recorder ramps up to ~17x during the write process. Should I be concerned about this???

I don´t think so.Maybe you just can not burn in lower speed than that.

> PRSHAH I can't seem to run md5sum from a cmd line(windows) but it does appear that the MD5.txt is indeed on the CDR which I burned the iso to.

[Here]("https://help.ubuntu.com/community/BurningIsoHowto") is explained how to check md5sum in Windows and how to burn iso.

---

### Post by lapishc on 2008-09-25
I have indeed verified that the .iso was not damaged.  I loaded it on to my other machine and ran the check disk function on it and it all checked out.  It must be something to do with my box...any suggestions?  

Here are the specs from my machine
Asus P5NSLI motherboard
Intel Pentium D CPU 3.4GHz
LGA 775
NVidia nForce 570 SLI
nVidia GeForce 6200 TurboCache
AI overclocking
2x500 Seagate HD(Master and Slave arranged in a RAID array for mirror backup)


Thanks again for you help: you guys:guitar:

ccl

---

### Post by Partyboi2 on 2008-09-25
Maybe your cdrom does not like that particular brand of disk that you have burn't, try another brand. Another option to try  is cleaning your cdrom lens.

---

### Post by prshah on 2008-09-26
> **lapishc said:**
> 
The error is as following:
'The .dist/heardy/main/debian/-installer/binary-amd64/Packages.gz.  Your CD-ROM ... may have been corrupted.  


> **Partyboi2 said:**
> 
Another option to try  is cleaning your cdrom lens.

+1; maybe the CDROM drive is nearing it's EOL (End Of Life?)

---

### Post by lapishc on 2008-09-26
'+1; maybe the CDROM drive is nearing it's EOL (End Of Life?)'

The box is <1 year old, but maybe the CD drive is a piece of junk.  

Can you suggest a good method to burn the iso to a USB drive?  The methods I have been able to find are very vague or from ~3 years back and may not be applicable. 

Thanks again for the continued comments.

ccl

---

### Post by Sef on 2008-09-26
> Can you suggest a good method to burn the iso to a USB drive? The methods I have been able to find are very vague or from ~3 years back and may not be applicable.

Read this [HowTo]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by lapishc on 2008-09-26
I have burned the ISO to a USB drive with UNetbootin and it now hangs at a command prompt which reads

SYSLINUX 3.71 2008-07-31 CBIOS....
could not find kernel image:

I then went back and performed the optional portion of the directions and I still received the same error.  

ANY CLUE AS TO WHAT THIS COULD BE???

---

### Post by lapishc on 2008-09-28
I have resolved the problem that I presented when I started this thread.  Hopefully this can help others that may have a similar issue. 

This was solved by disabling RAID in BIOS.  I have Phoenix Award BIOS and NVIDIA MediaShield RAID controller.  I tried every mirrored and striped configuration in MedaiShield to no avail. It was a simple solution at the end of the day but a round about way to get there.

Thanks for all your help.

:D

---

