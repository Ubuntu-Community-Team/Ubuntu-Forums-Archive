---
title: "GRUB 21 Error &amp; Can't Return to XP?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by rreyes on 2007-06-18
I made an installed of the Ubuntu OS, version Feisty Fawn 7.04, from the down loaded CD. I installed the Ubuntu OS to an external USB La Cie HD. After the install I went to boot of the La Cie HD and my laptop will gave a message of "No OS". I can not reboot off my laptops internal drive back to Windows XP. I get the "GRUB 21" Error. I went into the BIOS to try to reset boot sequence back to defaults, but no luck. I still get the same error. I can still run the Ubuntu CD and run the OS. I could see all the normal files on both HD's so I know I didn't over write the internal laptop HD. Any suggestions on how to get my laptop to re-boot to Windows again? :confused:

---

### Post by Pumalite on 2007-06-18
> **rreyes said:**
> I made an installed of the Ubuntu OS, version Feisty Fawn 7.04, from the down loaded CD. I installed the Ubuntu OS to an external USB La Cie HD. After the install I went to boot of the La Cie HD and my laptop will gave a message of "No OS". I can not reboot off my laptops internal drive back to Windows XP. I get the "GRUB 21" Error. I went into the BIOS to try to reset boot sequence back to defaults, but no luck. I still get the same error. I can still run the Ubuntu CD and run the OS. I could see all the normal files on both HD's so I know I didn't over write the internal laptop HD. Any suggestions on how to get my laptop to re-boot to Windows again? :confused:

Windows CD>Recovery>FixMBR

---

### Post by rreyes on 2007-06-18
Original User rreyes with follow up:

I tried everything I could to get my ThinkPad R51 to re-boot back to my internal HD to launch Windows XP. I called Lenovo Support and explained the problem. Lenovo Support confirmed what I thought that the error code "GRUB 21" is a boot record code for Linux that is looking for the HD with the Ubuntu OS that was a bad install on my external La Cie HD. The installer for Ubuntu made a corrupt entry on my internal HD's boot record file during the install process and now my PC cannot find the correct partition to boot off for Windows XP. Lenovo Support now has to send me 6 recovery CDs to re-install Windows XP and I will loose all my data in the process on my ThinkPad. No big deal, but I was hoping for a smoother install because I really like the Ubuntu OS from what I tried on the CD. I will try another method to use Ubuntu in the future by maybe getting a PC from Dell or another manufacture who sells it already installed. I still believe Open Source software is the way to go despite my glitch on this first time install. 

Thanks for your help everyone.

Robert
Lodi, CA USA:guitar:

---

### Post by merlinus on 2007-06-18
Before you pack it in and reinstall, try:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Also, blame Lenovo for not issuing you an OEM WinXP disk when you bought your machine!

-merlin

---

### Post by Howard Kaikow on 2007-06-18
Don't know if this will help, but here's what I recently did.

1. I have a multiboot Windows 000 system, use the NTLoader for booting.
2. I tried to install ubuntu 7.04, but could not do that because my system does not allow booting from USB drives.
3. I then managed to create two small partitions on 1 of my hard drives.
4. I did manage to install linux on the hard drive and used the NTLOader, not GRUB, to control to which OS I boot.

I did the install from the LiveCD.

Using the LiveCD you should be able to instal;l Linux and edit the Windows boot.ini so you can get ypur multiple boot. My boot.ini is given below.


Note do NOT install GRUB to the MBR.
Use the notation (hdx,y) to specify where GRUB is to be installed.

Most importantly, read [Give up on Linux????]("http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=21;t=5731"). You'll see the pain I went thru.

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(2)partition(2)\WINNT
[operating systems]
multi(0)disk(0)rdisk(2)partition(2)\WINNT="J: Microsoft Windows 2000 Professional" /fastdetect
signature(32a7e53f)disk(1)rdisk(0)partition(2)\WINNT="G: Microsoft Windows 2000 Professional" /fastdetect
signature(32a7e53f)disk(1)rdisk(0)partition(1)\WINNT="F: Microsoft Windows 2000 Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="C: Microsoft Windows 2000 Professional" /fastdetect
C:\grubold.lnx="OLD Ubuntu Linux"
C:\grubboot.lnx="Ubuntu Linux"

```

---

