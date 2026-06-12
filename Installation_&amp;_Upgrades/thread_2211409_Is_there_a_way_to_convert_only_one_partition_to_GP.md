---
title: "Is there a way to convert only one partition to GPT?"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by javier14 on 2014-03-15
Hi there ppl!!
I've been researching about this the whole day and i couldn't find a proper answer to my problem... no1 seems to be in the same situation neither...
The thing is, i have a 1tb hard drive, partitioned in 3:

-partition 0 with windows 7 installed (78gb)
-partition 1 with my movies, tv series, music, etc. (around 800gb ntfs)
-partition 3 linux installed 40gb

what i want to do, is install windows 8.1 in the partition 0, and when i try to install there it says it can't in a MBR partition, 

and so i've read that the only way to change to GPT is by deleting the whole disc... but i have like 700gb of stuff in my 2nd partition that i don't want to lose, and i don't have an external hard drive to back them up :/

i've seen some ppl saying that it is possible to do this without having to wipe out the entire disk...

Anyone knows if this is true?

Does anyone have a tutorial or something on how to achieve this using Gparted?

or maybe another kind of workaround to have dual boot W8.1/Linux without having to lose everything?

Thanks and regards!

---

### Post by Mark Phelps on 2014-03-16
As far as I know -- NO.  The entire disk has to be either MBR or GPT.

---

### Post by javier14 on 2014-03-16
> **Mark Phelps said:**
> As far as I know -- NO.  The entire disk has to be either MBR or GPT.

Thank you for your answer :)

Yes i was afraid that was going to be the deal haha...

Do you know if it is possible to install windows 8.1 or just 8 using a MBR partition? 

Maybe formating the pendrive in some special way?

Thanks!

---

### Post by Mark Phelps on 2014-03-16
> Do you know if it is possible to install windows 8.1 or just 8 using a MBR partition? 

Yes -- it is possible.  I have a desktop with MBR-formatted drives and am able to install and run Win 8.1 without problems.

Realize, though, that if you install Win8.1 to the same physical drive that now has Ubuntu, Windows will overwrite the MBR on that drive, and after that, you will only be able to boot into Win8.1.

To get dual-boot working, you will need to reinstall GRUB on the drive -- which you can do from the Ubuntu install media.

Also, if you plan to access the Win8.1 partition from inside Ubuntu, you will first need to disable Fast Startup in Win8.1, as that uses a new form of hibernation which keeps the partitions mounted even when Win8.1 is not running.

---

### Post by javier14 on 2014-03-16
> **Mark Phelps said:**
> Yes -- it is possible.  I have a desktop with MBR-formatted drives and am able to install and run Win 8.1 without problems.

Realize, though, that if you install Win8.1 to the same physical drive that now has Ubuntu, Windows will overwrite the MBR on that drive, and after that, you will only be able to boot into Win8.1.

To get dual-boot working, you will need to reinstall GRUB on the drive -- which you can do from the Ubuntu install media.

Also, if you plan to access the Win8.1 partition from inside Ubuntu, you will first need to disable Fast Startup in Win8.1, as that uses a new form of hibernation which keeps the partitions mounted even when Win8.1 is not running.

Thanks again for all you help!

Can you recommend a tool to create an USB bootable image for windows 8.1 from linux? 

I've tried with Unetbootin and WinUSB but neither of those work :/ 
The first one doesn't support ntfs and the 2nd one prompts an error at the end of the process, i think it's related to not being launched as root, but i tried through console using sudo and i got the same error.

Regards

---

### Post by oldfred on 2014-03-17
Do not know what may work from Linux to create a Windows installer.

But how you boot install media is how it installs. So if you boot in UEFI mode, it will install in UEFI mode which for Windows requires gpt partitioning. If you boot in BIOS mode it requires MBR partitioning. And Windows does not correctly convert partitioning in many cases.

You may be able to convert from MBR to gpt, but good backups are required. And existing Ubuntu install would require reconfiguration.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

Windows does require specific partitions if UEFI. 
With BIOS/MBR it needs at least one primary partition with the boot flag. Normal installs use 2 partitions, one 100MB boot and main install.

      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

 Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

