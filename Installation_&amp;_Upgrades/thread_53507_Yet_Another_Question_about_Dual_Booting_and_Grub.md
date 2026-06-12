---
title: "Yet Another Question about Dual Booting and Grub"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by audax321 on 2005-08-01
Hello,

Okay, this is kind of complicated but here goes:

I have three hard drives:

/dev/hda (40 GB; ReiserFS, Partitions: /, /home, swap; GRUB sees this drive as hd0)
/dev/hdb (200 GB; FAT32, 1 partitions used for storage, GRUB sees this as hd2)
/dev/hde (27.3 GB; NTFS, 1 partition used for WinXP, GRUB sees this as hd1)

Now, the complicating crap here is that hde is on a controller card, not attached directly to the motherboard. Also, in order to install Windows on that drive, I had to remove the drive from the controller card and temporarily make it primary master (with linux and FAT32 drives removed).

After installing Windows, I put hde back on the controller card and currently the system is setup as shown in the list above.

I then booted off of hda as I usually do into Ubuntu and edited /boot/grub/menu.lst and added the following:

```

title		Microsoft Windows XP Professional
root		(hd1,0)
map		(hd1) (hd0)
map		(hd0) (hd1)
makeactive
chainloader	+1

``` 

This kind of works because I do get the Windows boot screen to show up, but then a few seconds later a blue screen of death shows up and the system reboots. The same thing happens in safe mode. It seems to occur in safe mode during/after loading agp440.sys. Is there a way to find out what the damn BSOD is saying??? Or does anyone else have any suggestions on how to correct this problem? It's obviously trying to boot but something is going horribly wrong.


Thanks.

---

### Post by dave9191 on 2005-08-01
Somewhere in the wonderful menu's inside windows ( i forget where exacly ) is a little tickbox that you can remove so that windows will not restart after showing the BSOD. I think you got to it somewhere from right clicking on My Computer and selecting proeties. Hope that gets you one step closer if you can get into windows by rewiring your hdd first. 

Dave

---

### Post by KiwiNZ on 2005-08-01
The first lines of the BSOD give the stop code which may look like this 
STOP 0x0000001E (0xc0000006, 0xA011C102,
or this 
0x0000001E KMODE_EXCEPTION_NOT_HANDLED

Copy down the error code and go to the Microsoft site and do a search for the stop error 
and the cause and resolutions suggestions.

Note those examples above just random examples only

cheers

---

### Post by MrCheese on 2005-08-01
> I have three hard drives:

/dev/hda (40 GB; ReiserFS, Partitions: /, /home, swap; GRUB sees this drive as hd0)
/dev/hdb (200 GB; FAT32, 1 partitions used for storage, GRUB sees this as hd2)
/dev/hde (27.3 GB; NTFS, 1 partition used for WinXP, GRUB sees this as hd1)

Now, the complicating crap here is that hde is on a controller card, not attached directly to the motherboard. Also, in order to install Windows on that drive, I had to remove the drive from the controller card and temporarily make it primary master (with linux and FAT32 drives removed).

Looks like XP doesn't actually have a boot-time driver for your raid card. Put it back on one of the mobo contoller ports & put your Ubuntu drive on either as slave to it or on the secondary port (you'll have to re-jig grub). Your XP system should then boot.

For the record, my system is :

hda 160Gb Fat32 - on ide raid card
hde 40Gb NTFS XP - primary onboard ide as master
hdf 40Gb Ubuntu - slave to XP disk

plus rather too many optical drives........

Because Linux insists on seeing the offboard ide as the primary controller it will decide that the hdd hanging off this is in fact drive 0 a.k.a. /dev/hda hence the reason for rejigging Grub. Personally I still use lilo, but that's my problem....

---

### Post by audax321 on 2005-08-01
Well, I decided to try and load drivers for the controller card in Windows only to find that I had a very very outdated BIOS on it and the drivers for it weren't supported anymore. So I tried to flash it and, of course, with my luck the flash failed and the card is now a paper weight. I don't really care that much because it was a very old ATA33 or ATA66 card anyway. I'm going to go try to find a good Promise Tech. one thats at least ATA100 and I'll post back when I find a solution. Thanks for all your help, I'm pretty sure it might be the driver issue because it boots fine when connected to the motherboard. I remember I couldn't even get this card to work when I bought it for Windows 98. Oh well, I got it free after rebates anyway... no loss, no gain.  :neutral:

---

### Post by audax321 on 2005-08-05
Okay, just got a Promise Ultra 100 TX2 card and installed it. The system still crashed on boot. So, I plugged the 27.3 GB drive with Windows directly into the motherboard and started Windows. I then installed drivers for all the undetected cards in the computer like the video card, network card, and the add-on card. After this I connected everything as I normally would:

  27.3 GB in the add-on card (hde1 - Windows)
  100 GB as Primary Slave (hdb1 - FAT32 Storage Drive)
  40 GB as Primary Master (hda1,2,3 - Linux /, swap, and /home)

  with grub having this for the windows operating system:

  title		Microsoft Windows XP Professional
  root		(hd1,0)
  map		(hd1) (hd0)
  map		(hd0) (hd1)
  makeactive
  chainloader	+1

Then, after booting and selecting Windows in grub, everything worked great. So in the end it was just Windows not having enough drivers to boot properly. All this work just to play a few games... I hate Windows so much  ](*,)

---

### Post by dave9191 on 2005-08-06
Yet another reason why Microsoft is so popular, and where linux suffers the lack of drivers problem ?!?! hehe ;)
And there is little gamers like us can do to fully cut away from MS :(

Dave

---

