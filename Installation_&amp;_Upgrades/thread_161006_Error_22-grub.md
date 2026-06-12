---
title: "Error 22-grub"
date: 2006-04-16
forum: Installation &amp; Upgrades
---

### Post by rsvasan72 on 2006-04-16
Hi,
I am quite new to Linux. I tried to install Ubuntu 5.10 on my system (MOBO: Intel D945GNT; Processor Intel P4 3.4 GHz) which is already running Win-XP Home. Everything went on well until it said loading GRUB after which system rebooted and now halts at saying [COLOR="Blue"]"Error 22"[/COLOR]. Any help to fix this problem would be greatly appreciated.
Thanks
rsv

---

### Post by ubernoob on 2006-04-16
Are you dualbooting? And which of them fails?

---

### Post by ubernoob on 2006-04-16
If it's your window partition: Run the Windows XP CD and go for 'recovery console' and at the prompt type
'fixmbr' you can try 'fixboot' or 'fdisk /mbr' as well.

---

### Post by rsvasan72 on 2006-04-16
[QUOTE=ubernoob]If it's your window partition: Run the Windows XP CD and go for 'recovery console' and at the prompt type
'fixmbr' you can try 'fixboot' or 'fdisk /mbr' as well.[/QUOTE]

I could not boot into either of them. When I restart the system, I get three messages 1. loading GRUB installer stage 1.5 ; 2. Please wait; 3. ERROR 22; and then stops.
Thanks
rsv

---

### Post by Kingduck on 2006-05-03
I'm getting exactly the same problem. the computer just has ubuntu installed, not windows.. so it's obviously not a problem with the windows partition... 

Btw it happened when i was attempting to uninstall the OS.. but i failed.

i just wwant to format my pc and have no OS on it

---

### Post by aujaman on 2006-05-03
[QUOTE=Kingduck]I'm getting exactly the same problem. the computer just has ubuntu installed, not windows.. so it's obviously not a problem with the windows partition... 

Btw it happened when i was attempting to uninstall the OS.. but i failed.

i just wwant to format my pc and have no OS on it[/QUOTE]

I had similar problem after installing Ubuntu Dapper 6.06.  From this forum someone suggested that I unplug my computer from the internet while installing Ubuntu using the live CD and it will take care of the problem.  Apparently it appears that the installation is getting something from the internet that makes grub not to install properly.  I did exactly what was suggested, grub installed properly and I am a happy camper since last night.  Ubuntu reigns.:)

---

### Post by Kingduck on 2006-05-04
i found a way to fix this (on my computer at least) 

When you boot your computer, you have to press one of the F keys... i think F1 but whatever button it is to get onto the BIOS menu (Must do this on the first loading screen, before it gives you the grub error 22 msg). Go to the boot tab (not sure the name of it) and it has a priority list of places to boot from out of 3. Mine was set to 1. Floppy, 2. Hard drive, 3. CD/DVD drive... what you need to do is put CD in front of hard drive so it boots from your installation CD before loading up the broken operating system on your hard drive.

I am now reinstalling ubuntu as normal.. (remember to set it to boot to hard drive in front of cd again otherwise it will go to your installation disk every time you boot, if a cd is in the drive)

hope this can help anyone :)

---

### Post by Sef on 2006-05-05
For getting into the BIOS the usual keys are F2, esc, or delete.  There can be others, but those are the normal ones.

---

### Post by rakan_dr on 2008-07-13
It's a memory problem.
Try to make a memtest, if there are errors, then you have to replace ur memory.
I faced this problem and i read this in a book.
Cuz try to enter the rescue mode in Ubuntu, then u will have a problem called "Kernel panic", which is about bad hardware.

---

### Post by rsvasan72 on 2008-07-13
Thanks Much Rakan

> **rakan_dr said:**
> It's a memory problem.
Try to make a memtest, if there are errors, then you have to replace ur memory.
I faced this problem and i read this in a book.
Cuz try to enter the rescue mode in Ubuntu, then u will have a problem called "Kernel panic", which is about bad hardware.

---

