---
title: "Install/Boot issues..."
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by whiskey212 on 2008-04-14
I am hoping for some help here as I am relatively new to Linux. I have tried several times to install Ubuntu to my system without much luck. I have a custom build which is currently booting Vista and I want to install Ubuntu to a separate hard drive which I have bought and set aside specifically for using Linux. I downloaded the 7.10 live cd and tried to install from that and everything seems to go well until it comes time to remove the disk and boot from the drive. On reboot I get a message saying "Missing Operating System". I just installed the OS and I changed the boot order in BIOS to put the Linux disc first so everything should be hunky dory but apparently not. What am I doing wrong?

---

### Post by Peter09 on 2008-04-14
Grub, the Linux boot manager will manage the boot order of the disks. By changing your boot order in the BIOS you have by passed GRUB. Change your boot order in the BIOS back to how it was during the installation. It should then work.


PC

---

### Post by njparton on 2008-04-14
I would install without the windows drive attached to your motherboard, then use the boot manager (present on most modern motherboards) to boot between windows and linux.
 
That's what I do. I have to hit F12 during POST to enter the BIOS boot menu and select a different hard drive than the first one set in the BIOS.

---

### Post by whiskey212 on 2008-04-15
This has no effect. It's actually Esc on my board and when I select the HDD I have Linux on it gets me right back to the "Missing Operating System" message. I am really getting frustrated by this.

---

### Post by whiskey212 on 2008-04-15
I need to know how to get Linux to boot if changing the boot order in BIOS and selecting the drive in the boot order on startup still result in the "Missing Operating System" message. Someone out there must know how to help me.

---

### Post by martrn on 2008-04-15
Hello whiskey212#,

Your post indicates you are receiving a POST (power on self test)  message that you have a " Missing Operating System".

Normally this would indicate one of several things ---

•	The basic input/output system (BIOS) does not detect the hard disk.
•	Sector 0 of the physical hard disk drive has an incorrect or malformed master boot record (MBR).
•	An incorrect set partition table or your partition table is incorrect.

From my guess from your post I would conculde that Sector 0 of your first hard disk drive has an incorrect or malformed master boot record (MBR).

What operating systems can you boot ? Can you boot windows ? Can you boot ubuntu ?

When you was installing ubuntu did ubuntu write grub to the master boot record (MBR), and which disk did it write the master boot record to ??? I presume it would have installed the master boot record (Grub) to the first hard disk (and thus over-righting the windows Master Boot Record)) ???

It is difficult to give any clues as to what to do with out realise your set-up and what disk has what on it and what your master boot records current are.  To dual boot windows/ubunut you can install grub to any master boot record and boot windows and linux.

I would recomment to installing grub to a flopp disk configuring grub correctly there and then installing grub to your MBR (master boot record) of the first hard disk in the system, once you have the correct grub settings.

The installing grub from a live CD thred which explains the process better than I can is here :- [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Pumalite on 2008-04-15
If you have a bootable Linux in your system, Super Grub will be able to boot it. Otherwise, you might have a failed installation.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by torgrot on 2008-04-15
You just need to install grub to the boot sector of your linux disk.  Check out this link by Herman [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

torgrot

---

### Post by yngvrr on 2008-04-15
Hi, I am using a  compaq nx9005 and I am having a problem booting thu ubuntu cd. It wont boot from the cd.. If I start the boot menu by pressing Esc before windows starts end click on "boot from cd" the boot menu closes and then windows starts normally... 
What should I do now??
anybody please! If been trying to figure this out for 4 hours and I'm not even close....

---

### Post by torgrot on 2008-04-15
Its not nice to hijack a thread.  See the wiki about checking the md5 sum of the iso in windows.  Sounds like you have a bad cd.

torgrot

---

### Post by yngvrr on 2008-04-15
Yes sorry.. mean to steal the thread.. didnt realize yet that it was a special thread.. And now I have created my own... new user..

---

### Post by whiskey212 on 2008-04-18
Well I tried that stuff with the GRUB disk and whatnot, didn't work. Now I get to the same screen and it says "Error 17: Cannot mount selected partition". Oh and one more good thing, now I can't boot Vista either. You know this is all seeming like way too much work. I am starting to gain a real appreciation for Microsoft, I didn't think that would EVER happen. But I still hate Mac, so at least that's still good.

---

### Post by martrn on 2008-04-18
If you wish to fix your master boot record in windows boot your windows [rescue cd] and run a command called 'fixmbr' To correct your master boot record.

 [ http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113") Gives a large guide on how to restore you master boot record if your master boot record is messed up.

The error message you are getting indicates your master boot record is not able not being able to locate the files it needs, on the partition it's configured for.  There appears no error message regarding you anything else.

---

### Post by whiskey212 on 2008-04-19
If there is no other problem then what does "Error 17: Unable to mount partition" mean? Seems like a bit of a problem to me.

---

### Post by Pumalite on 2008-04-19
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by martrn on 2008-04-20
> If there is no other problem then what does "Error 17: Unable to mount partition" mean? Seems like a bit of a problem to me.

"Error 17: Unable to mount partition" means the bootloader is present but not working.  It can't find the files.

An operating system, like windows or ubuntu boots in several stages.  It boots the bios (usually from the motherboard), the BIOS tell the machine to boot the MBR (master boot record from one on the hard disks (or a CD or a floppy).  The master boot record will look on the file system where the MBR resides for some files.  From what files it finds on this system it will then boot the appropriate kernel.

If you have grub installed it will look for a directory called /boot/, where it belives config files reside.  You should be able to boot windows, from the command line or even linux from the command line if stuck at a command line grub.  

Your bios/masterbootrecord it confused about where the linux kernel / windows kernel / bios is and the diffrent disks.  

Read [http://users.bigpond.net.au/hermanzone/p15]("http://users.bigpond.net.au/hermanzone/p15").htm#17 about how to put the MBR on the other disk, and switch this around in the bios.  Read about the yin/yang thing.

---

### Post by whiskey212 on 2008-04-22
So I thought to myself, "Self, what if these guys are right? What if you buggered up the install and just need to fix that?" So, reinstalled Ubuntu, twice. I also tried Kubuntu, Fedora and Mandriva, just in case any of those worked any different, and no dice. I get the same damned message, "Error 17: Cannot mount selected partition". Even booting through Super Grub gets me the same message. There has got to be a way to fix this, can't anyone out there help me out?

---

### Post by Partyboi2 on 2008-04-22
Have you double checked the hard drive that its installed correctly? eg the jumper settings etc...

---

### Post by martrn on 2008-04-22
> **Partyboi2 said:**
> Have you double checked the hard drive that its installed correctly? eg the jumper settings etc...

As well as checking the jumper setttings to the hard drive I would also check the BIOS to make sure that it has no Anti-Virual protection method to prevent or protect Master Boot Records.

I did say :
> The error message you are getting indicates your master boot record is not able not being able to locate the files it needs, on the partition it's configured for. There appears no error message regarding you anything else.

Apparenty some people have had sucsess with installing GAG as their boot-manager..
See :--- [http://www.hezardastan.org/breezy_xp_dualboot/en/gaginstall.html]("http://www.hezardastan.org/breezy_xp_dualboot/en/gaginstall.html")

Also try updateing your BIOS from your motherboard manafacture and check any know problems with your BIOS.

---

