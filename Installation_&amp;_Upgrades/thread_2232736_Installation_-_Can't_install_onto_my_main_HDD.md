---
title: "Installation - Can't install onto my main HDD"
date: 2014-07-03
forum: Installation &amp; Upgrades
---

### Post by andrewerkinger on 2014-07-03
Hello, I'm sorry if the title is not that specific, I'm just not sure how to word it. During the installation (I have tried both DVD/USB) when it comes to the time that I choose to install with Windows 8, and when it brings me to the partition page, I cannot seem to find my main 500GB hard drive. Yet it shows the windows recovery drive, I hope the pictures will explain better. Thanks for the help everyone :)

---

### Post by grahammechanical on 2014-07-03
How many drives do you have? If you have only one drive then where is the Windows partition?

My suggestion is to run the live session until you get to a desktop and run either the Disks utility or the partitioning tool Gparted and examine what they show you as to what drives and partitions are available.

If you have two drives then look at the first image and the panel that says "Select Drive." At the far right hand end of the panel is a small downwards pointing arrow. If you click that it might reveal another drive, the one with Windows on.

It is my guess that the installer/partitioner is either very smart or very dumb. By choosing the Install alongside option it has to create two partitions for Ubuntu (one for Ubuntu and one for swap) and it is being smart by offering to shrink the Windows recovery partition instead of the Windows partition. That could be a smart thing to do. But the partitioner may not be so smart. It might be fooled by this drive being the first drive (sda) with Windows installed on a second drive (sdb).

I am of the opinion that the partitioner is dumb and is offering to install Ubuntu in sda because it is programmed to install alongside Windows into sda. Now I could be completely wrong in all this. It all depends on whether you have a second hard drive with Windows installed on to it. One thing is certain. The installer is seeing a 500GB drive. Total the sizes for sda1 and sda3 and you get 500GB.

Another idea has entered my head. Do you have Windows 8 installed? When Windows 8 shuts down it does not actually shut down. It hibernates and that fact could be preventing the installer from identifying what is in sda3 apart from it being a NTFS partition. And for the same reason it will not offer to resize sda3.

Regards.

---

### Post by andrewerkinger on 2014-07-03
Thanks for the response! Yes, I am running windows 8, and I think that maybe the problem, as I recall when I tried to install Ubuntu back on 7 on a false shutdown I think I had the same problem. That's interesting that it does not shut down. So if that is the case, I guess I should do some research how to REALLY shut down 8. 


[COLOR=#000000]Thanks Grammechanical! And yes, the installer may not be on the smart side ;)

EDIT: Just found out how to do the full shutdown, I'll hopefully reply again within a fully installed Ubuntu ;)[/COLOR]

---

### Post by Mark Phelps on 2014-07-04
Do NOT, repeat NOT, use the installer to shrink the Win8 OS partition.  Doing this risks corrupting Win8 and rendering it unbootable.

Instead, use the Win8 Disk Management utility to shrink the OS partition.

---

### Post by andrewerkinger on 2014-07-16
If I use this, do you think that it would show up as a part of my hard drive in the installer, instead of just the recovery? 

Thanks, 
Andrew

---

### Post by Bucky Ball on 2014-07-17
Do you have one hard drive because /dev/sda3 looks like 500Gb of unallocated space to me. Weird thing is, it's marked as /dev/sda3 = unallocated. If it's unallocated, it shouldn't have /dev/sda3. There's no /dev there. I would get rid of this as it may well be causing your issue.

Again, NEVER resize Win8 with Gparted. Resize with Windows tools then when at the partitioning section of the install, use 'Something Else' and partition manually.

---

