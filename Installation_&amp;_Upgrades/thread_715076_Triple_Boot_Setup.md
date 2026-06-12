---
title: "Triple Boot Setup"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by pixelhog on 2008-03-04
Hi guys,
I was planning on creating an triple boot setup (xp, vista, ubuntu[7.04 feisty]) but I have come across a problem with the GRUB bootloader...
So far, I have XP and Vista installed, dualbooting nicely, and using the Vista bootloader.
I'm anxious to install ubuntu and get a triple boot setup going, however I would like to KEEP the Vista bootloader to choose between the 3 OSes...
I understand that when Ubuntu installs, GRUB gets written to the MBR... so my question to you guys is:
Is there any way to install the GRUB bootloader on the _partition_ and **NOT** the MBR so that I can retain the Vista bootloader?

I greatly appreciate any help!

---

### Post by froy02 on 2008-03-04
Yes, use the alternate desktop Cd installation rather than the live Cd version.  When it gets to section of asking you to install grub say no to the default choice then select the partition where you want grub installed.

---

### Post by pixelhog on 2008-03-05
thanks a bunch!

---

### Post by Shazaam on 2008-03-05
You can also use the desktop cd to specify where to put grub. If I remember right, during installation when you get the notice (or just before)  that Ubuntu is going to install and that it is going to partition/format your drive  there is an "Advanced" button that you can click to specify where to put grub.

---

### Post by pixelhog on 2008-03-08
I think you're right about the Advanced button....just never clicked it.
Thanks for pointing that out

---

### Post by daarkstaar on 2008-03-21
I have decided to do a triple boot as well.  As per the suggestion I put GRUB on the same partition as Ubuntu 8.04beta.  When I boot, the Vista boot screen comes up, but without Ubuntu on the boot list.  I'm guessing I have to alter the MBR to add Ubuntu, right?  Any tips on how to do this?

---

### Post by pixelhog on 2008-04-07
i'd say you're better off just dual booting xp and ubuntu.  i haven't had any success with the tri-boot setup. 
The closest i've come is having the vista bootloader pop up but when you select 'other os', the grub bootloader pops up.
having two bootloaders is just a pain in the *** so i just got rid of vista, and decided to dual boot xp and ubuntu 7.10....
what good is vista anyway? lol

---

