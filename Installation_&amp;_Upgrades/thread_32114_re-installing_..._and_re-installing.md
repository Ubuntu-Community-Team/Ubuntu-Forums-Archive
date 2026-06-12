---
title: "re-installing ... and re-installing"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by oprogue on 2005-05-06
wow ... this is about the 5th attempt to get this distro installed as a second OS (with XP).  I've read lots of articles that say this is an easy install ... must be as a stand alone.  I have no issues in creating partitions and formating them ... no in creating a directory structure.  My SuSe dual boot works flawlessly and the first time.  Ubuntu however seems to have some sort of bootloader issue.  I've attempted to install it into it's own directory (nice small 200mb bootable compartment) without success (infact I've had to re-install Windows each time as well as it trashes the main bootloader).  Frustration has finally set in, I was due home ... ummm ... 8 hours ago and it's 04:30 am.  I've read: [http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo)
and with the exception of mimicing the order of the directories, I have the same basic partition structure.  Is it just me?  Is anyone else have any issues with 5.04 and a Gateway??

Patience is wearing out ... this machine might just end up with a different distro.

Thanks.

P.S. ... if this hoses my XP, can someone post explicit instructions on how to recover from the install?

Thanks again!

---

### Post by oprogue on 2005-05-06
ok ... time to document this so someone can either tell me where I've went wrong or if there is a greater (or not so great) underlying issue.

I've gotten past the partition and formating;
The remaining packages have been copied to the hard disk;
The time zone set;
Set up of users and passwords completed (without enabling "shadow");
Apt configured;
All successful up to this point ... 

Installing the GRUB boot loader to the hard disk
the package loads
it prompts me to install to the master boot record  ... and I say "No"
I specify hd0,9
Finish install 
prompted to reboot ...

and ... well ... least now it boots in to Windows ... ha ha ha ... without the option of booting into linux ... 

ok ok ... I've tossed SLAX in with the intention of installing it ... maybe it'll work better with an existing copy of linux already installed

---

### Post by Xian on 2005-05-06
[QUOTE=oprogue]Installing the GRUB boot loader to the hard disk
the package loads
it prompts me to install to the master boot record  ... and I say "No"
I specify hd0,9
Finish install 
prompted to reboot ...

and ... well ... least now it boots in to Windows ... ha ha ha ... without the option of booting into linux ... [/QUOTE]
I'm not sure what you are saying. Is it that depsite the fact that you tell it NOT to install to the MBR it does so anyway? It would seem that you are describing that you attempt to place the bootloader in /hda10, which is the root directory of Ubunut on you box, but it ignores you and goes to the MBR instead. What have you been using as the bootloader...SuSE?

---

