---
title: "No CD/DVD after Feisty Fawn update to 2.6.20-14-generic"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by muncrief on 2007-04-06
I upgraded to Feisty 7.04 (AMD64) last week and didn't have any problems. I didn't see any difference between it and 6.10 but I like to keep up to date so I've been running it since then.

Unfortunately this morning I applied all of the new updates, including the kernel upgrade to 2.6.20-14-generic (my previous kernel was 2.6.20-13-generic), and I can no longer access my DVD or CD drives.

I've done my best to find out what the problem is by searching the Ubuntu forums and the Internet in general, but so far I've only found a lot of references to people losing their hard drives after the upgrade. I guess I can be thankful that my computer at least booted after it (I think it's because I have SATA drives, the problems seem to have to do with PATA drives). 

In any case, this is a major disaster for me, and it's mind boggling that an update could be so devastating to so many systems that had previously worked perfectly.

Does anyone know how I can fix this problem? If not, does anyone know how I can "un-upgrade" back to the previous kernel?

Any help would be greatly appreciated. Thank you.

---

### Post by muncrief on 2007-04-06
After reviewing more reports about the lost drives (both hard and optical) I realized that the problem is in the recent updates configuration of /etc/fstab for parallel IDE ATA drives of any type. It looks like all parallel IDE ATA drives are now being mapped as SCSI devices and fstab doesn't realize it.

Before the update to the 2.6.20-14-generic kernel my DVD drive was mapped as /dev/hda, and my CD drive was /dev/hdc.

After the update my DVD drive was remapped to /dev/dvdrw, and my CD drive to /dev/cdrom. This is actually great, and far more intuitive and logical than the previous mapping. However, fstab was not updated correctly.

It also appears that the remapping of hard drives is also intuitive if you know about the SCSI translation.

I can't test this because I have serial ATA drives, but, for example, if your drive before the update was /dev/hda you might try changing it to /dev/sda. Just edit /etc/fstab and look for "hda", and change it to "sda",  then save the file and reboot. This will hopefully at least restore your root partition and allow you to boot into the GUI.

In any case, this is a pretty icky (technically speaking) and needless error, which novices could have a very difficult time recovering from. It should be fixed ASAP.

---

### Post by Dubstar_04 on 2007-04-07
I am also suffering from the same issue. Everything was working fine untill i updated and now my pc hangs at boot for nearly 30 seconds and the dvd srive won't work!!!  I really hope there is an up date fixing the problem as everythoing else is fine!!

You can down grade to another kernal by pressing escape at boot and loading an older kernal from the list and once booted you  can remove the newer ones using synaptic, just search for linux image and remove the one you require. 

I booted in to the older kernals and it seemed to make very little difference so it suggests that the problem is with HAL rather than the kernal!!

Just letting you know that your not alone with this problem.

Dubstar.

---

### Post by Dubstar_04 on 2007-04-07
After trying to solve this problem since since 9 oclock this morning, I tried loading 2.6.20-13-generic again and it worked fine!! now I can nurse my hangover to a dvd!!!

So it is a problem with the new kernal!!

I hope this helps,

---

