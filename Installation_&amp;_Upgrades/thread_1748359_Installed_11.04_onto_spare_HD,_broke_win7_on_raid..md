---
title: "Installed 11.04 onto spare HD, broke win7 on raid."
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by RichardUK on 2011-05-03
I have a dell with win7 installed on two disks as raid0. I added a 3rd HD and installed 11.04 on to it. This boots ok but only Linux shows in the grub menu. Win7 is not there and I have no way to boot it as the installer put grub on disk0 of the raid overwriting the windows boot prog. 

Is it dead????? Can I fix it?????? :(:(:(:(

---

### Post by Quackers on 2011-05-03
You needed to make sure that grub was installed to the mbr of the Ubuntu drive.
Does your raid array show as "normal" in your bios? If it has broken the raid array you will need to make a new one and re-install Windows 7. 
If the raid array shows as normal you should be able to fix the Windows bootloader with a Windows repair/installation disc.
Grub can be re-installed to the mbr of the Ubuntu drive later.

---

### Post by RichardUK on 2011-05-03
When installing I did think I should have unplugged the raid drives but I was worried the bios would forget them and so I would loose them.

I had expected the installer to have asked me which drive to put grub on but it didn't'.

I think the raid is still intact as Ubuntu shows the drives with raid for the partitions although I don't know how to mount them to back up some of the data on them.

I need look at the manufacture's website as it had one of these recovery partitions for reinstalling back to factory but as grub has killed the boot stuff it can't boot to the restorer.

This is a real pain, it's a work pc. I've used Ubuntu at home for years without problems, I wanted it on the work PC as Android development is easier in ubuntu that win7 64bit.

---

### Post by Quackers on 2011-05-03
At the bottom of the partitioning screen in the installer there is a field named "device for bootloader installation" and it defaults to /dev/sda.
You needed to change that.
You need to run the startup repair up to 3 times on the Windows system from a Windows Vista/7 repair/installation disc.
If you use a recovery disc or partition to recover Windows you will lose all your data and Ubuntu as well.

---

### Post by RichardUK on 2011-05-03
Ah, I tried the windows repair disk but only the once. I'll give it a few more goes and hope it comes back to life. Ta. :)

---

### Post by Quackers on 2011-05-03
If no joy please report back as there are other things to try.

---

### Post by YesWeCan on 2011-05-03
Lots of people have problems with the Ubuntu installer defaulting to sda and not giving adequate warning about it. This is Ubuntu's fault and ought to be fixed. So you are not alone.

I always recommend physically disconnecting all Windows disks before trying to install Ubuntu to guarantee that grub doesn't corrupt anything Windows needs. You want Grub installed to the Ubuntu disk and nowhere else.

I suspect you will not be able to boot your RAID0 Windows using Grub. So you will have to use the bios to select which disk to boot from. Not a big deal.

An alternative is to install EasyBCD in Windows and use it to add Ubuntu to the Windows bootloader. This works well.

---

### Post by RichardUK on 2011-05-04
Got it working, got a rescue disk from another win7 machine.
Used the command "bootsect /nt60 d: /mbr"

Replacing D: with what ever the raid is, this will be showing as the windows install the rescue disk finds.

Few, close one. :)

---

### Post by RichardUK on 2011-05-04
> **YesWeCan said:**
> Lots of people have problems with the Ubuntu installer defaulting to sda and not giving adequate warning about it. This is Ubuntu's fault and ought to be fixed. So you are not alone.

I always recommend physically disconnecting all Windows disks before trying to install Ubuntu to guarantee that grub doesn't corrupt anything Windows needs. You want Grub installed to the Ubuntu disk and nowhere else.

I suspect you will not be able to boot your RAID0 Windows using Grub. So you will have to use the bios to select which disk to boot from. Not a big deal.

An alternative is to install EasyBCD in Windows and use it to add Ubuntu to the Windows bootloader. This works well.

I don't think it gave me an option to choose where to install grub, although I can not be sure. This is the second time I've failed to install Linux on a system that has windows on a raid. 

I 'think' it is either an issue with grub not being able to work the raid, it is after all one of these 'fake' raids that most motherboards have, or the installer failing to create the windows entry in the grub menu. Either way it's not good, which is a real shame as I've been boaring everyone I know about how great Linux is. :)

---

### Post by RichardUK on 2011-05-04
> **Quackers said:**
> If no joy please report back as there are other things to try.

Thanks for your help. :KS

---

### Post by Quackers on 2011-05-04
It has been advised to install kpartx to the live desktop before trying to install 11.04 to a so-called "fakeraid" system.
Ubuntu's support for fakeraid has been somewhat flaky at times.
The choice for placement of grub is definitely there at the bottom of the partitioning screen. I have used it many times in the last few months. You missed it! Can't blame Ubuntu for that :-) It has been made much more visible in 11.04 in that it has a separate entry on the page now. Previously it was hidden behind the "advanced" button.

---

