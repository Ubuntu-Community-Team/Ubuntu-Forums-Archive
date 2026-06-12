---
title: "Unable to boot from CD"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by danjwray on 2007-04-25
I just bought an old RM box with Pentium III and 128 RAM to use as a music player, but can't get ubuntu on to it.

Whenever I boot it i get the error - 

"ISOLINUX 3.11 Debian-2007-03-12 isoLinux:
Cannot boot from this CD. Please use CD2 or try a BIOS update."

I have tried this with Edgy, Feisty and the alternate Feisty .iso, all of which give a similar message.

Is there anything I'm not thinking of which will get around this, or is a BIOS update my only option?  Having never updated a BIOS a few pointers on that would be handy too.  There isn't a CD2, is there?

My BIOS is Award Modular BIOS v4.60PGMA AX6BC R2.20, if that helps at all... 

Thanks guys, danjwray

---

### Post by mac.ryan on 2007-04-25
That error - I believe - it is due to the incapability of your bios to boot from a multiple isolinux image. The "CD2" is (in Debian) an alternate CD that comes with a different imaging scheme.

I can see two options here:
[LIST=1]
[*]upgrading your bios.
[*]using an alternate install method.[/LIST]Upgrading the bios should be quite easy: normally you have to make a bootable floppy, and use a utility to flash (i.e. write on your bios flash-ROM) the new bios image. Vendors sites have clear how-to's and files to download.

Using an alternate install method can be tricky but a good learning experience. See this page for a list of documented alternatives: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

PS: I don't know if there is an equivalent of "CD2" under ubuntu, but given the fact you tried pretty much everything out there... :-/

---

### Post by mac.ryan on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/62950](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/62950) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				Just needed to add the pointer to the bug in launchpad (to date it is impossible to add via editing an old message...)

---

### Post by tormentum on 2007-04-25
Do you have any further information about the PC? Mainboard make/model, hard disks, cd rom make/model?

---

### Post by danjwray on 2007-04-26
The cd is cd-rw CRX100E (sony)
the hard drive is Fujitsu mpd3108AT, 10 gigs.

i tried the alternate install using a bootable floppy with smart boot manager, but keep getting an(other) error when i try to boot from cd-

Disk error! 0xAA

from searching a bit it seems that this is quite common, but no fixes seem to be around.  I have tried this with Ubuntu feisty and edgy, knoppix, win 98se, mandriva 2006, vista and xp (everything i have around here!) but always get the same error, even after waiting as other suggest.  It seems like my disk drive just doesnt want to play with smart boot manager, it doesnt even spin the disks when i hit cdrom drive.

so next up, i'll try a bios firmware update. i'll let you know how I get on. 

Please let me know if you have any ideas about smart boot manager, as that seems like a nice way to do it.

thanks for your help.

---

### Post by richer.pierre on 2007-06-01
I get similar errors with my CDs.
Error 0x0C if a CD disk is in the reader
Error 0xAA if no CD disk in the reader

I would also be interested in a solution!

---

### Post by confused57 on 2007-06-01
> **richer.pierre said:**
> I get similar errors with my CDs.
Error 0x0C if a CD disk is in the reader
Error 0xAA if no CD disk in the reader

I would also be interested in a solution!

When I use Smart Boot Manager, after scrolling down to "cd rom", press "enter", I get the "Disk error! 0xAA", I then press "enter" a couple of more times and the cd drive boots...may not be your problem, but it's what works for me.

---

### Post by richer.pierre on 2007-06-02
Thanks for answering. I tried your suggestion. I can now hear the CD spinning and the read light flashes but it still won't boot.

The file I am trying to boot is "ubuntu-7.04-desktop-i386.iso". I have one CD with this integral file copied onto and another one with a copy of all the extracted file.

Which one does smart boot expect? The original file appears as a "rar" archive.

---

### Post by confused57 on 2007-06-02
> **richer.pierre said:**
> Thanks for answering. I tried your suggestion. I can now hear the CD spinning and the read light flashes but it still won't boot.

The file I am trying to boot is "ubuntu-7.04-desktop-i386.iso". I have one CD with this integral file copied onto and another one with a copy of all the extracted file.

Which one does smart boot expect? The original file appears as a "rar" archive.

You have to burn the iso as an "image", not as a data  or bootable cd, do not extract the files:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Sounds like you were able to get SBM working, but I believe you burned the iso incorrectly...check your cd writing software, there should be an option to burn the iso as an image, burn it at a low speed(8x or less).

To be absolutely sure the iso downloaded uncorrupted, you'll need to run a md5sum check on the iso...I've downloaded countless distro iso's and the md5sum has always checked out, the next one I do probably won't.

Added:  The iso appears to be a rar file, because that's the program Windows associates with .iso...it's actually an iso and shouldn't be extracted prior to burning to cd.

---

### Post by richer.pierre on 2007-06-05
You're a genious!

I must have missed something when I downloaded the file but I didn't know it required special burning...!!!

I downloaded Free ImgBurn and now I don't even need Smart Boot, the CD boots on its own!

Thank you very much, I think I'm in business now. I have to leave for a few days but then I will install Ubuntu.

I have a partition that already runs Debian Linux. My intention was to use that partition. Will the Ubuntu Install overwrite that partition or should I do it before?

---

### Post by merlinus on 2007-06-05
You can select that partition whilst installing, and Ubuntu will reformat it.

A suggestion, however.  You may wish to turn that partition into three, /, /home and swap.  It will make future upgrades easier as your application settings in /home will not be overwritten.

Good luck!

-merlin

---

