---
title: "Lubuntu and Xubuntu installation problems when trying to install on hard drive"
date: 2012-03-29
forum: Installation &amp; Upgrades
---

### Post by fernator on 2012-03-29
Hello, I am since a few weeks ago trying some Linux OS and I decided I would like to install Lubuntu on hard drive.
I choose the option to install in paralel with windows xp

But I don't know why, I can't install. I tried several times and sometimes after choose the time zone, it stops in the "Congratulations" menu. Other times (the majority) when appears the menu to choose the time, it says something like it can't mount because of the cd rom. I take out the cd rom (I am using a cd rom with plop to boot from usb) and it stops, I put the continue button but the menu of take out the cd rom doesn't disappear.

I even tried to install xubuntu but the same happens. On xubuntu, sometimes it appears to take out the cd rom and sometimes not. But when it appears, it always continue the installation.
I am writing from the installation of xubuntu, right now it is stopped since a lot of time in the congratulations menu and when i click in the end it shows this:
(I don't know how to copy the all text, so I will write the 2 last phrases)
---
ubuntu ubiquity [3074]: Ubiquity 2.8.7
ubuntu ubiquity [3074]: log-output -t ubiquity laptop-detect
---

Anyone know what might be the problem?

---

### Post by papibe on 2012-03-29
Hi fernator. Welcome to the forums!

Could you tell us a little bit about your machine?  Like processor, RAM, disk space?

Regards.

---

### Post by fernator on 2012-03-29
I don't remember very well, I don't know if there is some way to know that from the installation of xubuntu.

What I remember is that RAM has 500 mb and the hard drive is 20 gb.

I decided to quit from xubuntu installation and now I am on Winxp and my hardware is:

System Manufacturer	ASUSTeK Computer INC.
System Model	A7N8X-X
System Type X86-based PC
Processor	x86 Family 6 Model 10 Stepping 0 AuthenticAMD ~1143 Mhz
Date / BIOS version 	Phoenix Technologies, LTD ASUS A7N8X-X ACPI BIOS Rev 1009, 03-02-2004
SMBIOS	2.2
Boot Device	\Device\HarddiskVolume1
ardware Abstraction Layer (HAL)	Version = "5.1.2600.5512 (xpsp.080413-2111)"
Total Physical Memory 	512,00 MB
Available Physical Memory	78,56 MB
Total Virtual Memory	2,00 GB
Available Virtual Memory	1,96 GB
Page file space	866,23 MB

---

### Post by critin on 2012-03-29
> I choose the option to install in paralel with windows xp

What I remember is that RAM has 500 mb and the hard drive is 20 gb

A 20 gb disk isn't large enough for 2 OS's.  IMO  

Go to disk management in Windows and see how much space is left on the drive.

---

### Post by fernator on 2012-04-02
I still have 10 gb free
And in the installation it says it only needs about 4,5 gb or something, so maybe that's not the problem

---

### Post by oldfred on 2012-04-02
Windows NTFS likes 30% free or it starts to get slow.  At 10% free it just about stops working. 

Ubuntu will install in 4.5GB but you will almost immediately run of of space on updates and will not have room to install much. You also should have swap at 1GB if you only have 500MB of RAM.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by fernator on 2012-04-02
oldfred I am trying to install Lubuntu, not Ubuntu
Wikipedia says it only needs 256 mb of Ram "Lubuntu 11.10 requires a minimum of 128 MB of RAM to run and 256 MB of RAM to install with the graphic installer. The recommended minimum RAM to run a live CD session is 384 MB"

And for now I am not worried about after the installation.
I am worried is that I can't even install it in the hard disk. I already tried by usb and it works well, the problem as I said before, is that I can't install in hard drive

---

### Post by oldfred on 2012-04-02
The issue may then just be plop. I have seen posts where it has worked. What version are you installing.

Can you remove hard drive and use another computer to use to install so you do not have to use plop?

---

### Post by fernator on 2012-04-02
I tried to install Lubuntu 11.10 and Xubuntu 11.10.

It will be a bit complicated to get another computer to install.

But does it work? I mean, if you install windows in another computer mother board and then put the hard drive in another computer mother board, it doesn't work. Does it work with Lubuntu?
I could install in another computer, then put the hard drive in this one and this would work without problems?!!

---

### Post by critin on 2012-04-02
Linux is open source, you can use it on any computer.  Yes, you can install on one computer's hdd and move the hdd to another computer.  Windows is licensed for only one setup.

---

### Post by fernator on 2012-04-02
ok, I will try that

---

### Post by fernator on 2012-04-02
This is really incredible, it seems nothing work with me

I tried to install on another computer. While the old computer can boot from the usb with the help of plop, the newer one, don't boot from the usb even with flop.
It doesn't boot from lubuntu usb, so then I put ploop to force usb and in plop it says something like no device found or something.

Then in the new computer I entered in windows 7 and the usb was working very well, I could see the files and even click in wubi.exe or something like that.

So in the new computer, it can't even boot from lubuntu usb, it doesn't recognize it as a boot usb

So back to the old computer trying to install again and hoping for some miracle, but the same.. I choose the time, etc, then goes into the congratulations menu and nothing happens, no evolution.

---

