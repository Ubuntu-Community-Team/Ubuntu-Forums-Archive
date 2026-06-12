---
title: "BIOS update, trying to install win7."
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by lillskm513 on 2010-01-03
i'm having trouble upgrading my computer (an eee pc with karmic koala on it atm) to windows7. so far, windows7 is on my 186GB external HD, which has been formatted to NTFS. i finally figured out after starting win7 setup on my mother's computer (a desktop running on xp) that what i needed to do was download an ASUS update to BIOS so BIOS will support the win7 OS. and i know i need a flash drive to do this, but i don't know exactly what to do with it. does anyone happen to know?

i'm kind of a n00b, so if you don't put it in simple terms chances are i won't understand.

---

### Post by JuseBox on 2010-01-03
> **lillskm513 said:**
> i'm having trouble upgrading my computer (an eee pc with karmic koala on it atm) to windows7. so far, windows7 is on my 186GB external HD, which has been formatted to NTFS. i finally figured out after starting win7 setup on my mother's computer (a desktop running on xp) that what i needed to do was download an ASUS update to BIOS so BIOS will support the win7 OS. and i know i need a flash drive to do this, but i don't know exactly what to do with it. does anyone happen to know?

i'm kind of a n00b, so if you don't put it in simple terms chances are i won't understand.

This is not a windows forum... If you have and linux question i can answer that!

---

### Post by kellemes on 2010-01-03
> **lillskm513 said:**
> i'm having trouble upgrading my computer (an eee pc with karmic koala on it atm) to windows7. so far, windows7 is on my 186GB external HD, which has been formatted to NTFS. i finally figured out after starting win7 setup on my mother's computer (a desktop running on xp) that what i needed to do was download an ASUS update to BIOS so BIOS will support the win7 OS. and i know i need a flash drive to do this, but i don't know exactly what to do with it. does anyone happen to know?

i'm kind of a n00b, so if you don't put it in simple terms chances are i won't understand.

Are there no instructions on the ASUS support site?
Maybe if you give us the exact model of your system we can help you better.

As far as I remember you can extract the BIOS patch to the flash-disk and then enter BIOS using <DEL> at startup (or maybe another key-combo) and then load the BIOS patch from the BIOS screen..

---

### Post by lillskm513 on 2010-01-03
> **kellemes said:**
> Are there no instructions on the ASUS support site?
Maybe if you give us the exact model of your system we can help you better.

As far as I remember you can extract the BIOS patch to the flash-disk and then enter BIOS using <DEL> at startup (or maybe another key-combo) and then load the BIOS patch from the BIOS screen..

there are instructions, but not for my version of ubuntu. ASUS seems to assume all users are on windows. i have an eee 1000HE. do i need to make the flash drive bootable before i extract the BIOS patch to it?

---

### Post by lillskm513 on 2010-01-03
> **JuseBox said:**
> This is not a windows forum... If you have and linux question i can answer that!

the linux question part is how to update BIOS with linux, since all the instructions i can find are for windows. the non-linux part is whether a BIOS update is really what i need to do, since it sounds like it can be kind of risky especially for someone with little experience.

---

### Post by cascade9 on 2010-01-03
This should help- 

> Download the new BIOS from the download section. Extract the ROM file from the downloaded .zip file.

Copy the renamed file to a FAT formatted USB drive. (***NOT*** FAT32)

Insert the USB drive into the left USB port (the Eee looks there first)

Reboot.

At the BIOS screen, press the Alt + F2 keys to enter the BIOS utility.

Follow the onscreen prompts. Do NOT interrupt the flashing process. Have the Eee on AC power, not battery.

[http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1008HA&id=20090616013029034&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1008HA&id=20090616013029034&page=1&SLanguage=en-us)

---

### Post by kellemes on 2010-01-03
> **lillskm513 said:**
> there are instructions, but not for my version of ubuntu. ASUS seems to assume all users are on windows. i have an eee 1000HE. do i need to make the flash drive bootable before i extract the BIOS patch to it?

