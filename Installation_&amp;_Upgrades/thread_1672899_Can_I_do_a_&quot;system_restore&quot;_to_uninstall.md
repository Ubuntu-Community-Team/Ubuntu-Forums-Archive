---
title: "Can I do a &quot;system restore&quot; to uninstall Ubuntu?"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by jthompson99 on 2011-01-21
**EDIT** -- I just realized that "system restore" is going to sound like using the Windows System Restore feature. I meant system restore as in using the recovery disk that puts your pc back to the way it was when you bought it.



I need to remove Ubuntu because I am selling the computer. Will doing a system restore using the recovery disk or from the boot prompt remove Ubuntu and the partition and put the computer back to it's original state?


Thanks for any help.

---

### Post by endotherm on 2011-01-21
yes it should. most of the time they repartition the whole disk destroying everything.
if you want to be extra sure though, you can always boot to a live CD and us gparted to delete the partitions or wipe/sfill to overwrite the drive prior to restoring.

---

### Post by jthompson99 on 2011-01-21
Ok, I'm not sure what you mean by "live" cd. And then are you saying use gparted to delete the partition before I even attempt the recovery?

---

### Post by Old_Grey_Wolf on 2011-01-21
I have never seem a recovery CD that did **not** repartition the HDD. 

I see a lot of post on the forums with titles like, "I restored Windows and now my Ubuntu is gone". :)

If it doesn't reformat the HDD, you have only wasted about 45 minutes of your time.

---

### Post by endotherm on 2011-01-21
> **jthompson99 said:**
> Ok, I'm not sure what you mean by "live" cd. And then are you saying use gparted to delete the partition before I even attempt the recovery?
a liveCD is a bootable OS that lives on a CD. Ubuntu's install CD is a live CD, so if you put it in and reboot, you can boot off it instead of off the harddisk in your PC. this is important because an OS cannot format or remove a partition that contains the running OS, so we need to boot into another os that does not live on your hdd. 

BTW, I am not saying you need to wipe or unpartiton, but it is a way to be extra sure that ubuntu is gone for good, and yes you would have to do so Before running the restore. the restore disk will likey destroy any ubuuntu partitions anyway, but since i know nothing about your PC, i can't say for sure.

---

### Post by jthompson99 on 2011-01-21
Ok cool, thanks for the help guys. I think I am going to try the recovery CD.

And yes, I want to get rid of the partition and all of the data in ubuntu and vista.

---

### Post by jthompson99 on 2011-01-21
Ok, so I restored the computer to the factory default, but when I reboot, it still brings up that GRUB menu and let's me boot into Linux. I'm sure if I boot into Vista, it will be the factory default though.

How do I get rid of that and have it just boot into Windows like normal?

Thanks.

---

### Post by endotherm on 2011-01-21
it looks like your restore disk did not overwrite the MBR on your disk, so grub is still there, even thought the OSes that used it are now gone. 

here are some articles on how to repair a vista mbr:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)

---

