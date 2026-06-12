---
title: "Upgrade Manager getting New Release files from CD instead of Internet"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by petersfreeman on 2012-05-23
I want to upgrade from 11.10 to 12.04 using the Upgrade Manager because my PC is defective and although it can read from a CD, DVD and USB stick, it cannot boot from a CD, DVD or from a USB stick.  The other problem is that my Internet Connection is expensive and I want to use the LiveCD as the source of files instead of getting them from the Internet as it would cost a lot of money to upgrade.  

When I put the LiveCD in the drive, the Update Manager recognized it as a source and I selected it.  It now shows up and is checked in the Update Manager in Settings/Other Software as **cdrom:[Ubuntu 12.04 LTS_Precise Pangolin_-Release amd64 (20120425)]/ precise main restricted**

Is there a way to direct the new release upgrade to this CD instead of the Internet?

Thanks

Peter

---

### Post by jmore9 on 2012-05-23
Check out the alternate install cd.  It might be able to upgrade what you have .

---

### Post by jadtech on 2012-05-23
i think the term upgrade from live CD gets a bit confused it is possible if you have a separate home partition  to reuse it  just formatting  the root directory reuse home and swap .. 


how ever programs are not saved in the home  partition only personal files, documents , pictures , music  personal configuration and such so all  your added programs will need to be re installed ..

---

### Post by petersfreeman on 2012-05-23
Hi jmore9,

I have the alternate 12.04 disk, how do I tell the update manager to us it as a source instead of the Internet (I can't boot from it due to the defect with my BIOS/System)

Thanks,

Peter

---

### Post by jmore9 on 2012-05-23
Synaptic should have an option to allow the user to add volumns.  I just put the cd/dvd in and then start synaptic and add the vol. and it reads it and shows the packages that are avaiable from the cd/dvd.  I always use this way when upgrading without internet.

You just select mark all upgrades. then apply.

This may work without internet if you have a complete install already.  But always back up all your data .  Again always do a back of data you wish to keep.  Very important that is done.  Things do have a chance to go wrong sometines even for the experts out there.

---

### Post by petersfreeman on 2012-06-13
> **jmore9 said:**
> Synaptic should have an option to allow the user to add volumns.  I just put the cd/dvd in and then start synaptic and add the vol. and it reads it and shows the packages that are avaiable from the cd/dvd.  I always use this way when upgrading without internet.

You just select mark all upgrades. then apply.

This may work without internet if you have a complete install already.  But always back up all your data .  Again always do a back of data you wish to keep.  Very important that is done.  Things do have a chance to go wrong sometines even for the experts out there.

Hi jmore9,

I was successful in using the Alternative CD, and the installation completed, however on restarting after installation of 12.04, my machine freezes.  It appears that the BIOS is conflicting with the way 12.04 boots.  I can boot the regular LiveCD and install all versions up to and including 11.10 sucessfully, however the regular LiveCD for 12.04 will not even get to the Try Ubuntu/Install Ubuntu screen, and after installing using the Alternative CD, it completes the install but freezes after the first restart. 

It is like the Ubuntu Team has changed the boot software and it now conflicts with my BIOS.  I have had no problems installing 12.04 on various family member machines.

Cheers,

Peter

---

### Post by petersfreeman on 2013-04-28
The last Ubuntu release that I was able to install on my Gateway (a rebranded Acer) was 11.10.  I was unable to install 12.04 nor was I able to install 12.10.  However when 13.04 was released a few days ago, it installed fine.  I believe it was someting to do with 13.04's better support of EFI and UEFI (Unified Extensible Firmware Interface).  My tower has an EFI system and I think that was the reason I was having problems.  I now consider this problem solved.  Boy, it is sure nice to be able to use the latest Ubuntu again.

Peter

---

