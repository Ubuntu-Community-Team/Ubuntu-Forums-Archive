---
title: "Grub not installed to MBR on Feisty installation"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by 51m0n on 2007-04-25
I have tried alternate and desktop ISOs, but in both cases once the installation procedure is complete when the machine reboots its as if nothing was put in the MBR by GRUB. The machine just reboots itself over and over. There is absolutely no GRUB stage messaging at all.

If I use the rescue option I can mount the drives and see the data. I am no GRUB expert, and vi is almost unusable in the rescue disk, so any real editing is virtually no good.

I have tried grub-install, same issue, I have tried the GRUB super disk, no change, in fact asking the system to boot using the super disk, it finds none of the drives in the fstab file.

For information purposes this is running on an Abit KG7-RAID mobo, with a highpoint raid controller built in. I saw all the issues around Dapper and extra controllers and never bothered to install because of those issues (stuck with Mdk 10.1 Community). Now I actually need to install a newer system (new HP printer wont play with older Linux) and apparently these issues are supposed to be fixed.

Its not some weird piece of server kit we're talking about, if (K)Ubuntu cant run with 5 year old desktop mobos, or anything with more than one IDE/SATA controller its a pretty hopeless state of affairs - Linux has a very good rep with this stuff, so how come its all broken now?

Can anyone tell me the secret to getting this stuff to work? After plodding through endless forums and posts I cant find a defacto way that works and wont require a rescue disk every time I need to update the kernel. What gives?

Thanks for any and all assistance!

---

### Post by zvacet on 2007-04-25
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by 51m0n on 2007-04-25
Nice link!

OK I gave up on Feisty went to Dapper.

In Dapper I can get to GRUB Loading Stage 1.5 and then nothing at all, no error.

I can, however boot using the Grub Super Disk!

Hooray!

Once into Dapper I start a terminal and:-

>sudo grub

grub> find /boot/grub/stage1

Error 15: File Not Found

:confused: 

How the hell did I manage to boot here at all??

I guess this is the root of the problem I've got here.

Interestingly Grub Super Disk refers to hda1 and in every distro I've ever run its lways been hde1 as its on the RAID controller (though just used as an IDE controller)

One last point, clearing the MBR boots into W2K no problem at all....

Any clues anyone?

---

