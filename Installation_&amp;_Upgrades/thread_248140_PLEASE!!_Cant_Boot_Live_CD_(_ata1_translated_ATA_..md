---
title: "PLEASE!! Cant Boot Live CD ( ata1: translated ATA .. ) error"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by lynxus on 2006-08-31
Hi guys, 
Ive had Ubuntu on my work laptop and my home laptop for a while now and confident enuf that my games ect will now run ok on my home PC.

However i cant even boot the live CD to install...

It starts to boot then goes to a black screen with white text. 
This text slowly scrolls the following message.

[4294845.605000] ata1: translated ata start / err 0x51/00 to SCSI sk/asc/ascq 0x3/1
                     ( repeated a few times  )
                            ( Then )
Buffer I/O error on device dm-0, Logical block 634653

( wash and repeat :( )


After this ( 15mins or so ) it decides to carry on, It then shows me a very odd screen, Large verticle green lines and i can hear the ubuntu startup sounds in the background.

Im at loss on what the hell i need to do.

A) - fix the ata error thing
B) - fix it so i can actually see the desktop ( loading screen visible fine ) actual desktop = verticle green lines.. CANNOT MAKE OUT MENUS ETC ETC, Completely unuseable ( TFT auto sync no help )


My hardware..

2x Maxtor SATA drives. ( No IDE drives installed ) apart from dvd.
A7n8x deluxe motherboard
Nvidia GF 6600 GT
AMD 2800+ 32bit




ANY IDEAS PLEASE!!!:x

---

### Post by zxee on 2006-08-31
Have you tried to search the error messages you posted? I briefly searched > translated ata start / err 0x5/00 to SCSI and it looks like a SMART (hard drive failure detection error).

As to the unviewable screen it seems like you need to select a basic video mode from the installer start screen or use the text mode install and then configure your gpu after installation with > sudo dpkg-reconfigure xserver-xorg Is this a motherboard that has onboard video? That sometimes confuses the installer. Hope that's helpful.

---

### Post by lynxus on 2006-08-31
OK, thanks for your reply :)

Ive managed to get the video working. looks like the live cd nativly boots to an odd res for lcds..

with regards to the ata thing.
Ive disabled all smart stuff. i have looked for the error but couldnt find anything overly helpful.

If i CTRL+C during the wrror it passes by and loads ..

Soo next thing i suppose is to see if it detected teh drives.

i have a feeling its a SATA issue.. :(



Gparted doesnt seem to do anything.. Just sits there scanning for drives..

Any ideas how to get Ubuntu to work with a silicon image sata for an asus a7n8x delux board ?

Im fairly new to linux so im unsure how to inject it into the setup boot and to make sure it reconsises it after book not screwing up and exsisting partitions on the drives..

---

### Post by zxee on 2006-09-01
Take a look at the docs here [https://help.ubuntu.com/community](https://help.ubuntu.com/community) 
and here [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
There are hardware guides there too but I'm not sure how specific they are.
You can also check the hclat [www.linuxquestions.org](www.linuxquestions.org)
Hope that helps.

---

