---
title: "Broken dual boot, lost root(?)"
date: 2018-01-24
forum: Installation &amp; Upgrades
---

### Post by 2912pwil2 on 2018-01-24
(Beg beg beg, 70 years old, the brain is running slower… any help gratefully received).  
 
 
 I have broken my dual-boot Windoze Ubuntu 17.10 Dell laptop system. It’s been running various Windoze & Ubuntu for a few years, survived but….. apologies not sure of some terminology, started with computers in the early 70s...

 
 
 I was re-installing 17.10 and seem to have lost the root file system: I’ve never had this problem & can’t work out how to fix without destroying other stuff.  (Booting off USB 17.10…) I can see gparted layout of 1Tb:  In it are various things I want to keep…  

 
 
 Windows 10, (sda5, ntfs, 90Gb). Would like to keep asis and able to boot every now & then.
 
 
 Data partition, (sda7, fat32, 781Gb). Want it to be accessible from Windoze or Ubuntu.
 
 
 There is an old Ubuntu partition, want fresh install, (sda13, ext4, 40Gb) and swap (sda10, linux-swap, 8Gb).
 
 
 There’s also a microsoft recovery partition, sda11, 8Gb, but hope I can dispense with that.

 
 
 I have all of sda1-13, but could happily get rid of all but sda5 & 7.  What I’d like to end up with is dual boot Windoze/Ubuntu.  
 
 
 Could some kind soul point me at a simple guide of what to do, please? That means I shouldn’t lose Windows or the Data (but I do have a backup of the data partition a few days ago).  

 
 
 Regards & thanks in advance.

---

### Post by kansasnoob on 2018-01-24
What are you currently able to boot? Either Windows or Ubuntu? Or only the live USB?

Please use Boot Repair to create a boot info summary and post the url here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

**Do [COLOR="#FF0000"]NOT[/COLOR] run the "recommended repair"!** We just need to see the boot info summary.

It would also be helpful to see a screenshot of Gparted, just for simplicity sake so we can get a better idea of the partitioning layout.

---

### Post by 2912pwil2 on 2018-01-24
Thanks Kansas!

Can only boot off USB. (Using wife's windows now)

Will run boot-repair & report later, but herewith gparted..
[IMG][[IMG]http://i589.photobucket.com/albums/ss338/theartfullodger/Screenshot%20from%202018-01-24%2015-55-54_1.png[/IMG]]("http://s589.photobucket.com/user/theartfullodger/media/Screenshot%20from%202018-01-24%2015-55-54_1.png.html")[/IMG]

---

### Post by 2912pwil2 on 2018-01-24
Thanks guys, Boot repair info...

[https://paste.ubuntu.com/26453339/](https://paste.ubuntu.com/26453339/)

---

### Post by oldfred on 2018-01-24
With new UEFI systems, you do not want to ever boot in BIOS mode.

It looks like you installed in BIOS mode as now you have grub in gpt's protective MBR and bios_grub partitions.
And you have flagged sda12 with boot flag which makes it an ESP - efi system partition. But sda1 is your real ESP.
UEFI does not like two ESP, so use gparted and remove boot flag and/or efi boot flag from sda12.
With gpt you should only have one boot flag on the FAT32 partition used for UEFI booting.

You may have to use Boot-Repair to reinstall  grub, after removing second boot flag. Use advanced mode and the full uninstall/reinstall of grub as you need the UEFI version of grub, not the BIOS version of grub.

Make sure UEFI is set to boot in UEFI mode and/or BIOS/CSM/Legacy setting is off. Some systems just have one on/off and others have several separate settings. Dell is the only one where users have said they want CSM mode on, but you still boot in UEFI mode.
And separately always boot live installer in UEFI mode.

When in UEFI mode, you should then be able to select either Windows or ubuntu entries.

Side note.
While FAT32 is ok for smaller partitions like the ESP, best not to use for larger partitions. It cannot store any file over 4GB, nor has journal to help with recovery if corrupted. Use NTFS if you want compatibility with Windows.
And make sure Windows fast start up or always on hibernation is off. Windows may turn it back on with updates, so even if you turned it off, and then cannot write into your shared NTFS, Windows turned fast boot back on. Linux NTFS driver will not mount hibernated NTFS, not if NTFS needs chkdsk.

If in UEFI mode the two bios_grub partitions sda8 & sda9 are not required. Even if you wanted BIOS boot, only should have one bios_grub per drive/device.

---

### Post by 2912pwil2 on 2018-01-24
Thanks oldfred: (My father was a Freddie, liberated from Prisoner of War camp by American troops, 1945, thanks guys! ).  I will try your advice, carefully, tomorrow, my risk.

Think I may benefit from a bit more education/reading....

---

### Post by oldfred on 2018-01-24
There is a lot of reading in the link in my signature. Often too much for new users, who do not want to know details and just want it to work.

---

### Post by 2912pwil2 on 2018-01-26
Thanks everybody, largely sorted, much appreciation of this amazing resource!

---

