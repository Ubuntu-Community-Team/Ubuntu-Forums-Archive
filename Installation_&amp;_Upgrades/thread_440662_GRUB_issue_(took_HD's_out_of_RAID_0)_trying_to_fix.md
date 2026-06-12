---
title: "GRUB issue (took HD's out of RAID 0) trying to fix"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by 4Given_P8ntblr on 2007-05-11
My brothers computer was working and i then tried to see how cool it would have been to run Ubuntu linux on it just from the CD and such. Well i did that and tried to install the nVidia drivers to it and then restart, well i did and then rebooted using the CD to find that it didn't apply the drivers(no duh) because it was all running from the RAM. Well when i decided to give up and just to boot his computer normally to the current RAID 0 that i set up about 4 months ago to XP, after POST is said “A disk read error occurred.” When i noticed this i thought something must have gotten switched in the BIOS because of the Ubuntu CD boot. So i looked at settings and all seemed fine. Well under the Integrated peripherals option in bios i think the top item "SATA AHCI Mode was set to RAID, but i cannot select that option anymore, only AHCI and Disabled. So i try and boot and then see that the Gigabyte RAID setup thing says that one HD is set to Non-RAID and the other says RAID Inside.

The stripe setup below says Model Name=RDD0:, RAID Level=0-Stripe, Capacity Status=159 GB Failed, Members(HDDx)=?1

I think that this is major issue. I don't know how to fix it without deleting the RAID and reinstalling everything. I know my brother will be very disappointed if i have to do that. So based on the situation, do you have any suggestions how i can get this RAID 0 Stirping up and running again.

I’m not sure but this could also be an issue where GRUB has installed on one of the HD’s in RAID 0 Striping and caused it to say that it is in Non-RAID mode while the other says it’s RAID Inside. Does Windows XP normally use GRUB for running XP on a RAID 0 partition? Would this be something where I just delete the GRUB file on that Non-RAID HD so that they two can become the RAID they originally were. My question is how I get this Native Windows XP system working again soon.  

Thank you for reading this,

~Chris~

---

### Post by 4Given_P8ntblr on 2007-05-12
***UPDATE***

I don't know what happened nor what the solution was, but when my brother came home saw the note i had written him explaining the situation he turned on his computer and it ran fine. I came home all scared to see his light on in his room and there he was on the Windows desktop. So i'm not sure what went on but it's working somehow by the Grace of God! I just hope it stays that way.

---

