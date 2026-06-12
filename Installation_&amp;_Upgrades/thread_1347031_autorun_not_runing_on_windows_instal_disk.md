---
title: "autorun not runing on windows instal disk"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by aredhel on 2009-12-05
hello all im new, asking for some help on an issue with my laptop.
about 10 months ago i downloaded Linux Ubuntu 8.10 then upgraded to 9.04. loved the OS. now im trying to use a factory recovery disk to restore vista to my vista native cpu. seeing as im preparing this cpu for my cousin to play on. now when using any install disk it either tells me there is not enough temp memory or wont boot to disk at all any help?

---

### Post by phillw on 2009-12-05
> **aredhel said:**
> hello all im new, asking for some help on an issue with my laptop.
about 10 months ago i downloaded Linux Ubuntu 8.10 then upgraded to 9.04. loved the OS. now im trying to use a factory recovery disk to restore vista to my vista native cpu. seeing as im preparing this cpu for my cousin to play on. now when using any install disk it either tells me there is not enough temp memory or wont boot to disk at all any help?

Hi,

If you use a factory restore disk you will DESTROY your ubuntu installation.

Assuming this is what you want to do, then you need to alter your BIOS (Press esc, F2, F12 etc) when it is booting and says "press xxx For BIOS" - And change your boot order to put the CD as the FIRST boot device., then re-boot your computer with the recovery disk in the cd drive.

If, however, you want to put on Windows ALONGSIDE your Ubuntu installation, that is not too hard & you have the advantage of both operating sysytems.

Please post back if you want help on having both on your machine.

Regards,

Phill.

---

### Post by aredhel on 2009-12-05
yes any info would help seeing as i cant do anything with a different OS.

---

### Post by phillw on 2009-12-05
> **aredhel said:**
> yes any info would help seeing as i cant do anything with a different OS.

Hi.

Can you post the version of Win you were using (XP, etc), The size of the hard drive on your computer and if you have access to an external (e.g. USB) hard-drive.

The make & model of your computer would also be of help

Thanks,

Phill.

---

### Post by aredhel on 2009-12-05
VGN-NR498E SONY VAIO
 3G memory 300g hardrive
originally when i bought it it was running Windows Vista home premium OEMAct and yes access to an external hardrive

---

### Post by phillw on 2009-12-05
> **aredhel said:**
> VGN-NR498E SONY VAIO
 3G memory 300g hardrive
originally when i bought it it was running Windows Vista home premium OEMAct and yes access to an external hardrive


Sorry, 

I got diverted. You have plenty of room for a dual boot system - and, with access to an external drive, you can pop your Ubuntu area on there while you get Win back on, then pop Ubuntu back on, along side it (or keep it for another computer)

can you post the output of 
```
 sudo fdisk -l
```and 
```
df -ah | grep dev
```I'm off to bed (It's gone 2am here in the UK) - I'll have a look after some sleep (about 10 hours from now) & give you the instructions to backup your ubuntu area. Reset your computer so the Recovery disk will work & how to put back on your Ubuntu area along side it.

/edit -- If you get bored - you can go have a look at what you'll be doing for your backup, it's still in very rough form, but it is over here --> [http://www.vpolink.com/showthread.php?p=170](http://www.vpolink.com/showthread.php?p=170)
Dont worry, I'll go through the writing of the script - I'd be interested to know how you get on with writing your own

Regards,

Phill.

---

### Post by aredhel on 2009-12-06
hey man ty so much for helping out i really am grateful

---

### Post by phillw on 2009-12-06
Hi, did you figure out your own backup script, or would you like me to write it for you - if so - please post the results of the 2 commands in my earlier posting.


/edit a great howto for the dual booting is over here --> [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
You will possibly then have to head here to get the dual booting working correctly -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Regards,

Phill.

---

