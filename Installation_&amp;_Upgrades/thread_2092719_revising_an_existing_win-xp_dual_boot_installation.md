---
title: "revising an existing win-xp dual boot installation by using &quot;boot-repair&quot;"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by bruce63 on 2012-12-08
I have a general question about changing the way an existing dual-boot installation works at boot time. It presently has windows-xp in /dev/sda2 (the active partition) and the ubuntu "/boot" partition in sda3, with ubuntu "/" in sda4. The /dev/sda1 partition has some OEM utilities in it. It all works, but is said not to be entirely compatible with windows anti-virus software that I would like to install in win-xp, due to the non-standard (grub) mbr. To avoid this conflict, I would like to restore the mbr in the active partition to microsoft standard, install grub in the sda3 /boot partition, and then edit the windows boot.ini file to boot windows normally or to optionally chain load grub in sda3, the ubuntu boot partition. 

The proposed revision mirrors an already completed fresh install on a first machine that works nicely in all respects. I am wondering if "boot-repair" has all of the features necessary to restore the windows mbr and install grub to sda3, and thereby avoid all of the effort and risk of a fresh install on a second machine. If so, it would also get around a nasty bug in this particular windows-xp (factory) installation that has, so far, prevented use of the windows recovery console from running "fixmbr" to revert to using the windows bootloader.

