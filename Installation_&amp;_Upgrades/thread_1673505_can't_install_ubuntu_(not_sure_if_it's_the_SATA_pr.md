---
title: "can't install ubuntu (not sure if it's the SATA problem?)"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by kodrann on 2011-01-22
the situation:
i had ubuntu installed on my PC up until few days ago and everything worked perfectly. and then my HDD died (it was old Maxtor IDE). i bought new Seagate SATA. connected everything and proceeded with ubuntu installation (fresh 10.10 cd). the computer detects the installation cd and then the screen goes blank with only a line blinking in the top left corner of the screen. i also installed windows xp and tried from there. files from ubuntu cd copy just fine but when i restart to complete the installation the same thing happens. so i downloaded ubuntu 8 and burned it on cd. this time i was able to get a menu on the startup but after i choose anything it freezes again. so i don't know wher the problem is... the cd's were burned with 2 different recorders, they work fine up until the installation is about to begin. only hardware change is the new sata HDD. this is a problem for me since i don't want to use windows in everyday activities... thank you for your help in advance ;)

---

### Post by wilee-nilee on 2011-01-22
That is a very confusing post.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by lisati on 2011-01-22
It might be easier for us to understand your request if you use a separate paragraph for each of the things you tried.

A number of things can cause a freeze with only a blinking cursor showing. One common problem I've seen that causes this is an issue with graphics drivers.

---

### Post by dabl on 2011-01-22
In your BIOS, try setting the SATA mode to "Legacy IDE" or "Compatibility" or whatever the non-AHCI option is.

After you finish installation and verify that it's working correctly, you should be able to reset the mode back to AHCI and run correctly.

---

### Post by kodrann on 2011-01-22
- have previously installed ubuntu and everything worked fine
- changed HDD from IDE to SATA one
- tried to install ubuntu from cd and from usb but both failed at the very beggining (menu with install ubuntu, check disc etc. options)
- i can't get any info with the script since i'm not able to boot into ubuntu
- have tried to change sata type from native IDE to other types, still nothing...
- the reason i suggested SATA at first place is because before HDD change everything worked like it should

---

### Post by dabl on 2011-01-22
If you know it, please give the brand and model of the motherboard, and the model of the new Seagate hdd.  Is the SATA connector on the motherboard, or is there a separate SATA controller installed?  When you go into BIOS, does it show the new hdd?

Also, does that hdd have a jumper block on it -- are there any jumpers set?

---

### Post by kodrann on 2011-01-22
in the meantime i actually found the solution on this exact (sub)forum :)

**At the CD boot menu, press F6 and chose the option that turns off ACPI.**

Problem solved. thank you people for your help! ;)

---