Well, I found some links that may be helpful, it seems possible anyway..
As far as I understand you only have to put the xxx.ROM to the flashdrive and reboot the machine with the flashdrive connected, now..
```
As soon as you see the BIOS screen, hold down Alt, and hit F2.  This should load up the BIOS updater from the boot block.
```
[http://www.blakeanthonyjohnson.com/?p=170]("http://www.blakeanthonyjohnson.com/?p=170")
[http://georgia.ubuntuforums.org/showthread.php?p=7537298]("http://georgia.ubuntuforums.org/showthread.php?p=7537298")

Sorry I can't be of much help.

---

### Post by lillskm513 on 2010-01-03
> **cascade9 said:**
> This should help- 



[http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1008HA&id=20090616013029034&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1008HA&id=20090616013029034&page=1&SLanguage=en-us)

> **kellemes said:**
> Well, I found some links that may be helpful, it seems possible anyway..
As far as I understand you only have to put the xxx.ROM to the flashdrive and reboot the machine with the flashdrive connected, now..
```
As soon as you see the BIOS screen, hold down Alt, and hit F2.  This should load up the BIOS updater from the boot block.
```[http://www.blakeanthonyjohnson.com/?p=170](http://www.blakeanthonyjohnson.com/?p=170)
[http://georgia.ubuntuforums.org/showthread.php?p=7537298](http://georgia.ubuntuforums.org/showthread.php?p=7537298)

Sorry I can't be of much help.

thank you so much guys! :)

---

### Post by kellemes on 2010-01-03
> **lillskm513 said:**
> thank you so much guys! :)

Good luck.
Let us know if it worked.

---

### Post by lillskm513 on 2010-01-03
> **kellemes said:**
> Good luck.
Let us know if it worked.

it half-worked. the instructions you both gave me were accurate, and i got the E-Z flash BIOS updater to start, and then this happened:

Checking for USB device...
Reading 1000HE.ROM...
1000HE.ROM not found!

or something like that. i checked the flash drive, and it IS formatted to FAT. do i need to remove all the other files on the flash drive, or should that not make a difference?

---

### Post by cascade9 on 2010-01-03
BTW, in that link I posted there is a bit I edited out (Rename the ROM file to 1008HA.ROM). You shouldnt have to rename the .ROM, but if you do..it wont be 1008HA. It would probably be '1000HE.ROM' but dont try renaming it till yuo have tried it with the name it downloaded under. 

> **lillskm513 said:**
> thank you so much guys! :)

+1 to what lillskm513 said. ;)

---

### Post by lillskm513 on 2010-01-03
> **cascade9 said:**
> BTW, in that link I posted there is a bit I edited out (Rename the ROM file to 1008HA.ROM). You shouldnt have to rename the .ROM, but if you do..it wont be 1008HA. It would probably be '1000HE.ROM' but dont try renaming it till yuo have tried it with the name it downloaded under. 



+1 to what lillskm513 said. ;)

aha! this fixed it. BIOS is updated. THANK YOU SO MUCH for all your help, guys! now all i have to do is figure out why win 7 still won't boot :D

---

### Post by kellemes on 2010-01-04
> **lillskm513 said:**
> aha! this fixed it. BIOS is updated. THANK YOU SO MUCH for all your help, guys! now all i have to do is figure out why win 7 still won't boot :D

It's a sine..
It wants you to stick with Linux I'm sure ;-)

---

### Post by cascade9 on 2010-01-05
> **lillskm513 said:**
> aha! this fixed it. BIOS is updated. THANK YOU SO MUCH for all your help, guys! now all i have to do is figure out why win 7 still won't boot :D

If you've set your computer to boot from USB and win7 isnt booting, then there isnt much you can do. Apart from install it on the internal Hdd (which I wouldnt LOL)

---

