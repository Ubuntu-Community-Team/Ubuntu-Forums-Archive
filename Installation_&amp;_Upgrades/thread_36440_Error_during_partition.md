---
title: "Error during partition"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by wolfesidhe on 2005-05-23
I just tried to install version 5.04 on a friend's pc for him to dual boot with win me. It was originally an e-machine, but they have upgraded it somewhat, adding a second hard drive, new cdrom, etc....   It gets to the part where it's going to partition the second drive , and I get the following error:

[!] Partition disks

Input/output error during read on 
/dev/ide/host0/bus0/target1/lun0/disc
ERRORR!!!


I try to go back and it goes on to the formatting swap space. It gets stuck at 0% formatting swap space in partition #5 of IDE1 slave (hdb)... 


Any ideas what can cause this or any work-arounds?

Thanks

---

### Post by nemin on 2005-05-23
[QUOTE=wolfesidhe]It gets to the part where it's going to partition the second drive , and I get the following error:

[!] Partition disks

Input/output error during read on 
/dev/ide/host0/bus0/target1/lun0/disc
ERRORR!!!


I try to go back and it goes on to the formatting swap space. It gets stuck at 0% formatting swap space in partition #5 of IDE1 slave (hdb)... 


Any ideas what can cause this or any work-arounds?[/QUOTE]Did you ever check the HD? Are you sure it's OK?

---

### Post by wolfesidhe on 2005-05-23
[QUOTE=nemin]Did you ever check the HD? Are you sure it's OK?[/QUOTE]

We did run a couple of different programs to see if there were any errors on the drive but nothing was found. It was one that came out of one of my other computers and it worked fine in there.  No idea what could cause it

---

### Post by [RIT]IVIr_Evil on 2006-01-05
I have the same exact problem, I have tried my ubuntu cd my kubuntu cd and my debian cd and I get the same problem.. Then I installed Windows XP and it worked fine.  I'm lost? any help will be greatly appreciated.. 


thanks

-tom

---

### Post by Vevmesteren on 2006-02-07
well, I am running into this as well. During the last shutdown the system stated a refresh of some kind failed so he let it be for 5 minutes, I let the the system run on try to fix it, every five minutes I had the same error so I force quit and tried rebooting. Now I get Grub Error 16 when trying to reboot. I have tried reinstalling the grub as per this post: [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=Grub+Error+16](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=Grub+Error+16) to no avail. Is this really just the hard-drive dying on me like that. It is no older then two years, does this maybe mean there are some downsides to my migrating adventure after all? I loooooove Ubuntu, but this kind of error seems rather serious. I do not have any critical data on the hard drive, so reformatting is no problem. But when trying to do so I am told the same thing as the messages above:

[!] Partition disks

Input/output error during read on
/dev/ide/host0/bus0/target1/lun0/disc


any suggestions, maybe a one disc bootdisc that could just check wether the hard drive is bust or not?

anyone?

---

### Post by indoz on 2006-02-19
My first try to install any linux release. When I get to partition section of install it reads my hdd as sda1 instead of hda1. Also calls it a scsi drive and my hdd is sata. Will not allow me to resize!! I tried changing to hda1 but no change

---

### Post by Vevmesteren on 2006-02-19
my issue was easily tracable once I checked into it. My HD is busted...bummer.

---

### Post by izardstreet on 2006-02-28
i am having this input/output installation issue as well.
its darn well frustrating.

DOES anyone at Ubuntu know the fix?
PLEASE!
i do not think it is my harddrives, they install Windows fine.

---

### Post by maka on 2006-02-28
i recieved the same error

---

