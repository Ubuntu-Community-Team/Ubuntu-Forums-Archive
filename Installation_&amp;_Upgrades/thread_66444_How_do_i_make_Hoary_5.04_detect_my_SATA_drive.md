---
title: "How do i make Hoary 5.04 detect my SATA drive?"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by netneo on 2005-09-17
HI

My specs:
My system is:
Processor---->AMD Athlon A64 3000+ having Socket 939
Motherboard----->MSI RS480 with ATI x300 Onboard gfx
Ram------>512 Mb DDR
Hard Disk----->Samsung 80 Gb SATA

I had installed WinXp with NTFS and 3 partitions of sizes 29.2,29.2 and 15.9 gb respectively

Firstly,i am a total noob...so how do i figure out what SATA controller i have...cant find it in the device manager...

Secondly..how do i make changes to make Hoary 5.04 recognise my 80 gb SATA drive...

Currently during the Hd install it says "No partitionable media was found."

The LIVE CDs also suck..tried three of them and all froze on the splash screen

I cant use qt parted as well to partition my drive since it doesnt detect any disks..instead o the interface it has a blank column where the disks are supposed to be shown.
Shouldnt Hoary 5.04 resize my NTFS for me anyways?

and more importantly..how do i make Ubuntu recognise my SATA drive..

I really want to install Hoary 5.04 and dont want to wait for Breezy Badger till October..

does anyone else have a solution or is someone with a similar mobo out there?

I know this topic has been repeated quite often in the forums but i really couldnt find anyone with a similar mobo or someone whose query had been solved...if there is no solution but to wait till October..please lemme know..but dont keep me hanging!

Thank you very much

---

### Post by _jB on 2005-09-17
Had some problems with my 2 160gb sata disks also..
I dont use raid (windows) so i disabled it in bios = no drive @ ubuntu.
After enabling raid again, linux had no problems seenin and mounting my sata's ;)

---

### Post by netneo on 2005-09-17
But isnt RAID supposed to be activated only if u have multiple Hdd?

I have only one of 80 gb

Will enabling RAID for me work as well without any probs?

---

### Post by tseliot on 2005-09-17
I had an MSI RS480 and a Seagate Barracuda SATA 160gb and I had the same problem. I had to install Hoary to a PATA harddisk. Moreover the motherboard has several problems as it is not supported by Linux (DON'T BUY THIS MOTHERBOARD). In my case I managed to solve the following problems:

1) the double clock speed problem > I made a HOWTO about that
2) DMA issues > I made a guide for newbies about kernel compilation
3) The computer froze randomly. It said something about Unix fonts. I've tried almost every method I found in Google but nothing worked and I gave in.

In the end I bought a new computer and stopped worrying about the issues. Remember to check the hardware compatibility with Linux on the Internet before buying it.

By the way the right module if you want to use a SATA drive is "[COLOR=Red]sata_sil[/COLOR]". I hope someone can help you. I really wouldn't know how to make the Ubuntu installer load it before the installation.

---

### Post by netneo on 2005-09-18
i guess il just have to wait till breezy is released

Bummer

---

### Post by ben2005uk on 2005-09-27
I've got the ECS RS480 and having problems installing Breezy :'( ,  is this a linux problem or a ubuntu problem?

---

### Post by rurouni_smc on 2005-09-27
[quote=netneo]i guess il just have to wait till breezy is released
 
Bummer[/quote]
 
Breezy allowed me to install on one of these motherboards to my SATA drive with out any problem. Where 5.04 was not letting me.

---

### Post by 23meg on 2005-09-27
the breezy kernel definitely plays better with sata. give the live cd a try and see if it detects the drive.

---

### Post by jaded on 2005-09-27
hey...me gots the same problem.still tryin to figure it out
i got a 3000+ amd 64 bit proc.and 120gb sata hard drive,  with 5gb reserved and unallocated for installing ubuntu. but no media was detected for me too.need help urgently.....as for you my friend, try creating RAID support for your hard drive. it was suggested for me , but didnt work. so my problem is worse....

---

### Post by jaded on 2005-09-27
hey....can anyone help me with the problem? the 5.04 installer isnt detecting my sata drive or even my network cards....

---

### Post by ben2005uk on 2005-09-29
I know this might sound silly - but would KUbuntu be any different??

AMD64 didn't detect my drive + X86 did so was wondering if kUbuntu would work for me....

I really really want to install ubuntu !! Dont want to have to use vmware......but i guess im going to have to

---

