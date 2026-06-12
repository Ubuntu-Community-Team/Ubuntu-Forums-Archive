---
title: "Installation woe: Several Disks, AMD64, SATA HDD, Ubuntu 6.06LTS DVD"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by R0sbif on 2007-01-02
Hallo all,

I have recently made the decision to move from Windows to Linux and a friend has made a strong recommendation to use Ubuntu.  I chose 6.06 LTS DVD version.  Incidentally, I have succesfully installed this, using the same DVD on an Asus M6 laptop for my GF.  It certainly seems to do the business - and I want it on my desktop now!!

My PC consists of the following:

AMD 64 3200 
Asus K8V Deluxe motherboard
ATI Radeon 9600XT
1Gb RAM
1x SATA WD Raptor 74Gb (on VIA controller)
1x IDE WDC 240Gb 
1x IDE WDC 120Gb
2x IDE Maxtor 240 (RAID Array (500Gb for data) on Promise controller)

I currently boot from the Raptor (SATA) with Win XP. On this disk there is a Windows (NTFS) partition and a data (NTFS) partition.

All the other disks are for data and are currently NTFS partitions.  The RAID array is done from the BIOS rather than the tricky Windows method....

I have tried (over the past 5 days) to install Ubuntu using the following methods:

Remove second partition from SATA disk and install using largest free space
Expand Windows partition to maximum and get Ubuntu to resize, and install in the space created.
Delete the 120Gb WDC and use the entire disk (and change BIOS to boot from it)
Create my own partitions using the facility in Ubuntu's installer on SATA disk and on 120Gb WDC

All the methods have failed for one or more of the following reasons:

Failed at 15% - cannot create file system(yes that old cookie.  it went away after a bit so no worries about that.)

Cannot find operating system. - in this case, I need to either boot from the DVD again or use partition magic's recovery disk to activate the windows partition once again so i can use the machine.

I have noticed that each time, during the installation process (which seems to happen without hitch every time) that when it installs GRUB, it says detecting other OSs but never asks me anything, or says that it has found anything... in fact, I don't even get a GRUB prompt or anything GRUB like on boot after installation.

I cannot work out why it is that I can't successfully install this.  The frustration is incredible.  I have looked on documentation, wikis, forums (fora?) and have tried some of the things that appear to be related but obviously aren't.  

I would like to try and manually install GRUB and have seen people mention to do this from the DVD but I can't seem to be able to find it or any data on how to.  

I would dearly like to get out of this Windows nightmare that I have been in since version 2.0. Therefore, any help that you could offer me would be greatly appreciated.

Thank you very much for at least reading this rather long rant...

Happy new year by the way :-)

Rich

---

