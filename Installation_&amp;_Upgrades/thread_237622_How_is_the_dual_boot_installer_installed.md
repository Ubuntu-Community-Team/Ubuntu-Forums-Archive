---
title: "How is the dual boot installer installed?"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by infocom on 2006-08-16
HI

I have two drives, Windows XP on one already, and I have (I think) just installed Ubuntu on the other. 

No boot loaded was loaded, and I boot into Windows XP everytime.

I followed the instruction here: [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) but it did not work. I still boott into Windows. I have also changed the boot sequence from the XP disk to the one where Ubuntu is, followed the above process again and it still boots into Windows.

Any ideas how to get a boot loader and offer choice of OS?

Thanks

Laurie

---

### Post by punkinside on 2006-08-16
Installation, even on different disks, should put grub as bootloader on your hard drive, if not, search for "broken grub" or something like that for threads on fixing grub. As you have just installed ubuntu, it would not hurt to run through the installation again and make sure you answer all the questions correctly.

---

### Post by infocom on 2006-08-16
OK. Thanks for speedy response. Perhaps I did make an error. During install it gave me a horrible warning about erasing all data on other drives unselected even if I did not ask to reformat. When I started install it started checking all the other disks and stating installing , for other drives. It said there was an error on a FAT16 disk. So I panicked thinking why is it doing this, I dont want to mess with any other drive/partition! So I closed the install window (the cross on top rihgt). I thouhgt I cancelled about but 20 mins later it said "Install successful" or something. SO I assumed it did install. PErhaps it didn;t after all??

So can you confirm one thing to me... will installing Ubuntu erase any other data?? I chose / and swap patitions which are available, and set it to reformat, but left all other partitions as is. i.e. did not delete them from the menu or select it to format. So I am just asking because of the install message for each partition.

Thanks

Laurie

---

### Post by Tomosaur on 2006-08-16
Ubuntu will only install wherever you tell it to, the 'This will wipe all data' message is just a generic warning which shows up regardless of what you're doing. If you tell it to install to somewhere you KNOW is safe, that's where it will install to, but you'll still get the message even if the drive is empty.

---

### Post by infocom on 2006-08-16
Well I enter / for the root and "swap" for the swap. I choose the drives from the list (i.e. Partition 2 disc IDE/ATA 2 (Primary) hdb2) but also in this big list are all the other partitions where Windows and my documents are (i.e. media/hdb1). I do not change these (or remove them) and I do not select to format. So does this mean they will stay as they are??? When installing it says something about installing for these other drives. I dont want anything to happen to the other drives in the list, only / and swap. Hope you know what I mean.

---

### Post by infocom on 2006-08-16
I went for it and re-installed Ubuntu, not interupting anything .It has installed OK. I restarted but it went straight into Windows again.

So back to my original quation I suppose... how can I install a boot loader like Grub?

Thanks

Laurie

---

### Post by infocom on 2006-08-16
I went back into BIOS and to check boot order and I notice that the drive where Ubuntu is, IDE Hard Drive, it has after it the statement " (not present)". So the IDE drive is present as I can access files on both drives. Does anyone know anything about this.?

So to reiterate, XP is on  drive, a SATA drive, and Ubuntu is on the IDE. The IDe is set to boot first but states (not present) after it in BIOS. 

Do you think it may be because I put Ubuntu at the end of the drive, with no Boot partition?

Laurie

---

### Post by infocom on 2006-08-16
Ok I sorted it out.

It was something to do with the (not present) message in BIOS. I had some options to turn drives on or off. I had the following setup:

SATA-0: On
SATA-1: Off
PATA-0: On
PATA-1: Off

I turned PATA-1 On and saved/exited and went back into BIOS. The (not present) was removed and next to PATA-1 it stated the drives capacity etc. So I dont know much about all this but now I got grub with choice of booting.

Laurie

---

