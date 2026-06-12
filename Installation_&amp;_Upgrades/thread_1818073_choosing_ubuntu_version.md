---
title: "choosing ubuntu version"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by ozonora on 2011-08-04
Hi, I have just installed a second hard disk (320 GB) on my desktop computer to have my several Windows installations and Ubuntu in diferent phisical disks. This way, I can format the OS without breaking the boot record or whatever. I think it is the easiest way.

In addition, my computer has a 64 bits processor.

I have two questions:

[LIST]
[*]Should I install Ubuntu 10.04 or 11.10? (I don't mind formatting the computer every 6 months).
[*]Should I install Ubuntu 32 bits or 64 bits? (I guess that 64 bits will be better, but I think I have heard of some problems when using Ubuntu 64 bits).
[/LIST]
Thank you very much, you're great.

---

### Post by Megaptera on 2011-08-04
My contribution:
- I'm not keen on Unity in 11.04 onwards so I'm content to use 10.04 LTS with Gnome.
- My Dell laptop runs the 64 bit version with no issues - but I'm not into vid editing or rendering etc so can't comment on issues or not from that angle.

---

### Post by tommpogg on 2011-08-04
> **ozonora said:**
> 

[LIST]
[*]Should I install Ubuntu 10.04 or 11.10? (I don't mind formatting the computer every 6 months).
[/LIST]


You don't need to format every 6 months to upgrade your OS. You need to do that only if something goes wrong with the upgrade process.

> **ozonora said:**
> 

[LIST]
[*]Should  I install Ubuntu 32 bits or 64 bits? (I guess that 64 bits will be  better, but I think I have heard of some problems when using Ubuntu 64  bits).
[/LIST]


I would choose 64 bit.

In the end my suggestion is Ubuntu 11.04 64-bit or Ubuntu 10.04 64 bit

---

### Post by YesWeCan on 2011-08-04
> **ozonora said:**
> Hi, I have just installed a second hard disk (320 GB) on my desktop computer to have my several Windows installations and Ubuntu in diferent phisical disks. This way, I can format the OS without breaking the boot record or whatever. I think it is the easiest way.
Definitely. Just make sure the Ubuntu installer doesn't/didn't stick the Grub boot code on your Windows disk.

I use 64 bit 10.10. I'm not intending to upgrade to 11.04.

---

### Post by ozonora on 2011-08-04
> **YesWeCan said:**
> Definitely. Just make sure the Ubuntu installer doesn't/didn't stick the Grub boot code on your Windows disk.
What do you mean? How can I avoid problems with Ubuntu touching my main disk?

---

### Post by YesWeCan on 2011-08-04
> **ozonora said:**
> What do you mean? How can I avoid problems with Ubuntu touching my main disk?
Well, the way Grub works it overwrites the normal MBR boot code of a disk. Sometimes this can cause problems with Windows. So I always recommend keeping your Windows disk entirely untouched by Ubuntu.

A problem can arise if you use the Ubuntu installer to do things automatically because it defaults to putting the grub boot code on /dev/sda and you may not be aware it is doing this. Most people start off with Windows and so it is installed to sda.

You can either select manual partitioning in the Ubuntu installer and choose where you want Grub put OR avoid the decision altogether and disconnect your Windows disk while you install Ubuntu.

---

### Post by ozonora on 2011-08-04
Thank you very much for your tip, YesWeCan. The installer lets me choose to instal GRUB in the secondary disk.

A final question. How should I configure the partitions on my disk? I said that I have 320 GB. I now that I need a primary partition for /. How many megas? Should I install /home in another partition? How many megas for that if neccesary? And how many for the swap if I have 4 GB?

Thank you all!

---

### Post by Hakunka-Matata on 2011-08-04
> **ozonora said:**
> Thank you very much for your tip, YesWeCan. The installer lets me choose to instal GRUB in the secondary disk.

A final question. How should I configure the partitions on my disk? I said that I have 320 GB. I now that I need a primary partition for /. How many megas? Should I install /home in another partition? How many megas for that if neccesary? And how many for the swap if I have 4 GB?

Thank you all!



[LIST]
[*]11.04 - 64 is a good Release, Unity Desktop is not to my liking so  I switched to "Ubuntu Classic" during logon (after selecting username,  and BEFORE entering password, move cursor to bottom margin, and select  "ubuntu classic)  This  is only possible while you are not using automatic logon, unless you're quick enough to interrupt the automatic logon countdown.
[*]
[*]for / system partition 30 GB is plenty  (if you are also going to use a /home) and it can be a logical partition, Ubuntu does not require a primary partition for the OS.  Windows does require a primary partition.
[*]**EDIT** above line to read **20GB for root**, I trust YesWeCan, but I do have a root partition that uses a /home partition for data, and the root is currently using 12.37GB, so I'm not entirely convinced 10GB is enough.
[*]
[*]for /home 50GB is large, but you have to decide that depending on how much data you will have.  It can be easily resized later if necessary.
[*]linux swap - recommended 2X RAM if you're going to hibernate, but I only use 2GB with 4 GiB RAM and it works fine, I don't hibernate.
[/LIST]
Caveat:  Partition sizing is a very personal choice, / partition does have minimum requirements, say about 20GB, but after that it's just a matter of how big the drive is and how you want to split it up.  Search "recommended Ubuntu partition size" and have a look.  

[https://help.ubuntu.com/](https://help.ubuntu.com/) I find useful and more or less, Official.

---

### Post by cogier on 2011-08-04
Well it seems everybody has an opinion which is what Linux is all about.

I would suggest using Ubuntu 10.04LTS until the bugs in Unity have been ironed out and unless there is a specific reason to use 64bit software I would stick with 32bit.

But that's only my opinion!

---

### Post by YesWeCan on 2011-08-04
> **ozonora said:**
> A final question. How should I configure the partitions on my disk? I said that I have 320 GB. I now that I need a primary partition for /. How many megas? Should I install /home in another partition? How many megas for that if neccesary? And how many for the swap if I have 4 GB?
4GB swap is enough.
It doesn't matter that much whether you have a separate /home. It can make clean installs easier. If necessary, sizes can be changed in the future by using GParted.
10 GB root
4 GB swap
rest for home

---

### Post by vlbaindoor on 2011-08-04
> **YesWeCan said:**
> Well, the way Grub works it overwrites the normal MBR boot code of a disk. Sometimes this can cause problems with Windows. So I always recommend keeping your Windows disk entirely untouched by Ubuntu.

A problem can arise if you use the Ubuntu installer to do things automatically because it defaults to putting the grub boot code on /dev/sda and you may not be aware it is doing this. Most people start off with Windows and so it is installed to sda.

You can either select manual partitioning in the Ubuntu installer and choose where you want Grub put OR avoid the decision altogether and disconnect your Windows disk while you install Ubuntu.
Hi there,

If you disconnect your Windows disk while installing Ubuntu you may have more problems - some motherboards seem to present the first SATA hard disk it finds as '/dev/sda' to the Linux installer - so if you install it in this way and then re-introduce your Windows disk - you will have multiple problems.

As the hard disk with Windows was not at all modified, Windows is configured to assume that it is the main hard disk in the system and it will boot. The second hard disk and your Ubuntu installation would then be unbootable as it is. The boot loader needs to jump in first and present you with a choice whether you want to boot into Windows or Ubuntu and the most common way to achieve this is by having the MBR of the first hard disk modified so that you would be presented with this choice.

If while installing you had only one hard disk all the disk mappings may change and you may have some problems later on. Luckily for you the Ubuntu boot process looks for a '/etc/fstab' file on the Ubuntu root file system to mount various partitions and the present day Linux installations use 'UUID' rather than 'dev/sdx' etc which was earlier format. Hence booting once root partition is discovered would not be a major problem.

Personally I have a triple boot system with two versions of UbuntuStudio and a Windows 7 64bit versions.

I use UbuntuStudio64 - because when I tried the standard Ubuntu64bit, the Gnome was unusable and Unity was not supported on my hardware and Kubuntu64 seemed to work but sound card gave lots of problems - so I am now using UbuntuStudio 64bit 11.04.

My Windows 7 is on a completely different hard disk, my Ubuntu is on a different hard disk and actually my '/home' partition is on a third hard disk. But I did not do any hardware changes while installing Ubuntu - I just put the bootable CD and chose the install options more carefully.

---

### Post by Hakunka-Matata on 2011-08-04
Ya, opinions, I don't really like to recommend settings either, but since the OP had sat 5 hours without a response I decided to offer something, in case he was waiting.  Actually I prefer 32 bit also.

---

### Post by ozonora on 2011-08-04
Thank you all for your opinions!

---

### Post by YesWeCan on 2011-08-04
> **vlbaindoor said:**
> Hi there,

If you disconnect your Windows disk while installing Ubuntu you may have more problems - some motherboards seem to present the first SATA hard disk it finds as '/dev/sda' to the Linux installer - so if you install it in this way and then re-introduce your Windows disk - you will have multiple problems.

As the hard disk with Windows was not at all modified, Windows is configured to assume that it is the main hard disk in the system and it will boot. The second hard disk and your Ubuntu installation would then be unbootable as it is. The boot loader needs to jump in first and present you with a choice whether you want to boot into Windows or Ubuntu and the most common way to achieve this is by having the MBR of the first hard disk modified so that you would be presented with this choice.

If while installing you had only one hard disk all the disk mappings may change and you may have some problems later on. Luckily for you the Ubuntu boot process looks for a '/etc/fstab' file on the Ubuntu root file system to mount various partitions and the present day Linux installations use 'UUID' rather than 'dev/sdx' etc which was earlier format. Hence booting once root partition is discovered would not be a major problem.

Personally I have a triple boot system with two versions of UbuntuStudio and a Windows 7 64bit versions.

I use UbuntuStudio64 - because when I tried the standard Ubuntu64bit, the Gnome was unusable and Unity was not supported on my hardware and Kubuntu64 seemed to work but sound card gave lots of problems - so I am now using UbuntuStudio 64bit 11.04.

My Windows 7 is on a completely different hard disk, my Ubuntu is on a different hard disk and actually my '/home' partition is on a third hard disk. But I did not do any hardware changes while installing Ubuntu - I just put the bootable CD and chose the install options more carefully.
Windows XP sometimes makes a fuss if it is not installed to the first boot drive. With Vista and Win 7 it is much less sensitive. But as you can easily switch the Windows disk to be the first boot disk when necessary it is not a problem. I think the bigger problems are when you replace the Windows disk MBR with Grub's. So this is why I always recommend a separate disk for Ubuntu and Grub on that disk. Booting Windows from Grub in this arrangement is no problem in my experience (except for XP in some situations, IDE I think).

---