FYI, here's the current boot-info summary for the machine in question:
[http://paste.ubuntu.com/1419509/](http://paste.ubuntu.com/1419509/)

Any comments?

---

### Post by oldfred on 2012-12-08
Boot-Repair does not work with grub legacy. It does offer to uninstall grub legacy & upgrade to grub2. It should also let you install a Windows boot loader.
You do have to check the separate /boot partition to get grub2 to install correctly.

You are not changing active partition sda2, but the MBR. Only a few real aggressive virus checkers think grub is a virus but I have heard that before with some but usually with Windows 7. I never had that issue with my XP's virus checker which was the free AVG. But I am not running XP now and I have seen some other suggestions on virus-checkers. Are you sure the one you use thinks grub is a virus?

Windows does not chain load to another system. I have seen a few users that copy the partition boot sector to a file and use that in boot.ini to chain load. Grub2 does not like to be installed in a partition, so until you upgrade versions I might stay with grub legacy. I originally did not like grub2, but after learning about it find it better. But most of that is that grub2 works with newer systems and multi-boots better.

---

### Post by bruce63 on 2012-12-08
> Boot-Repair does not work with grub legacy. It does offer to uninstall grub legacy & upgrade to grub2. 

Good to know!

> It should also let you install a Windows boot loader.
You do have to check the separate /boot partition to get grub2 to install correctly.

Reading the cautions on the Boot-Repair web page, I get a little nervous about checking boxes on the gui based only on my guess as to exact meaning of labels and resultant action. Do you know of any closely similar examples that might be posted somewhere?

> You are not changing active partition sda2, but the MBR. Only a few real aggressive virus checkers think grub is a virus 

Yes. My impression is the problems are sporadic and unpredictable, caused by ongoing maintenance decisions by AV suppliers and/or microsoft. I want to minimize my exposure to that sort of potential random, show stopper disruption. Certainly, microsoft and its associated ecosystem are not inclined to consider adverse effects on competing OS installations, so I figure I had better think about it.

> I have seen a few users that copy the partition boot sector to a file and use that in boot.ini to chain load.

That's actually my plan. It worked nicely with last week's fresh install on another machine, which was ubuntu 12.04 /boot on sda3 and win-xp on sda2. I'm hoping to accomplish the same thing by revising the existing dual boot installation of ubuntu 10.04 and win-xp, without disturbing anything else.

> Grub2 does not like to be installed in a partition, so until you upgrade versions I might stay with grub legacy. 

Hmmm... therein lies a dilemma; the risks of upgrade to a new and somewhat unfamiliar system, versus the risks of sticking with outdated code. 

Actually, I assume last week's 12.04 fresh install here must have involved grub2. It worked with grub in sda3, the /boot partition, though I never looked closely at that partition afterward to see exactly what it did. I do vaguely recall encountering some commentary along the way, during partitioning and whatnot, that it was somehow unconventional (hazardous?) to do what I did. I overruled a recommendation at some point. I figured the win-xp hazards (and outright bugs) are harder for me to foresee or fix than any linux problem; hence my choice.

I'm going to cogitate a bit more on this before pulling the trigger. Further sage advice is most welcome. 

To patch a smoothly working install of 10.04, or start over with a new install of 12.04, and hope to quickly work through all the potential new issues, especially with "Unity"...hmmm.

---

### Post by oldfred on 2012-12-09
We often recommend Boot-Repair as it is a gui and automates a lot of the standard repairs.

Older instructions for manually updating grub or grub2.
       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2 info & full chroot version - also METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD

I am a belt & suspenders type when it comes to booting. So I keep Windows on one drive & Ubuntu on another & have each bootable from its own drive. But use grub2 to boot.
I then also have repairCD, RepairUSB and even a larger flash drive with a full install of Ubuntu with some extra entries added to my grub menu to also boot my hard drive installs.
I have flash drive with Boot-Repair, Supergrub, of course Ubuntu current version, Knoppix, gparted or parted magic and a few others to experiment with.

---

### Post by bruce63 on 2012-12-09
OldFred, Thank you. This all very enlightening.

After loading boot-repair and tinkering with the buttons, without hitting "Apply," it appears to me it may be designed to do part of what I wanted, but maybe not all. 

First, I see that it can do replacement of grub with the newer version, but it does not allow me to force grub into the /boot partition first sector as part of that process. It appears to want to put grub in /sda, which I take to mean the usual location of the mbr and partition table where windows would normally have its mbr, etc.. Maybe that is what you were referring to as a limitation above. I can see the rationale for that: the system would be un-bootable at that point, if it allowed what I want. To complete what I want, I would need to follow up manually, doing the boot sector file copy to windows, and the boot.ini edit, in order to make the ubuntu partition bootable by the windows boot loader (after having also restored the windows mbr, by some means). Boot-repair plays it safe, not assuming I am smart enough to complete the procedure on the windows side and thereby not allowing a non-bootable situation to arise. I see the wisdom in that.

Second, as a separate option, boot-repair appears designed to restore the windows boot loader, essentially thereby rendering the present ubuntu system non-bootable, but restoring windows booting without using grub (right?). Folks wishing to remove ubuntu could utilize that option, at least as a basic first step in ubuntu removal. What is not yet clear to me is the state of the partition table after that operation. I assume the ubuntu partitions would remain, but would be dead space without follow-up steps to make them bootable by the windows boot.ini chainload method, or without steps to repartition/reformat them for some other purpose. Right?

It seems one option in my case would be to let boot-repair restore windows normal operation (hoping windows' AV software does not barf on the "generic" mbr), and then follow that with a fresh install of ubuntu 12.04 lts in the upper cylinders of the hard drive, where the older ubuntu presently resides. During the 12.04 install, the old ubuntu partitions would get redefined and I assume I would have the option of forcing grub into the sda3 partition's boot sector, as in my other 12.04 install last week.

I wonder if the there might be another available option using boot-repair. Could I do two steps? First, I could let it restore normal windows boot operation, as indicated above. Then, after that, in a second step, without re-installing ubuntu, would boot-repair allow me to force grub into the first sector of sda3, the existing /boot partition? If so, the end result of would be an immediately bootable windows xp system, and an ubuntu 10.04 system that could be made bootable by the sda3 boot sector file being copied manually to windows and with the manual edit of the windows boot.ini file to permit chain loading. 

As you point out, this sort of dual booting would seem safer with separate hard drives. Unfortunately, that is usually not an option with laptops. Also unfortunately, dual booting is really handy in technical field work where laptops are the only option.

---

### Post by oldfred on 2012-12-09
While USB flash drives are not speedy it is a full drive. I have a full install in my 16GB flash drive. I find it very functional if not real fast. Once applications are in RAM it is just as fast.

I think all the new versions of Ubuntu have grub2 as default but if system has none of the new features that need grub2, you can manually install grub2 and install grub legacy.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 
[https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy](https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy)
Older threads kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

Herman's page on grub2, also several pages on installs & grub legacy. Lots of detail in Herman's site.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install)

---

### Post by bruce63 on 2012-12-12
OldFred, I am intrigued by the suggestion that a fully working Ubuntu system might run at adequate speed off of a thumb drive. I had not seriously considered that possibility. A second question would be about the working lifetime of that sort of approach, given the write cycling and read disturb limits of the flash memory in a thumb drive. Flash memory, in its raw form at least, particularly when operating cells in multi-level mode for maximum data density, may not tolerate more than a few hundred writes. With good memory management, effective cycling numbers can be much larger, of course. Results likely vary from one brand to another, due to different memory management schemes. Anyhow, based on your comments, I guess the lifetime, whatever it is, must be adequate for your purposes. Very interesting.

On the main topic here, after learning more about boot-repair, I concluded it is designed to do more than I needed to do. I intended only to modify an installation that was actually working, as opposed to repairing a broken one. So here's what I ended up doing.

To make it possible to "chain load" from the windows xp boot loader, I first installed grub in the /dev/sda3 partition by doing this, per guidance on Herman's web pages:

sudo grub-install /dev/sda3

Then, I made a copy of the boot sector of that partition and put it on the ubuntu desktop where I could see it, by doing this:

sudo dd if=/dev/sda3 of=~/Desktop/ubuntu.bin bs=512 count=1

I used the ubuntu desktop gui to mount the Windows XP file system and then copy the file to the Windows C:\ directory.

At that point, the system behavior had not been altered. The grub installation in /dev/sda was still in control at boot time. To put the windows bootloader in control, the MBR in sda had to be restored to Microsoft original, or equivalent. In my case, the Windows recovery console could not be loaded from original XP disks because of an apparent bug that fails to recognize a valid administrator password. That was further complicated by the fact that the original XP disks are said not to be directly compatible with an XP installation that has had SP1,2 and 3 upgrades. MS provides a series of postings on their support website to work around all of this, but it looked like a time consuming mess. Instead, one could install the "generic" mbr from syslinux, according to what I have read. However, I booted into Windows XP and used a piece of DOS command line freeware called MBRWiz. I had previously used it to backup the grub MBR, for disaster recovery, so it already existed on the Windows XP disk partition. In this case, I used it to restore a "standard" mbr, overwriting grub's. It took about two seconds, which compares favorably with the several hours that likely would have been needed to complete the series of work-around steps that Microsoft described. 

Having put the Windows bootloader back in operation by restoring the mbr to "standard," I then used the edit procedure documented in the Windows XP help files to add the following line at the end of the  boot.ini file:

c:\ubuntu.bin="Ubuntu Linux"

After that, booting up brings up a short menu that offers Windows XP or Ubuntu Linux. Selecting the latter then starts grub from sda3, with the familiar ubuntu menu choices. I also notice the grub menu still includes a Windows XP option that I presume is now not functional, that should be removed, but that's no big deal.

This all seems to work as desired. Ubuntu has already gone through an update cycle that included a new kernel. That update worked as before in grub. Also, I loaded MSE anti-virus in Windows XP, completed a full system scan and received no complaints from MSE. There was no adverse effect on the operation of the dual boot installation either. MSE, believe it or not, permits a relatively quick XP boot-up, as compared to the half hour or so required by the previously installed, commercial 3rd party anti-virus bloatware (that was the irritation that got me started down this path, BTW-- long boot-up times tend to defeat the purpose of carrying a laptop around). Now, if during an update or scan or whatever, MSE does as some have alleged it can sometimes do, and refreshes the mbr with a microsoft standard one, it should go unnoticed by me!

Thanks, OldFred, and also to those who posted their collected wisdom on the various web pages referenced above.

---

