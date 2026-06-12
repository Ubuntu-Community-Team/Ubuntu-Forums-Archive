---
title: "oh my I stuffed it! hear me weep into my ubuntu"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Fenris_rising on 2008-04-30
hi all.
well after 3 days getting used to HH 8.04. i decided to do a proper install. i had installed within windows initially. i shouldnt have done it, the dreaded intramfs reared its ugly head and wouldnt bugger orf! so onto the alternate install disk id made just incase. turned out to be kubuntu....nothing against it but Ubuntu had some rather natty features that kubuntu didnt. from there on it went pear shaped and i must stress this is MY fault. i messed up trying to uninstall it and trashed my XP install. then  my floppy disk i need to install the raid drivers for the sata drive failed although im not sure if something went wrong with the floppy drive controller (i had an error message about it) its taken me an hour to get to the point where the drive is now formatting ready for the XP install. Still i will be installing HH straight away. something thats bothered me about this sata lark is floppy disks are gradually disappearing. but you need one to install the raid drivers for a sata drive. Is this the norm or do more modern boards handle sata drives directly? Also when i get to the point of just installing ubuntu as my one and only OS i obviously will need to install the raid drivers for it. The ones provided on the motherboard disk are all for flavours of M$ windows, are there specific raid drivers for Linux and if so where are they? luckily i have a laptop so im of to down load the UBUNTU HH Alternate iso again. its been a long day. Has anyone come up with a definitive answer to the initramfs yet? is it just a bug that needs ironing out to do a straight to HDD install? of coarse philsophically i guess this is making me learn lolollol. mind, hard lessons are the best lessons. wish me luck guys.

Regards

Fenris

---

### Post by dstew on 2008-04-30
The initramfs message usually means that the installation disk kernel is having trouble running the hardware. Sometimes this can be fixed using kernel parameters, but going to the Alternate Install CD is a good idea.

As far as the SATA drivers, from what I understand Ubuntu has full support for this. I do not think you will need to look for or install any drivers. To set up a RAID, if it is the "fakeraid" type of BIOS-supported software-assisted RAID, Ubuntu can manage that with the **dmraid** program. If you want to install Ubuntu onto a RAID, that might be difficult. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). The Alternate Install CD can install to a pure software RAID, but to boot it you would need a separate un-RAIDed /boot partition, or a /boot partition on a software RAID-1 (mirrored). Grub cannot boot a software RAID-5 or RAID-0. Grub can boot mirrored fake-RAIDs, though (see the HowTo).

---

### Post by Fenris_rising on 2008-04-30
cheers, food for thought indeed. i will wander over and read to how to.

ok read that........gawd thats a big job lolol. something for a long winters night i think.

im just burning my new CORRECT copy of ubuntu 8.04, when i checked my previous DL i had indeed DL'd the xubunto by mistake. good to go in 10 mins i think. ive done a MinImal install of XP, just all the drivers and oddments. i'll update it tomorrow online and install my specific XP progs. for now i just want to get my Hardy Heron back. i hope i get it right this time. if not i'll at least ask how to roll back and try again if needs be.

regards

Fenris

---

### Post by Fenris_rising on 2008-04-30
ok im stuck. i have booted successfully adding pci=nomsi. however it errors when i try to partition. this is how it looks;
SCSI1 (0,0,0) (sda) - 80.0GB ATA ST380811AS
     #1 primary 80.0GB ntfs
        pri/log  8.2MB FREE SPACE
what do i do here? im a bit wary as this is where it can all cock up. i really dont want to go back and reinstall XP just so i can partition at that point.

oh well looks like ive killed it again cant boot XP and the disk wont continue after boot either. ho hum, any useful advice at this point?

oh whoops i told it to use all the disk. if it works i will let you know, of course this means i have lost XP, hope the SATA drivers are intact.


regards
Fenris

---

### Post by Fenris_rising on 2008-04-30
alls well it works no problem. no XP but i can access the backup drive and i can get the important docs over to my laptop, when i figure out how to do a network, or use the CD burner software. night all. happy but knackered.

regards

Fenris

---

