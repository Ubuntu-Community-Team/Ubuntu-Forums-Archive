---
title: "ubuntu install issues on dual boot raid"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by darkzenlord on 2010-04-15
simply put. I have 2 HDs in RAID 0 a 3rd HD for back-ups and a 4th HD for media. I backed everything up and created a partition on the "back-up" drive. I wanted to install ubuntu to it. My Main OS is XP and is on the RAID array. I booted from the latest ubuntu .iso and found the 50gb partition I wish to use on the "back-up" drive. I selected it and told it to install. It finished installing and said to reboot, took the disk out, and the system booted right into windows. When I went into the file browser, the whole "back-up" disk does not show up now. Plus the computer won't prompt me to boot to ubuntu. Anyone have any suggestions on how I can get my disk back? and how I can get it to dual boot.

Notes: I did not install any "raid drivers" before the OS install because I figured ubuntu didn't need them. I think it's possible "grub" did not recognize the windows raid partition and got lost somehow.

---

### Post by darkzenlord on 2010-04-15
I am a bit confused but I spoke with some fellas on the ubuntu chat. They say windows will not recognize the partition that is EXT4 format, I understand and thats fine. The rest of the "missing" drive is NTFS and still has data on it but is somehow NOT recognized by windows. One thing I am interested in is where do I put the bootloader code? I put it on the ubuntu partition but my comp still boots into windows no questions asked. I am afraid to put it on the windows drive because it might mess up my windows. Am I right or wrong on that?

Note: also, where do I select the disk to begin? Example it asks ( \  or \boot etc....) I selected \ as I figure this to be the root directory. I wish this was easier. I think I should have just gone virtual box.

---

### Post by darkzenlord on 2010-04-15
Sorry for all the replies:

Update!!!
I was able to get my "back-up" partition back. I booted from the ubuntu .iso CD and went into the file system of the disk, I compared it to my "media" drive and found MBR info on it. I deleted this info. I guesstimate it was the bootloader info from the first ubuntu install. This would in theory render the drive invisible considering it is not configured for windows. I booted to XP and viola it's there. The partition I made EXT4 is not, but i expected that. I also reformatted the "ubuntu" partition again so when I decide to install, it will be labeled and formatted for ubuntu and may make it clearer during the install. 

So, it's down to this conclusion, during the install, I would have to write the "bootloader" to the XP drive? Even though ubuntu is located on a separate drive?

---

