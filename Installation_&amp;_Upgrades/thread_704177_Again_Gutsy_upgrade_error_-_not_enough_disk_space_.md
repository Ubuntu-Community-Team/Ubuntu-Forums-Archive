---
title: "Again: Gutsy upgrade error - not enough disk space in /boot"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by dfro on 2008-02-22
Just like with my attempt to upgrade to fiesty, I have run into the /boot partition being too small.  It is 45 MB, but the upgrade says I need 11 MB more free space.

So, that I do not ever have this problem again, what would experienced partitioners in ubuntu suggest for the definitive "/boot will never be too small ever again" size?  100 MB? 150 MB? or maybe 200 MB?

Thanks,
dfro

---

### Post by mxg01 on 2008-02-22
100Mb seems to be the usually recommended amount of space for /boot. I suppose if you are only going to have the last and current kernel then that should be fine.

Might be worth seeing what kernels you have in there and removing any that are old and unused. You may need to remove them from GRUB options then too. This scenario shouldn't occur as the upgrade process maintains what's in /boot. 

There is a bug mentioning the messages and what they might mean:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/104337](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/104337)

---

### Post by dstew on 2008-02-22
Remove old unused kernels using Synaptic. That way, the kernel files are gone, and the grub menu is updated also. Then you will have enough room.

---

### Post by dfro on 2008-02-22
Here are the contents of my /boot partition:

abi-2.6.20-16-generic
config-2.6.20-16-generic
config-2.6.20-16-lowlatency
grub
initrd.img-2.6.20-16-generic
initrd.img-2.6.20-16-lowlatency
lost+found
memtest86+.bin
System.map-2.6.20-16-generic
System.map-2.6.20-16-lowlatency
vmlinuz-2.6.20-16-generic
vmlinuz-2.6.20-16-lowlatency


Is there anything that looks removable? I already removed the .bak files.

Thanks,
dfro

---

### Post by dstew on 2008-02-22
You could look in lost+found for files to delete. Do you really want both the generic and low-latency kernels?
EDIT: What is lost+found doing in your boot directory? I don't think that is where is usually is. But, if it had no files in it, then you are stuck with throwing overboard one of your kernels.
EDIT again: Those files shouldn't add up to 50 megabytes. The kernel images should only be 5 Mb or so, the other files even less. Something doesn't add up.

---

### Post by dfro on 2008-02-22
Dstew, nothing was in lost+found so I deleted it. I have in /boot what the Ubuntu Studio team decided to put in there.

I am going to get rid of the /boot partition. This is a problem I am very not interested in figuring out. 

Wish me luck! I hope all of my /home settings work after I have repartitioned the hd and done a fresh install! I also hope I can get grub working again. It took me a while with two internal sda drives.

Thanks,
dfro

---

### Post by dfro on 2008-02-23
The reinstall went well. Reinstalling instead of upgrading gave me a chance to reorganize, clean up, and resize my partitions, and probably cleanup a lot of newbie experiment files scattered everywhere.  Now /boot is in the / partition!! Yeah!

I first rsync'ed my files to and external backup hd. I then downloaded, burned, and launched the Ubuntu Gutsy live cd, since Ubuntu Studio does not have a live cd. I launched gparted in the live cd and with it erased and recreated my partitions.  I did it this way, because trying to resize and move everything while retaining the data was taking hours.  

I then launched  the latest Ubuntu Studio dvd and did a fresh install. During the grub install and configure stage, the installer noticed my other internal hd with  Windows on it.  I let it automatically write to the Windows mbr, and now Windows launches fine. I remember reading that writing to the Windows mbr was risky, but I did not want to spend hours studying how to reset all of the grub configure files, without touching the Windows hd. At one point I figured out how to do this, but I did not feel like relearning it.

During the install and when I first loaded Ubuntu Studio, the screen was not displaying correctly. But, once I found the nvidia drivers that Ubuntu cannot put in thier package, the display corrected itself.

I did not rsync my /home folder back.  I just dragged and dropped everything.  I decided to start fresh with all of my settings - the Ardour-noire look is so cool.

Ubuntu Studio rocks!  Thank you to the developers!

Thanks,
dfro

---

