---
title: "Install Ubuntu on an ext3 partition"
date: 2005-07-03
forum: Installation &amp; Upgrades
---

### Post by champion on 2005-07-03
[font=Century Gothic]First, my hardware specs:[/font]
[font=Century Gothic][/font] 
[font=Century Gothic]KT-7A mobo, AMD Tbird 1 GHz CPU, GeForce4 Vidcard, Maxtor 32049H3 20GB hard drive (hda), Western Digital 600BB 60 GB hard drive (hdb).[/font]
[font=Century Gothic][/font] 
[font=Century Gothic]I had Hoary 5.04 installed & running ok at one time on this rig. I had a helluva time getting it to install. Originally I had a 10GB hdb that I had to unhook to get Ubuntu to install correctly. I later swapped in the 60GB hdb, and partitioned (ext3) it into one big drive (/public) to use for backing up stuff on my little 3 box LAN.[/font]
[font=Century Gothic][/font] 
[font=Century Gothic]Went away for a week, came home, started up the box again, and hda was hosed. After a bunch of futzing around, I finally got Ubuntu installed again, but after running a few hours, it told me hda was mounted read-only due to errors, and now there are other errors & it won't boot.[/font]
[font=Century Gothic][/font] 
[font=Century Gothic]I ran Memtest86 for over 24 hours, no problems found.[/font]
[font=Century Gothic][/font] 
[font=Century Gothic]I have run all of the tests on Maxtor's PowerMax diagnostic software, no problems found. Maxtor claims that if it passes all the tests, the drive is certified error-free.[/font]
[font=Century Gothic][/font] 
[font=Century Gothic]After all that, I used PowerMax to "low-level" format the drive. This actually writes zeros everywhere on the drive rather than what low-level formatting did in the old days.[/font]
[font=Century Gothic][/font] 
[font=Century Gothic]Reinstalled, same problems. ](*,) [/font]
[font=Century Gothic][/font] 
[font=Century Gothic]All that said, I still think the drive is going bad. What else would cause spurious errors that would make the drive remount read-only?[/font]
[font=Century Gothic][/font] 
[font=Century Gothic]After all that, my question is can I install Ubuntu on the 60GB drive without losing any of the data on it? TIA. [/font]

---

### Post by codejunkie on 2005-07-03
it could possibly be the jumper settings on the drive and drive settings in the bios. 
on my motherboard it's kinda picky about how certian drives are configured and i have experienced problems like you described for example:
----------------------------------------------------------------------------------------------------------------------------------------
First Scenario: i have one drive over 100gb set as master hda jumper on hard drive.
and one drive 40gb or larger set as slave hdb jumper on hard drive, on the same ide cable and bios configuration is set to automatic configuration i will randomly loose the drive setup as slave hdb which can really freak out a dual boot system.
---------------------------------------------------------------------------------------------------------------------------------------- 
Second Scenario: if i change it up like hda master and dvd drive slave on the same ide cable, and hdb master dvd+rw drive slave on another ide cable and the bios set to automatic configuration no problems.
---------------------------------------------------------------------------------------------------------------------------------------
Third Scenario: if i have one drive aroud 40gb set as master hda jumper on hard drive. and one drive 40gb or smaller set as slave hdb jumper on hard drive, on the same ide cable and bios configuration is set to automatic configuration i have no problems at all.
---------------------------------------------------------------------------------------------------------------------------------------
also on the first scenario if disable automatic configuration in the bios and keep the jumper settings the same and specify the drives size in the bios, or if i change both drives to cable select and have auto configure enabled in the bios everything works. 
         in my case this only seems to only happen when a large drive is on the same ide cable as an smaller or equal size drive with auto config enable i don't know if this will help you at all but it's something to look at maybe swapping jumpers or bios configs around might work.

---

### Post by champion on 2005-07-03
I read elsewhere that acpi can cause problems, especially with VIA hardware. So I'm trying to install with acpi=off. We'll see what happens.
 
I also may try to put the slave 60GB drive as the master on the secondary controller & move the CD-ROM to the primary slave.

---

### Post by WildTangent on 2005-07-03
call me a traditionalist, but i prefer to keep my CD drives on one IDE cable, and my hard drives on another. i seem to have nothing but problems otherwise. anyway, the only advice i can offer is just to try another drive, because it sounds like yours is toast. and no, you cant install ubuntu on the 60GB without erasing it, as far as i know. youll have to retrieve whatevers on it by mounting it on another computer running linux

-Wild

---

### Post by codejunkie on 2005-07-03
if you already had ubuntu installed you dont have to reinstall at the grub menu hit e and enter linux acpi=off if this works just add acpi=off to /boot/grub/menu.lst also i think maybe sudo update-grub will work to.

---

### Post by codejunkie on 2005-07-03
[QUOTE=WildTangent]call me a traditionalist, but i prefer to keep my CD drives on one IDE cable, and my hard drives on another. i seem to have nothing but problems otherwise. anyway, the only advice i can offer is just to try another drive, because it sounds like yours is toast. and no, you cant install ubuntu on the 60GB without erasing it, as far as i know. youll have to retrieve whatevers on it by mounting it on another computer running linux

-Wild[/QUOTE]
you can install ubuntu on a drive without erasing it by using partition magic or an open source equivilent to resize the drive and install using the largest freespace option on the ubuntu installer but backing up before doing isn't a bad idea because stuff can always go wrong no matter what you do.

---

