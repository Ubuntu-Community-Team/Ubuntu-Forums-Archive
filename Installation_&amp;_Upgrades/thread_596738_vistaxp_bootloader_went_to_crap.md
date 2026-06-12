---
title: "vista/xp bootloader went to crap"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by dracule on 2007-10-29
I tried installing wubi, but it crashed thus leaving my vista loader corrupted. i had a lab report due the next day so i installed linux,

now grub gives me the option to boot into the longhorn(loader) but that is corrupted, so i cant boot into xp or vista. i have no disks with me to do this.

is there a way to add an entry into grub to bypass the vista loader and boot directly into vista/xp?

---

### Post by taurus on 2007-10-29
Try this, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

---

### Post by maxlpk on 2007-10-29
yeah this happened to me too... (and i didnt even install grub on the mbr but on the ubuntu / partion)
Boot with your Xp or XP recovery disk and use the option to fix vista boot problems...
then (assuming you didnt put grub on the mbr ) use easybcd(in vista) to add your ubuntu to the vista bootloader.
if you did install grub to the mbr you will have to boot your ubuntu disk and run grub to tell it which partion to install on, then the above 
hope that helps.

---

### Post by dracule on 2007-10-30
Ok, i have no vista or xp recovery or install cd's


cant i just add a grub entry permenatly to my install?

---

### Post by dracule on 2007-11-01
> **dracule said:**
> Ok, i have no vista or xp recovery or install cd's


cant i just add a grub entry permenatly to my install?

sure nobody knows the answer? like what i meant was with my current grub config file, can i add a vista entry and an xp entry and bypass vista's loader?

---

### Post by louieb on 2007-11-01
I don't believe you can bypass the XP  boot loader. XP is booted to in GRUB by using **chainloader +1** what this does is transfer control to the boot sector of the XP partition. Thats where the XP boot loader **ntldr** takes over.  Don't know for sure about Vista haven't played with dual booting it. But I have read it works the same.  

With any luck it may be that your boot.ini file is all that messed up. Lucky for you :) you can use Ubuntu Gutsy to edit it. Your just going to have to search around to see what it should look like. This might help.
[Booting Using NTloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=351692")

---

### Post by flytier on 2007-11-01
Trashed my bootloader the same way.  Found [Super Grub Disc]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") and gave it a try, repaired Windows bootloader quick.  I now run Gutsy on an external USB drive with Vista on internal.  When I want to boot from Gutsy I just plug in drive and go.  This [SDC]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") saved my Vista install. Thanks Taurus

---

### Post by dracule on 2007-11-02
ok, i used super grub disc, it didnt work. i said boot windows, it came up with the BCD corrupted error. i said advanced->windows->selected vista partition, it still came up with a BCD error

i should have you know that i am using BCD not boot.ini, since it is vista

then i said "fix windows boot" and it rewrote the mbr or something, but yet again it still comes up the error about BCD being corrupted when i try to boot windows.

---

### Post by louieb on 2007-11-02
> **dracule said:**
> .. that i am using BCD not boot.ini, ...
Whats BCD?:confused:
**BCD** is an [acronym]("http://en.wikipedia.org/wiki/Acronym_and_initialism") with multiple meanings, including:
 [LIST]
[*][Bad Conduct Discharge]("http://en.wikipedia.org/wiki/Military_discharge#Bad_Conduct_.28BCD.29"), a form of discharge from US military service
[*][Barrels per calendar day]("http://en.wikipedia.org/wiki/Barrels_per_calendar_day"), a unit for measuring output of [oil refineries]("http://en.wikipedia.org/wiki/Oil_refinery")
[*][Beirut Central District]("http://en.wikipedia.org/wiki/Beirut_Central_District"), a neighborhood in downtown Beirut
[*][Binary-coded decimal]("http://en.wikipedia.org/wiki/Binary-coded_decimal"), numbering
[*][Birth Control]("http://en.wikipedia.org/wiki/Birth_Control") Device, contraceptive or slang for military issued goggles
[*][Board-certified diplomat]("http://en.wikipedia.org/wiki/List_of_credentials_in_psychology"), a professional credential
[*][Bolt Circle Diameter]("http://en.wikipedia.org/wiki/Wheel_sizing#Bolt_circle") used in manufacturing drawings
[*][Boot Configuration Data]("http://en.wikipedia.org/wiki/Boot_Configuration_Data"), a computing term for the boot loader for Windows Vista and later operating systems.
[*]The [Brainchild Design]("http://en.wikipedia.org/wiki/Brainchild_Design"), website
[*][The British Columbia Dragoons]("http://en.wikipedia.org/wiki/The_British_Columbia_Dragoons"), a Canadian Forces armoured regiment based in Kelowna and Vernon, British Columbia
[*][Buoyancy control device]("http://en.wikipedia.org/wiki/Buoyancy_compensator") used in scuba diving
[*][Zero-power Bi-stable Cholesteric Display]("http://en.wikipedia.org/wiki/Liquid_crystal_display")
[*][Behind Closed Doors]("http://en.wikipedia.org/wiki/Behind_Closed_Doors"), something done or said in private.
[*]A [blue compact dwarf galaxy]("http://en.wikipedia.org/wiki/Blue_compact_dwarf_galaxy").[/LIST]    [[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/5/5f/Disambig_gray.svg/30px-Disambig_gray.svg.png[/IMG]]("http://en.wikipedia.org/wiki/Image:Disambig_gray.svg")

---

### Post by Computer Guru on 2007-11-04
> **dracule said:**
> Ok, i have no vista or xp recovery or install cd's


cant i just add a grub entry permenatly to my install?

This should do the trick:
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Taken from the EasyBCD user manual.

---

